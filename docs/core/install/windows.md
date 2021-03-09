---
title: Windows に .NET をインストールする
description: .NET をインストールできる Windows のバージョンについて説明します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 7909a94c6384e53569db3ba17047cbcc93e80fe1
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105103"
---
# <a name="install-net-on-windows"></a>Windows に .NET をインストールする

> [!div class="op_single_selector"]
>
> - [Windows へのインストール](windows.md)
> - [macOS へのインストール](macos.md)
> - [Linux にインストールする](linux.md)

この記事では、Windows に .NET をインストールする方法について説明します。 .NET は、ランタイムと SDK で構成されています。 ランタイムは .NET アプリを実行するために使用され、アプリに含まれている場合と含まれていない場合があります。 SDK は、.NET アプリとライブラリの作成に使用されます。 .NET ランタイムは、常に SDK と共にインストールされます。

.NET の最新バージョンは 5.0 です。

> [!div class="button"]
> [.NET をダウンロードする](https://dotnet.microsoft.com/download/dotnet)

## <a name="supported-releases"></a>サポートされているリリース

以下の表は、現在サポートされている .NET リリースと、それらがサポートされている Windows のバージョンの一覧です。 これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Windows のバージョンの有効期限が切れるまで](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)サポートされます。

Windows 10 のバージョンのサービス終了日は、エディションごとに分かれています。 次の表では、**Home**、**Pro**、**Pro Education**、**Pro for Workstations** の各エディションだけが考慮されています。 具体的な詳細については、「[Windows ライフサイクルのファクト シート](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)」を確認してください。

> [!TIP]
> `+` 記号は、最小バージョンを表します。

| オペレーティング システム            | .NET Core 2.1 | .NET Core 3.1 | .NET 5 |
|-----------------------------|---------------|---------------|--------|
| Windows 10 / Windows Server バージョン 20H2    | ✔️           | ✔️            | ✔️    |
| Windows 10 / Windows Server バージョン 2004    | ✔️           | ✔️            | ✔️    |
| Windows 10 / Windows Server バージョン 1909    | ✔️           | ✔️            | ✔️    |
| Windows 10 / Windows Server バージョン 1903    | ✔️           | ✔️            | ✔️    |
| Windows 10 バージョン 1809    | ✔️           | ✔️            | ✔️    |
|  Windows 10 バージョン 1803    | ✔️           | ✔️            | ✔️    |
| Windows 10 バージョン 1709    | ✔️           | ✔️            | ✔️    |
| Windows 10 バージョン 1607    | ✔️           | ✔️            | ✔️    |
| Windows 8.1                 | ✔️           | ✔️            | ✔️    |
| Windows 7 SP1 [ESU][esu]    | ✔️           | ✔️            | ✔️    |
| Windows Server 2019<br>Windows Server 2016<br>Windows Server 2012 R2<br>      | ✔️           | ✔️            | ✔️    |
| Windows Server Core 2012 R2 | ✔️           | ✔️            | ✔️    |
| Nano Server バージョン 1809 以上  | ✔️           | ✔️            | ✔️    |
| Nano Server バージョン 1803   | ✔️           | ✔️            | ❌    |

## <a name="unsupported-releases"></a>サポートされていないリリース

次のバージョンの .NET は、❌ サポート対象外となりました。

- 3.0
- 2.2
- 2.0

## <a name="runtime-information"></a>ランタイムに関する情報

ランタイムは、.NET で作成されたアプリを実行するために使用されます。 アプリの作成者は、アプリを公開するとき、アプリにランタイムを含めることができます。 ランタイムが含まれていない場合は、ユーザーがランタイムをインストールする必要があります。

Windows には、3 つの異なるランタイムをインストールできます。

- *ASP.NET Core ランタイム*\
  ASP.NET Core アプリを実行します。 .NET ランタイムが含まれます。

- *Desktop ランタイム*\
  Windows 用の .NET WPF と Windows フォームのデスクトップ アプリを実行します。 .NET ランタイムが含まれます。

- *.NET ランタイム*\
  このランタイムは最も単純なランタイムであり、他のランタイムは含まれていません。 .NET アプリとの互換性を最善にするには、"*ASP.NET Core ランタイム*" と "*Desktop ランタイム*" の両方をインストールすることを強くお勧めします。

> [!div class="button"]
> [.NET ランタイムをダウンロードする](https://dotnet.microsoft.com/download/dotnet)

## <a name="sdk-information"></a>SDK に関する情報

SDK は、.NET アプリとライブラリを作成して公開するために使用されます。 SDK のインストールには、次の 3 つの[ランタイム](#runtime-information)が含まれます: ASP.NET Core、Desktop、.NET。

## <a name="dependencies"></a>依存関係

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[.NET 5.0](#tab/net50)

.NET 5.0 では以下の Windows のバージョンがサポートされます。

> [!NOTE]
> `+` 記号は、最小バージョンを表します。

| OS                  | バージョン       | アーキテクチャ   |
|---------------------|---------------|-----------------|
| Windows 10 クライアント   | バージョン 1607+ | x64、x86、ARM64 |
| Windows クライアント      | 7 SP1+、8.1   | x64、x86        |
| Windows Server      | 2012 R2+      | x64、x86        |
| Windows サーバー コア | 2012 R2+      | x64、x86        |
| Nano Server         | バージョン 1809+ | X64             |

.NET 5.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md)」 (.NET 5.0 でサポートされている OS バージョン) を参照してください。

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

.NET Core 3.1 では以下の Windows のバージョンがサポートされます。

> [!NOTE]
> `+` 記号は、最小バージョンを表します。

| OS                            | バージョン                        | アーキテクチャ   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows クライアント                | 7 SP1+、8.1                    | x64、x86        |
| Windows 10 クライアント             | バージョン 1607+                  | x64、x86        |
| Windows Server                | 2012 R2+                       | x64、x86        |
| Nano Server                   | バージョン 1803+                  | x64、ARM32      |

.NET Core 3.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)」(.NET Core 3.1 でサポートされている OS バージョン) を参照してください。

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

" *.NET Core 3.0 は現在 ❌ サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "

.NET Core 3.0 では以下の Windows のバージョンがサポートされます。

> [!NOTE]
> `+` 記号は、最小バージョンを表します。

| OS                            | バージョン                        | アーキテクチャ   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows クライアント                | 7 SP1+、8.1                    | x64、x86        |
| Windows 10 クライアント             | バージョン 1607+                  | x64、x86        |
| Windows Server                | 2012 R2+                       | x64、x86        |
| Nano Server                   | バージョン 1803+                  | x64、ARM32      |

.NET Core 3.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)」(.NET Core 3.0 でサポートされている OS バージョン) を参照してください。

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

" *.NET Core 2.2 は現在 ❌ サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "

.NET Core 2.2 では以下の Windows のバージョンがサポートされます。

> [!NOTE]
> `+` 記号は、最小バージョンを表します。

| OS                            | バージョン                        | アーキテクチャ   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows クライアント                | 7 SP1+、8.1                    | x64、x86        |
| Windows 10 クライアント             | バージョン 1607+                  | x64、x86        |
| Windows Server                | 2008 R2 SP1+                   | x64、x86        |
| Nano Server                   | バージョン 1803+                   | x64、ARM32      |

.NET Core 2.2 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)」(.NET Core 2.2 でサポートされている OS バージョン) を参照してください。

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 では以下の Windows のバージョンがサポートされます。

> [!NOTE]
> `+` 記号は、最小バージョンを表します。

| OS                            | バージョン                        | アーキテクチャ   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows クライアント                | 7 SP1+、8.1                    | x64、x86        |
| Windows 10 クライアント             | バージョン 1607+                  | x64、x86        |
| Windows Server                | 2008 R2 SP1+                   | x64、x86        |
| Nano Server                   | バージョン 1803+                  | x64、            |

.NET Core 2.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)」(.NET Core 2.1 でサポートされている OS バージョン) を参照してください。

### <a name="offline-install-for-windows-7"></a>Windows 7 用のオフライン インストール

Windows 7 で .NET Core 2.1 用のオフライン インストールを実行する場合は、まず最新の [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) がターゲット コンピューターにインストールされていることを確認する必要があります。

_certmgr.exe_ ツールを使用すると、証明書のインストールを自動化できます。これは、Visual Studio または Windows SDK から取得されます。 .NET Core 2.1 インストーラーを実行する前に、次のコマンドを使用して証明書をインストールします。

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

[以下の Windows 7](#additional-deps) に必要な依存関係を確認してください。

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2

次の Windows のバージョンに .NET SDK またはランタイムをインストールする場合は、さらに依存関係が必要になります。

| オペレーティング システム         | 前提条件                                                                    |
|--------------------------|----------------------------------------------------------------------------------|
| Windows 7 SP1 [ESU][esu] | - Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32] <br> - KB3063858 [64 ビット][kb64] / [32 ビット][kb32] <br> - [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) (.NET Core 2.1 のオフライン インストーラーのみ) |
| Windows Vista SP 2       | Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32] |
| Windows 8.1              | Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32] |
| Windows Server 2008 R2   | Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32] |
| Windows Server 2012 R2   | Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32] |

上記の要件は、次のいずれかの dll に関するエラーが発生した場合にも必要です。

- *api-ms-win-crt-runtime-l1-1-0.dll*
- *api-ms-win-cor-timezone-l1-1-0.dll*
- *hostfxr.dll*

## <a name="install-with-powershell-automation"></a>PowerShell オートメーションを使用してインストールする

[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの CI 自動化および管理者以外によるインストールに使用されます。 スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。

スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。 `Channel` スイッチを指定することで、特定のリリースを選択できます。 ランタイムをインストールするには、`Runtime` スイッチを含めます。 それ以外の場合は、スクリプトによって SDK がインストールされます。

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

`-Runtime` スイッチを省略して SDK をインストールします。 この例では、`-Channel` スイッチが `Current` に設定されているため、サポートされている最新バージョンがインストールされます。

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a>Visual Studio を使用してインストールする

次の表で、Visual Studio を使用して .NET アプリを開発している場合に、ターゲットの .NET SDK バージョンに基づいて最低限必要な Visual Studio のバージョンを説明しています。

| .NET SDK バージョン      | Visual Studio のバージョン                      |
| --------------------- | ------------------------------------------ |
| 5.0                   | Visual Studio 2019 バージョン 16.8 以降。 |
| 3.1                   | Visual Studio 2019 バージョン 16.4 以降。 |
| 3.0                   | Visual Studio 2019 バージョン 16.3 以降。 |
| 2.2                   | Visual Studio 2017 バージョン 15.9 以降。 |
| 2.1                   | Visual Studio 2017 バージョン 15.7 以降。 |

Visual Studio を既にインストールしてある場合は、次の手順でバージョンを確認できます。

01. Visual Studio を開きます。
01. **[ヘルプ]**  >  **[Microsoft Visual Studio のバージョン情報]** を選択します。
01. **[バージョン情報]** ダイアログで、バージョン番号を確認します。

Visual Studio には、最新の .NET SDK とランタイムをインストールできます。

> [!div class="button"]
> [Visual Studio をダウンロードします](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。

### <a name="select-a-workload"></a>ワークロードを選択する

Visual Studio をインストールまたは変更するときは、ビルドするアプリケーションの種類に応じて、次の 1 つ以上のワークロードを選択します。

- **[他のツールセット]** セクションの **[.NET Core クロスプラットフォームの開発]** ワークロード。
- **[Web クラウド]** セクションの **[ASP.NET と Web 開発]** ワークロード。
- **[Web クラウド]** セクションの **[Azure の開発]** ワークロード。
- **[デスクトップとモバイル]** セクションの **[.NET デスクトップ開発]** ワークロード。

[![Windows Visual Studio 2019 と .NET Core ワークロード](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>Visual Studio Code と共にインストールする

Visual Studio Code は、デスクトップ上で動作する強力で軽量なソース コード エディターです。 Visual Studio Code は、Windows、macOS、Linux で利用できます。

Visual Studio Code には、Visual Studio のような自動化された .NET Core インストーラーは付属していませんが、.NET Core のサポートを簡単に追加できます。

01. [Visual Studio Code をダウンロードしてインストールします](https://code.visualstudio.com/Download)。
01. [.NET Core SDK をダウンロードしてインストールします](https://dotnet.microsoft.com/download/dotnet)。
01. [Visual Studio Code マーケットプレースから C# 拡張機能をインストールします](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。

## <a name="windows-installer"></a>Windows インストーラー

.NET の[ダウンロード ページ](https://dotnet.microsoft.com/download/dotnet)には、Windows インストーラーの実行可能ファイルが用意されています。

Windows インストーラーを使用して .NET をインストールする場合、`DOTNETHOME_X64` および `DOTNETHOME_X86` パラメーターを設定することによってインストール パスをカスタマイズできます。

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

運用環境で、または継続的インテグレーションをサポートするために .NET をサイレント インストールする場合は、次のスイッチを使用します。

- `/install`\
.NET をインストールします。

- `/quiet`\
UI やプロンプトが表示されないようにします。

- `norestart`\
再起動の試行を抑制します。

```console
dotnet-sdk-3.1.301-win-x64.exe /install /quiet /norestart
```

詳細については、「[インストーラーの標準コマンドライン オプション](/windows/win32/msi/standard-installer-command-line-options)」を参照してください。

> [!TIP]
> 成功した場合は、インストーラーから終了コード 0 が返されます。再起動が必要であることを示す場合は、終了コード 3010 が返されます。 その他の値は通常、エラー コードです。

## <a name="download-and-manually-install"></a>手動でダウンロードしてインストールする

.NET 用 Windows インストーラーの代わりに、SDK またはランタイムをダウンロードして手動でインストールすることもできます。 手動インストールは、通常、継続的インテグレーション テストの一環として行われます。 開発者またはユーザーの場合、通常は[インストーラー](https://dotnet.microsoft.com/download/dotnet)を使用することをお勧めします。

.NET SDK と .NET ランタイムはどちらも、ダウンロード後に手動でインストールできます。 .NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。 まず、次のいずれかのサイトから SDK またはランタイムのバイナリ リリースをダウンロードします。

- [.NET 5.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet/5.0)
- [.NET Core 3.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet/3.1)
- [.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet/2.1)
- [すべての .NET Core のダウンロード](https://dotnet.microsoft.com/download/dotnet)

.NET を抽出するためのディレクトリを作成します (`%USERPROFILE%\dotnet` など)。 次に、ダウンロードした zip ファイルをそのディレクトリに抽出します。

既定では、この方法でインストールされた .NET は、.NET CLI コマンドおよびアプリから使用されないため、使用することを明示的に選択する必要があります。 これを行うには、アプリケーションの起動に使用する環境変数を変更します。

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

この方法では、複数のバージョンを別々の場所にインストールして、その場所を参照する環境変数を使ってアプリケーションを実行することで、アプリケーションによって使用されるインストール場所を明示的に選択できます。

`DOTNET_MULTILEVEL_LOOKUP` が `0` に設定されている場合、.NET により、グローバルにインストールされている .NET のバージョンはすべて無視されます。 アプリケーションを実行するための最適なフレームワークを選択するときに、.NET によりグローバル インストールの既定の場所が考慮されるようにするには、その環境設定を削除します。 通常、既定値は `C:\Program Files\dotnet` です。インストーラーによってここに .NET がインストールされます。

## <a name="docker"></a>Docker

コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。 同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。

.NET は Docker コンテナー内で実行できます。 公式の .NET Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet)で見つけられます。 各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。

Microsoft は、特定のシナリオに対応したイメージを用意しています。 たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-aspnet)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。

Docker コンテナー内で .NET を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)ページを参照してください。

## <a name="next-steps"></a>次のステップ

- [.NET が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md?pivots=os-windows)。
- [チュートリアル: Hello World チュートリアル](../tutorials/with-visual-studio.md)。
- [チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。
- [チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
[vcc64]: https://aka.ms/vs/16/release/vc_redist.x64.exe
[vcc32]: https://aka.ms/vs/16/release/vc_redist.x86.exe
[kb64]: https://www.microsoft.com/download/details.aspx?id=47442
[kb32]: https://www.microsoft.com/download/details.aspx?id=47409
