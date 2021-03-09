---
title: .NET の概要
description: さまざまな種類のアプリをビルドするための無料のオープンソース開発プラットフォームである、.NET について学習します。
author: tdykstra
ms.date: 11/16/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 7997346c9b248962b36688592d357247ec0ce6aa
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105090"
---
# <a name="introduction-to-net"></a>.NET の概要

.NET は、次のようなさまざまな種類のアプリをビルドするための無料のオープンソース開発プラットフォームです。

* [Web アプリ、Web API、およびマイクロサービス](/aspnet/core/introduction-to-aspnet-core#recommended-learning-path)
* [クラウドのサーバーレス関数](/azure/azure-functions/functions-create-first-function-vs-code?pivots=programming-language-csharp)
* [クラウド ネイティブ アプリ](../architecture/cloud-native/index.md)
* [モバイル アプリ](https://dotnet.microsoft.com/learn/xamarin/hello-world-tutorial/intro)
* デスクトップ アプリ
  * [Windows WPF](/dotnet/desktop/wpf/)
  * [Windows フォーム](/dotnet/desktop/winforms/)
  * [ユニバーサル Windows プラットフォーム (UWP)](/windows/uwp/get-started/create-a-hello-world-app-xaml-universal)
* [ゲーム](https://dotnet.microsoft.com/apps/games)
* [モノのインターネット (IoT)](../iot/index.yml)
* [Machine Learning](../machine-learning/index.yml)
* [コンソール アプリ](tutorials/with-visual-studio-code.md)
* [Windows サービス](/aspnet/core/host-and-deploy/windows-service)

[クラス ライブラリ](../standard/class-libraries.md)を使用して、異なるアプリとアプリの種類の間で機能を共有します。

.NET を使用すると、ビルドするアプリの種類に関係なく、コードおよびプロジェクト ファイルの外観が同じになります。 各アプリで同じランタイム、API、および言語の機能にアクセスできます。

## <a name="cross-platform"></a>クロス プラットフォーム

次のような多くのオペレーティング システム用の .NET アプリを作成できます。

* Windows
* macOS
* Linux
* Android
* iOS
* tvOS
* watchOS

サポートされているプロセッサ アーキテクチャは次のとおりです。

* X64
* x86
* ARM32
* ARM64

.NET の場合、オペレーティング システム API などのプラットフォーム固有の機能を使用することができます。 例として、Windows 上の Windows フォームと WPF、および Xamarin からの各モバイル プラットフォームへのネイティブ バインドがあります。

詳細については、[サポートされている OS ライフサイクル ポリシー](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)と [.NET RID カタログ](rid-catalog.md)に関するページを参照してください。

## <a name="open-source"></a>オープン ソース

.NET はオープン ソースであり、[MIT および Apache 2 ライセンス](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)を使用します。 .NET は [.NET Foundation](https://dotnetfoundation.org/) のプロジェクトです。

詳細については、[GitHub.com のプロジェクト リポジトリの一覧](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)を参照してください。

## <a name="support"></a>サポート

.NET は、Windows、macOS、および Linux 上で Microsoft によってサポートされています。 セキュリティと品質に関する更新は、毎月第 2 火曜日に定期的に行われます。

Microsoft からの .NET のバイナリ配布は、Azure 内の Microsoft が管理するサーバーでビルドされてテストされ、Microsoft のエンジニアリングおよびセキュリティ プラクティスに従っています。

Red Hat Enterprise Linux (RHEL) 上の [.NET は Red Hat によってサポート](https://developers.redhat.com/topics/dotnet/)されています。 Red Hat とマイクロソフトが共同して、.NET Core が RHEL 上で適切に動作するようにします。

Tizen プラットフォーム上の [.NET は Tizen によってサポート](https://developer.tizen.org/development/training/.net-application)されています。

詳細については、「[.NET Core および .NET 5 のリリースとサポート](releases-and-support.md)」を参照してください。

## <a name="tools-and-productivity"></a>ツールと生産性

.NET を使用すると、言語、統合開発環境 (IDE)、およびその他のツールを選択できます。

### <a name="programming-languages"></a>プログラミング言語

.NET によって、次の 3 つのプログラミング言語がサポートされます。

* [C#](../csharp/index.yml)

  C# ("シー シャープ" と読みます) は、最新のタイプ セーフなオブジェクト指向のプログラミング言語です。 C# は C 言語ファミリーをルーツとしているため、C、C++、Java、JavaScript のプログラマーであればすぐに使いこなすことができます。

* [F#](../fsharp/index.yml)

  F# 言語は、関数型、オブジェクト指向、および命令型のプログラミング モデルをサポートします。

* [Visual Basic](../visual-basic/index.yml)

  .NET 言語の中で Visual Basic の構文は通常の人間の言語に最も近いため、より簡単に習得できます。 Microsoft が新機能を積極的に開発している C# や F# とは異なり、Visual Basic 言語は安定しています。 Visual Basic は Web アプリではサポートされていませんが、Web API ではサポートされています。

.NET 言語でサポートされる機能をいくつか以下に示します。

* [タイプ セーフ](../standard/base-types/common-type-system.md)
* 型の推定 - [C#](../csharp/programming-guide/types/index.md#specifying-types-in-variable-declarations)、[F#](../fsharp/language-reference/type-inference.md)、[Visual Basic](../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
* [ジェネリック型](../standard/generics.md)
* [デリゲート](../standard/delegates-lambdas.md)
* [ラムダ](../standard/delegates-lambdas.md)
* [イベント](../standard/events/index.md)
* [例外](../standard/exceptions/index.md)
* [属性](../standard/attributes/index.md)
* [非同期コード](../standard/async.md)
* [並列プログラミング](../standard/parallel-programming/index.md)
* [コード アナライザー](../fundamentals/code-analysis/overview.md)

### <a name="ides"></a>IDE

.NET 用の統合開発環境には、次のようなものがあります。

* [Visual Studio](https://visualstudio.microsoft.com/vs/)

  Windows でのみ実行されます。 .NET で動作するように設計された豊富な機能が組み込まれています。 Community Edition は無料であり、学生、オープンソースの共同作成者、および個人向けです。

* [Visual Studio Code](https://code.visualstudio.com/)

  Windows、macOS、Linux 上で実行される。 無料かつオープン ソース。 拡張機能は、.NET 言語での作業に使用できます。

* [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)

  macOS でのみ実行されます。 iOS、Android、および Web 用の .NET アプリとゲームを開発するためのものです。

* [GitHub Codespaces](https://github.com/features/codespaces)

  オンラインの Visual Studio Code 環境 (現在はベータ版)。

### <a name="sdk-and-runtimes"></a>SDK とランタイム

[.NET SDK](sdk.md) は、.NET アプリケーションを開発および実行するためのライブラリとツールのセットです。

[.NET をダウンロードする](https://dotnet.microsoft.com/download/dotnet)ときに、.NET ランタイムや ASP.NET Core ランタイムなどの、SDK または "*ランタイム*" を選択できます。 .NET アプリを実行するために準備するコンピューター上にランタイムをインストールします。 開発に使用するコンピューター上に SDK をインストールします。 SDK をダウンロードすると、それと共にランタイムを自動的に取得することになります。

SDK のダウンロードには次のコンポーネントが含まれます。

* [.NET CLI](tools/index.md)。 ローカル開発および継続的インテグレーション スクリプトに使用できるコマンドライン ツール。
* `dotnet` [ドライバー](tools/index.md#driver)。 フレームワーク依存アプリを実行する CLI コマンド。
* [Roslyn](https://github.com/dotnet/roslyn) および [F#](https://github.com/microsoft/visualfsharp) プログラミング言語コンパイラ。
* [MSBuild](/visualstudio/msbuild/msbuild) ビルド エンジン。
* [.NET ランタイム](#clr)。 型システム、アセンブリ読み込み、ガベージ コレクター、ネイティブ相互運用機能、およびその他の基本的なサービスを提供します。
* [ランタイム ライブラリ](#runtime-libraries)。 プリミティブ データ型および基本的なユーティリティを提供します。
* ASP.NET Core ランタイム。 Web アプリ、IoT アプリ、モバイル バックエンドなど、インターネットに接続されたアプリ用の基本的なサービスを提供します。
* デスクトップ ランタイム。 Windows フォームや WPF など、Windows デスクトップ アプリ用の基本的なサービスを提供します。

ランタイムのダウンロードには、次のコンポーネントが含まれます。

* (省略可能) デスクトップまたは ASP.NET Core ランタイム。
* [.NET ランタイム](#clr)。 型システム、アセンブリ読み込み、ガベージ コレクター、ネイティブ相互運用機能、およびその他の基本的なサービスを提供します。
* [ランタイム ライブラリ](#runtime-libraries)。 プリミティブ データ型および基本的なユーティリティを提供します。
* `dotnet` [ドライバー](tools/index.md#driver)。 フレームワーク依存アプリを実行する CLI コマンド。

詳細については、次のリソースを参照してください。

* [.NET SDK の概要](sdk.md)
* [.NET CLI の概要](tools/index.md)
* [dotnet コマンド](tools/dotnet.md)

### <a name="project-system-and-msbuild"></a>プロジェクト システムと MSBuild

.NET アプリは、[MSBuild](/visualstudio/msbuild/msbuild) を使用してソース コードからビルドされます。 プロジェクト ファイル ( *.csproj*、 *.fsproj*、または *.vbproj*) により、[ターゲット](/visualstudio/msbuild/msbuild-targets)と、コードのコンパイル、パッキング、公開を行う関連 [タスク](/visualstudio/msbuild/msbuild-tasks)が指定されます。 ターゲットとタスクの標準コレクションを参照する SDK 識別子があります。 これらの識別子を使用すると、プロジェクト ファイルのサイズを小さく保つのに役立ち、操作しやすくなります。 たとえば、次のようなコンソール アプリのプロジェクト ファイルです。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

Web アプリの場合は次のようになります。

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

これらの例では、`Project` 要素の `Sdk` 属性によって、プロジェクトをビルドする一連の MSBuild ターゲットとタスクが指定されます。  `TargetFramework` 要素によって、アプリが依存する .NET のバージョンが指定されます。 プロジェクト ファイルを編集して、プロジェクトに固有のターゲットとタスクをさらに追加することができます。

詳細については、[.NET プロジェクト SDK の概要](project-sdk/overview.md) に関するページと、[ターゲット フレームワーク](../standard/frameworks.md)に関するページを参照してください。

### <a name="cicd"></a>CI/CD

MSBuild と .NET CLI は、次のようなさまざまな継続的インテグレーション ツールと環境で使用できます。

* [GitHub のアクション](https://github.com/features/actions)
* [Azure DevOps](/azure/devops/user-guide/what-is-azure-devops)
* [CAKE](https://cakebuild.net/)
* [FAKE](https://fake.build/)

詳細については、[継続的インテグレーション (CI) での .NET SDK とツールの使用](tools/using-ci-with-cli.md)に関するページを参照してください

### <a name="nuget"></a>NuGet

[NuGet](/nuget/what-is-nuget) は、.NET 用に設計されたオープンソースのパッケージ マネージャーです。 NuGet パッケージは、拡張子が `.nupkg` の *.zip* ファイルであり、コンパイル済みのコード (DLL)、そのコードに関連する他のファイル、パッケージのバージョン番号などの情報が記述されているマニフェストが含まれます。 開発者はコードを共有して、パッケージを作成し、それらを [nuget.org](https://nuget.org) またはパブリック ホストに公開します。 共有コードを使用する開発者はプロジェクトにパッケージを追加し、その後、プロジェクト コードでパッケージによって公開される API を呼び出すことができます。

詳細については、[NuGet に関するドキュメント](/nuget/)を参照してください。

### <a name="net-interactive"></a>.NET インタラクティブ

.NET Interactive は、ユーザーが Web、マークダウン、ノートブック全体の対話型エクスペリエンスを作成できるようにする CLI ツールと API のグループです。

詳細については、次のリソースを参照してください。

* [ブラウザーでの .NET のチュートリアル](https://dotnet.microsoft.com/learn/dotnet/in-browser-tutorial/1)
* [コンピューター上の Jupyter での .NET ノートブックの使用](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)
* [.NET Interactive に関するドキュメント](https://github.com/dotnet/interactive/blob/main/docs/README.md)

## <a name="execution-models"></a>実行モデル

共通言語ランタイム (CLR) と呼ばれるランタイム環境では、.NET アプリによって[マネージド コード](../standard/managed-code.md)が実行されます。

### <a name="clr"></a>CLR

.NET [CLR](../standard/clr.md) は、Windows、macOS、Linux のサポートを含むクロスプラットフォーム ランタイムです。 CLR は、メモリの割り当てと管理を行います。 CLR は、アプリの実行だけでなく、Just-In-Time (JIT) コンパイラを使用してコードを生成してコンパイルする仮想マシンでもあります。

詳細については、「[共通言語ランタイム (CLR) の概要](../standard/clr.md)」を参照してください。

### <a name="jit-compiler-and-il"></a>JIT コンパイラと IL

C# などの高レベル .NET 言語は、中間言語 (IL) と呼ばれるハードウェアに依存しない命令セットにコンパイルされます。 アプリを実行すると、JIT コンパイラにより、プロセッサで認識されるマシン コードに IL が変換されます。 JIT コンパイルは、コードが実行されるのと同じマシン上で行われます。

JIT コンパイルはアプリケーションの実行中に行われるため、コンパイル時間は実行時間の一部になります。 したがって、JIT コンパイラを使用して、コードの最適化に要する時間と、結果のコードによって得られる時間の節約のバランスを取る必要があります。 しかし、JIT コンパイラによって実際のハードウェアが認識されるため、開発者は異なるプラットフォームに対して異なる実装を提供する必要がなくなります。

.NET JIT コンパイラを使用すると、"*階層型コンパイル*" を実行できます。これは、実行時に個々のメソッドを再コンパイルできることを意味します。 この機能を使用すると、すぐにコンパイルできると同時に、頻繁に使用されるメソッドに対して高度に調整されたバージョンのコードを引き続き生成できます。

詳細については、「[マネージド実行プロセス](../standard/managed-execution-process.md)」と「[階層型コンパイル](whats-new/dotnet-core-3-0.md#tiered-compilation)」を参照してください。

### <a name="aot-compiler"></a>AOT コンパイラ

ほとんどの .NET ワークロードの既定のエクスペリエンスは JIT コンパイラですが、.NET により、次の 2 つの形式の Ahead-Of-Time (AOT) コンパイルが提供されます。

* 一部のシナリオでは、100% の AOT コンパイルが必要です。 例として、[iOS](/xamarin/ios/) があります。
* その他のシナリオでは、ほとんどのアプリのコードは AOT コンパイルされますが、一部は JIT コンパイルされます。 一部のコード パターンは AOT には適していません (ジェネリックなど)。 この形式の AOT コンパイルの例として、[ready-to-run](whats-new/dotnet-core-3-0.md#readytorun-images) publish オプションがあります。 この形式の AOT により、欠点のない AOT の利点が提供されます。

### <a name="automatic-memory-management"></a>自動メモリ管理

"*ガベージ コレクター*" (GC) によって、アプリケーションのメモリの割り当てと解放が管理されます。 コードで新しいオブジェクトが作成されるたびに、CLR によって、[マネージド ヒープ](../standard/garbage-collection/fundamentals.md#the-managed-heap)からオブジェクトにメモリが割り当てられます。 マネージド ヒープに使用可能なアドレス空間がある限り、ランタイムは新しいオブジェクト用に領域の割り当てを続けます。 十分な空きアドレス空間が残っていない場合、GC により、アプリケーションで使用されなくなったマネージド ヒープ内のオブジェクトが確認されます。 その後、そのメモリが再利用されます。

GC は、"*メモリの安全性*" の確保に役立つ CLR サービスの 1 つです。 割り当てられているメモリのみにプログラムがアクセスする場合、そのプログラムはメモリ セーフです。 たとえば、ランタイムでは、配列の範囲を超えた割り当てられていないメモリにアプリがアクセスしていないことを確認します。

詳細については、「[自動メモリ管理](../standard/automatic-memory-management.md)」と「[ガベージ コレクションの基礎](../standard/garbage-collection/fundamentals.md)」を参照してください。

### <a name="working-with-unmanaged-resources"></a>アンマネージ リソースの操作

コードで "*アンマネージ リソース*" を参照する必要がある場合があります。 アンマネージ リソースは、.NET ランタイムで自動的に維持されないリソースです。 たとえば、ファイル ハンドルは、アンマネージ リソースです。 <xref:System.IO.FileStream> オブジェクトはマネージ オブジェクトですが、アンマネージドのファイル ハンドルを参照します。 <xref:System.IO.FileStream> の使用が終わったら、ファイル ハンドルを明示的に解放する必要があります。

.NET では、アンマネージ リソースを参照するオブジェクトは <xref:System.IDisposable> インターフェイスを実装します。 オブジェクトの使用が終わったら、すべてのアンマネージ リソースを解放する、オブジェクトの <xref:System.IDisposable.Dispose> メソッドを呼び出します。 .NET 言語によって、便利な `using` ステートメント ([C#](../csharp/language-reference/keywords/using.md)、[F#](../fsharp/language-reference/resource-management-the-use-keyword.md)、[VB](../visual-basic/language-reference/statements/using-statement.md)) が提供されます。これにより、`Dispose` メソッドが確実に呼び出されます。

詳細については、「[アンマネージ リソースのクリーンアップ](../standard/garbage-collection/unmanaged.md)」を参照してください。

## <a name="deployment-models"></a>デプロイ モデル

.NET アプリは、次の 2 つの異なるモードで公開できます。

* アプリを "*自己完結型*" として公開すると、.NET [ランタイム](#sdk-and-runtimes)と [ライブラリ](#runtime-libraries)、およびアプリケーションとその依存関係を含む実行可能ファイルが生成されます。 そのアプリケーションのユーザーは、.NET ランタイムがインストールされていないコンピューター上でそれを実行することができます。 自己完結型アプリはプラットフォーム固有であり、必要に応じて、[AOT コンパイル](#aot-compiler)の形式を使用して公開できます。

* アプリを "*フレームワーク依存*" として公開すると、アプリケーション自体とその依存関係のみを含む実行可能ファイルとバイナリ ファイル ( *.dll* ファイル) が生成されます。 そのアプリケーションのユーザーは、.NET [ランタイム](#sdk-and-runtimes)を個別にインストールする必要があります。 実行可能ファイルはプラットフォーム固有ですが、フレームワークに依存するアプリケーションの *.dll* ファイルはクロスプラットフォームです。

  複数のバージョンのランタイムを並行してインストールし、異なるバージョンのランタイムをターゲットとするフレームワーク依存アプリを実行することができます。 詳細については、[ターゲット フレームワーク](../standard/frameworks.md)に関するページを参照してください。

実行可能ファイルは、[ランタイム識別子 (RID)](rid-catalog.md) で指定する特定のターゲット プラットフォームに対して生成されます。

詳細については、[.NET アプリケーションの公開の概要](deploying/index.md)に関するページと「[.NET および Docker の概要](docker/introduction.md)」を参照してください。

## <a name="runtime-libraries"></a>ランタイム ライブラリ

.NET には、[ランタイム ライブラリ](../standard/glossary.md#runtime)、[フレームワーク ライブラリ](../standard/glossary.md#framework-libraries)、または[基本クラス ライブラリ (BCL)](../standard/glossary.md#bcl) と呼ばれるクラス ライブラリの広範な標準セットが用意されています。 これらのライブラリによって、多くの汎用およびワークロード固有の型とユーティリティ機能の実装が提供されます。

.NET ランタイム ライブラリで定義されている型の例をいくつか以下に示します。

* <xref:System.Boolean?displayProperty=nameWithType> や <xref:System.Int32?displayProperty=nameWithType> などのプリミティブ型。
* <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> や <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> などのコレクション。
* <xref:System.Data.DataSet?displayProperty=nameWithType> や <xref:System.Data.DataTable?displayProperty=nameWithType> などのデータ型。
* <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> などのネットワーク ユーティリティ型。
* <xref:System.IO.FileStream?displayProperty=nameWithType> や <xref:System.IO.TextWriter?displayProperty=nameWithType> などの[ファイルおよびストリーム入出力](../standard/io/index.md)ユーティリティ型。
* <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> や <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> などの[シリアル化](../standard/serialization/index.md) ユーティリティ型。
* <xref:System.Span%601?displayProperty=nameWithType>、<xref:System.Numerics.Vector?displayProperty=nameWithType>、[Pipelines](../standard/io/pipelines.md) などの高パフォーマンス型。

詳細については、「[ランタイム ライブラリの概要](../standard/runtime-libraries-overview.md)」を参照してください。 ライブラリのソース コードは [GitHub の dotnet/runtime リポジトリ](https://github.com/dotnet/runtime/tree/master/src/libraries)にあります。

### <a name="extensions-to-the-runtime-libraries"></a>ランタイム ライブラリの拡張機能

一般的に使用される一部のアプリケーション機能のライブラリは、ランタイム ライブラリには含まれませんが、次のような NuGet パッケージで使用できます。

| NuGet パッケージ | ドキュメント |
|---------|---------|
| [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) | [アプリケーションの有効期間の管理 (汎用ホスト)](extensions/generic-host.md) |
| [Microsoft.Extensions.DependencyInjection](https://www.nuget.org/packages/Microsoft.Extensions.DependencyInjection) | [依存関係の挿入 (DI)](extensions/dependency-injection.md)
| [Microsoft.Extensions.Configuration](https://www.nuget.org/packages/Microsoft.Extensions.Configuration) | [Configuration](extensions/configuration.md) |
| [Microsoft.Extensions.Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) | [Logging](extensions/logging.md) |
| [Microsoft.Extensions.Options](https://www.nuget.org/packages/Microsoft.Extensions.Options) | [オプションのパターン](extensions/options.md) |

詳細については、[GitHub の dotnet/extensions リポジトリ](https://github.com/dotnet/extensions)を参照してください。

## <a name="data-access"></a>データ アクセス

.NET によって、オブジェクト リレーショナル マッパー (ORM) と、コードで SQL クエリを記述する方法が提供されます。

### <a name="entity-framework-core"></a>Entity Framework Core

Entity Framework (EF) Core は、[オープン ソース](https://github.com/aspnet/EntityFrameworkCore)のクロスプラットフォーム データアクセス テクノロジであり、ORM として使用できます。 EF Core を使用すると、コードで .NET オブジェクトを参照してデータベースを操作できます。 これにより、書き込みとテストに必要なデータアクセス コードの量が減ります。 EF Core では多くのデータベース エンジンがサポートされます。

詳細については、「[Entity Framework Core](/ef/core/)」と「[データベース プロバイダー](/ef/core/providers/)」を参照してください。

### <a name="linq"></a>LINQ

統合言語クエリ (LINQ) を使用すると、データを操作するための宣言型コードを記述できます。 データは (メモリ内オブジェクト、SQL データベース、XML ドキュメントなどの) さまざまな形式にすることができますが、記述する LINQ コードは通常、どのデータ ソースでも違いがないように見えます。

詳細については、[LINQ (統合言語クエリ) の概要](../standard/linq/index.md)に関するページを参照してください。

## <a name="net-terminology"></a>.NET の用語

時間の経過と共に一部の用語の使用法がどのように変わったかを知っておくと、.NET に関するドキュメントを理解するのに役立ちます。

### <a name="net-core-and-net-5"></a>.NET Core と .NET 5

2002 年に、Microsoft によって、Windows アプリを作成するための開発プラットフォームである [.NET Framework](../framework/get-started/overview.md) がリリースされました。 現在、.NET Framework はバージョン 4.8 であり、引き続き [Microsoft によってサポート](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)されます。

2014 年に、Microsoft によって、.NET Framework のクロスプラットフォームのオープンソースの後継版の作成が開始されました。 この .NET の新しい実装には、バージョン 3.1 に達するまで .NET Core という名前が付けられていました。 .NET Core 3.1 以降の次のバージョンは .NET 5.0 であり、現在プレビュー段階です。 この .NET の実装と .NET Framework 4.8 間の混乱を避けるため、バージョン番号 4 はスキップされました。 "Core" という名前は、これが現在、.NET の主な実装であることを明確にするために削除されました。

この記事は .NET 5 に関するものですが、.NET 5 のドキュメントの多くにはまだ ".NET Core" や ".NET Framework" への参照があります。 さらに、"Core" は [ASP.NET Core](/aspnet/core/) や [Entity Framework Core](/ef/core/) という名前に残されています。

ドキュメントで .NET Standard も参照されています。 [.NET Standard](../standard/net-standard.md) は、.NET の複数の実装用のクラス ライブラリを開発できる API 仕様です。

詳細については、「[.NET アーキテクチャ コンポーネント](../standard/components.md)」を参照してください。

### <a name="overloaded-terms"></a>オーバーロードされた用語

.NET の用語の一部は混乱を招く可能性があります。これは、異なるコンテキストで同じ単語が異なる方法で使用されるためです。 より顕著な例をいくつか以下に示します。

* **ランタイム**

  |Context  |"ランタイム" の意味 |
  |---------|---------|
  | [共通言語ランタイム (CLR)](#clr)| マネージド プログラムの実行環境。 OS は、ランタイム環境の一部ですが、.NET ランタイムの一部ではありません。 |
  | [.NET のダウンロード ページの .NET ランタイム](https://dotnet.microsoft.com/download/dotnet) | [CLR](#clr) および[ランタイム ライブラリ](#runtime-libraries)。これらは組み合わせて使用され、[フレームワーク依存](#deployment-models)アプリを実行するためのサポートが提供されます。 このページには、ASP.NET Core サーバー アプリと Windows デスクトップ アプリのランタイムの選択肢が示されます。 |
  | [ランタイム識別子 (RID)](rid-catalog.md) | .NET アプリが実行される OS プラットフォームおよび CPU アーキテクチャ。 次に例を示します。Windows x64、Linux x64。 |

* **フレームワーク**

  |Context  | "フレームワーク" の意味 |
  |---------|---------------------|
  | .NET Framework | .NET の元の Windows のみの実装。 "Framework" の頭文字は大文字です。 |
  | ターゲット フレームワーク | .NET アプリまたはライブラリが依存する API のコレクション。 例: .NET Core 3.1、.NET Standard 2.0 |
  | ターゲット フレームワーク モニカー (TFM)  | TFM は、.NET アプリまたはライブラリのターゲット フレームワークを指定するための標準化されたトークン形式です。 例: .NET Framework 4.6.2 の `net462`。 |
  | フレームワークに依存するアプリ | [.NET のダウンロード ページ](https://dotnet.microsoft.com/download/dotnet)からランタイムをインストールしたコンピューター上でのみ実行できるアプリ。 この使用法の "フレームワーク" は、.NET のダウンロード ページからダウンロードする "ランタイム" と同じものです。 |
  | フレームワーク ライブラリ | [ランタイム ライブラリ](#runtime-libraries)のシノニムとして使用されることがあります。 |

* **SDK**

  |Context  | "SDK" の意味 |
  |---------|---------------|
  | [.NET のダウンロード ページの SDK](#sdk-and-runtimes)  | .NET アプリを開発して実行するためにダウンロードしてインストールするツールとライブラリのコレクション。 CLI、MSBuild、.NET ランタイム、およびその他のコンポーネントが含まれています。|
  | [SDK スタイルのプロジェクト](#project-system-and-msbuild) | 特定の種類のアプリのプロジェクトをビルドする方法を指定する、一連の MSBuild ターゲットとタスク。 この意味での SDK は、プロジェクト ファイル内の `Project` 要素の `Sdk` 属性を使用して指定されます。 |

* **platform**

  |Context  | "プラットフォーム" の意味 |
  |---------|--------------------|
  | クロス プラットフォーム | この用語での "プラットフォーム" は、オペレーティング システムとそれが動作するハードウェア (Windows、macOS、Linux、iOS、Android) を意味します。 |
  | .NET プラットフォーム | 使用法はさまざまです。 .NET の 1 つの実装 (.NET Framework や .NET 5 など)、またはすべての実装を含む .NET の包括的な概念を指す場合があります。 |

.NET の用語の詳細については、「[.NET 用語集](../standard/glossary.md)」を参照してください。

## <a name="advanced-scenarios"></a>高度なシナリオ

以下のセクションでは、高度なシナリオで役立つ .NET のいくつかの機能について説明します。

### <a name="native-interop"></a>ネイティブ相互運用

どのオペレーティング システムにも、システム サービスを提供するアプリケーション プログラミング インターフェイス (API) が含まれています。 .NET には、その API を呼び出すためのいくつかの方法が用意されています。

ネイティブ API と相互運用する主な方法は、"プラットフォーム呼び出し" (略して P/Invoke) を使用するものです。 P/Invoke は、Linux および Windows プラットフォーム全体でサポートされています。 Windows 限定で相互運用を行う方法は "COM 相互運用" と呼ばれます。これは、マネージド コードで [COM コンポーネント](/cpp/atl/introduction-to-com)を操作する場合です。 これは、P/Invoke インフラストラクチャ上に構築されますが、動作は少し異なります。

詳細については、「[ネイティブ相互運用性](../standard/native-interop/index.md)」を参照してください。

### <a name="unsafe-code"></a>アンセーフ コード

言語サポートに応じて、CLR の `unsafe` コードによって、ネイティブ メモリにアクセスしたりポインターの算術演算を実行したりできるようになります。 この操作は、特定のアルゴリズムおよびシステム相互運用性のために必要です。 アンセーフ コードの使用は強力ですが、システム API との相互運用を行ったり、最も効率的なアルゴリズムを実装したりする必要がなければ、推奨されません。 アンセーフ コードは、環境が異なると同じように実行されない可能性があり、さらにガベージ コレクターとタイプ セーフの利点が得られない場合があります。 可能な限りアンセーフ コードのみに制限し、そのコードを徹底的にテストすることをお勧めします。

詳細については、[アンセーフ コードとポインター](../csharp/programming-guide/unsafe-code-pointers/index.md)に関するページを参照してください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [.NET チュートリアルを選択する](tutorials/index.md)

> [!div class="nextstepaction"]
> [ブラウザーで .NET を試す](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)

> [!div class="nextstepaction"]
> [C# のツアーを見る](../csharp/tour-of-csharp/index.md)

> [!div class="nextstepaction"]
> [F# のツアーを見る](../fsharp/tour.md)
