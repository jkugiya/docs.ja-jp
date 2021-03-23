---
title: コンテナーでの診断の収集
description: この記事では、.NET Core 診断ツールを Docker コンテナーで使用する方法について説明します。
ms.date: 09/01/2020
ms.openlocfilehash: 1d0c9eadca348dad5c4fc0a395c8b371e3821262
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872757"
---
# <a name="collect-diagnostics-in-containers"></a>コンテナーでの診断の収集

他のシナリオでの .NET Core の問題の診断に役立つ同じ診断ツールが、Docker コンテナーでも動作します。 ただし、一部のツールについては、コンテナーで使用するには特別な手順が必要になります。 この記事では、パフォーマンス トレースとダンプを収集するためのツールを、Docker コンテナーで使用する方法について説明します。

## <a name="using-net-core-cli-tools-in-a-container"></a>コンテナーでの .NET Core CLI ツールの使用

**これらのツールの適用対象: ✔️** .NET Core 3.0 SDK 以降のバージョン

.NET Core グローバル CLI 診断ツール ([`dotnet-counters`](dotnet-counters.md)、[`dotnet-dump`](dotnet-dump.md)、[`dotnet-gcdump`](dotnet-gcdump.md)、[`dotnet-trace`](dotnet-trace.md)) は、さまざまな環境で動作するように設計されており、Docker コンテナーでもすべて直接動作するはずです。 このため、これらのツールは、コンテナーでの .NET Core 3.0 以降 (または、`dotnet-gcdump` の場合は 3.1 以降) を対象とする .NET Core のシナリオにおいて診断情報を収集するために推奨される方法です。

コンテナーでこれらのツールを使用するときの唯一の複雑な要因は、これらは .NET Core SDK でインストールされますが、多くの Docker コンテナーは .NET Core SDK がなくても実行されることです。 この問題に対する簡単な解決策の 1 つは、最初の Docker イメージでツールをインストールすることです。 ツールを使用するのに、.NET Core SDK が実行されている必要はなく、インストールされているだけでかまいません。 したがって、(.NET Core SDK が存在する) ビルド ステージでツールをインストールした後、バイナリを最終的なイメージにコピーする、[マルチステージ ビルド](https://docs.docker.com/develop/develop-images/multistage-build/)で Dockerfile を作成することができます。 この方法の唯一の欠点は、Docker イメージのサイズが増加することです。

```dockerfile
# In build stage
# Install desired .NET CLI diagnostics tools
RUN dotnet tool install --tool-path /tools dotnet-trace
RUN dotnet tool install --tool-path /tools dotnet-counters
RUN dotnet tool install --tool-path /tools dotnet-dump

...

# In final stage
# Copy diagnostics tools
WORKDIR /tools
COPY --from=build /tools .
```

または、CLI ツールをインストールするために必要になった時点で、コンテナーに .NET Core SDK をインストールすることもできます。 .NET Core SDK をインストールすると、.NET Core ランタイムが再インストールされるという副作用があることに注意してください。 そのため、コンテナーに存在するランタイムと一致するバージョンの SDK を必ずインストールしてください。

### <a name="using-net-core-global-cli-tools-in-a-sidecar-container"></a>サイドカー コンテナーでの .NET Core グローバル CLI ツールの使用

.NET Core グローバル CLI 診断ツールを使用して別のコンテナーのプロセスを診断する場合は、次の追加要件を考慮する必要があります。

1. コンテナーで、[プロセスの名前空間を共有する](https://docs.docker.com/engine/reference/run/#pid-settings---pid)必要があります (サイドカー コンテナー内のツールが、ターゲット コンテナー内のプロセスにアクセスできるようにするため)。
2. .NET Core グローバル CLI 診断ツールを使用するには、.NET Core ランタイムによって /tmp ディレクトリに書き込まれるファイルにアクセスする必要があるため、ターゲット コンテナーとサイドカー コンテナーの間でボリューム マウントを使用して /tmp ディレクトリを共有する必要があります。 これは、たとえば、コンテナーで共通の[ボリューム](https://docs.docker.com/storage/volumes/#create-and-manage-volumes)または Kubernetes [emptyDir](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir) ボリュームを共有することにより、行うことができます。 /tmp ディレクトリを共有せずにサイドカー コンテナーから診断ツールを使用しようとすると、プロセスで "互換性のある .NET ランタイムが実行されていない" というエラーが発生します。

## <a name="using-perfcollect-in-a-container"></a>コンテナーでの `PerfCollect` の使用

**このツールの適用対象: ✔️** .NET Core 2.1 以降のバージョン

[`PerfCollect`](./trace-perfcollect-lttng.md) スクリプトは、パフォーマンス トレースの収集に役に立ち、.NET Core 3.0 より前のトレースを収集する場合に推奨されるツールです。 コンテナーで `PerfCollect` を使用する場合は、次の要件を考慮してください。

1. `PerfCollect` を使用するには、[`SYS_ADMIN` 機能](https://man7.org/linux/man-pages/man7/capabilities.7.html)が必要なので (`perf` ツールを実行するため)、コンテナーが[その機能がある状態で開始される](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities)ことを確認します。
2. `PerfCollect` では、プロファイリング対象のアプリが開始するより前に、いくつかの環境変数が設定されている必要があります。 これらは、[Dockerfile](https://docs.docker.com/engine/reference/builder/#env) で、または[コンテナーを開始する](https://docs.docker.com/engine/reference/run/#env-environment-variables)ときに、設定できます。 これらの変数は通常の運用環境では設定されないので、プロファイリング対象のコンテナーを開始するときにだけ追加するのが一般的です。 PerfCollect で必要になる 2 つの変数は次のとおりです。
    1. COMPlus_PerfMapEnabled=1
    1. COMPlus_EnableEventLog=1

### <a name="using-perfcollect-in-a-sidecar-container"></a>サイドカー コンテナーでの `PerfCollect` の使用

あるコンテナーで `PerfCollect` を実行し、別のコンテナー内の .NET Core プロセスをプロファイリングする場合、エクスペリエンスはほぼ同じですが、次のような違いがあります。

1. 前に説明した環境変数 (COMPlus_PerfMapEnabled と COMPlus_EnableEventLog) を、(`PerfCollect` を実行するものではなく) ターゲット コンテナーに対して設定する必要があります。
2. (ターゲット コンテナーではなく) `PerfCollect` を実行するコンテナーに、`SYS_ADMIN` 機能が必要です。
3. 2 つのコンテナーは、[プロセスの名前空間を共有している](https://docs.docker.com/engine/reference/run/#pid-settings---pid)必要があります。

## <a name="using-createdump-in-a-container"></a>コンテナーでの `createdump` の使用

**このツールの適用対象: ✔️** .NET Core 2.1 以降のバージョン

`dotnet-dump` の代わりに、[`createdump`](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/xplat-minidump-generation.md) を使用して、ネイティブ情報とマネージド情報の両方が含まれるコア ダンプを Linux 上に作成することができます。 `createdump` ツールは .NET Core ランタイムと共にインストールされ、libcoreclr.so の隣にあります(通常は、"/usr/share/dotnet/shared/Microsoft.NETCore.App/[バージョン]" 内)。 このツールは、コンテナー内でもコンテナー化されていない Linux 環境と同じように動作しますが、1 つだけ例外があります。それは、ツールには [`SYS_PTRACE` 機能](https://man7.org/linux/man-pages/man7/capabilities.7.html)が必要であるため、Docker コンテナーを[開始するときにその機能を有効にしておく](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities)必要があるということです。

### <a name="using-createdump-in-a-sidecar-container"></a>サイドカー コンテナーでの `createdump` の使用

`createdump` を使用して、異なるコンテナー内のプロセスからダンプを作成したい場合、エクスペリエンスはほぼ同じですが、次のような違いがあります。

1. (ターゲット コンテナーではなく) `createdump` を実行するコンテナーに、`SYS_PTRACE` 機能が必要です。
2. 2 つのコンテナーは、[プロセスの名前空間を共有している](https://docs.docker.com/engine/reference/run/#pid-settings---pid)必要があります。
