---
title: .NET アーキテクチャ コンポーネント
description: .NET Standard、.NET 実装、.NET ランタイム、ツールなど、.NET アーキテクチャ コンポーネントについて説明します。
author: cartermp
ms.date: 10/05/2020
ms.openlocfilehash: d1780d8f85159c12ef4e11b2ac53091b61629352
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605322"
---
# <a name="net-architectural-components"></a>.NET アーキテクチャ コンポーネント

.NET アプリは、1 つまたは複数の *.NET 実装* 向けに開発され、実行されます。 .NET の実装には、.NET Framework、.NET 5 (および .NET Core)、Mono が含まれます。 .NET の複数の実装に共通する API 仕様があり、.NET Standard と呼ばれます。 この記事では、それぞれの概念について簡単に説明します。

## <a name="net-standard"></a>.NET Standard

.NET Standard は、.NET 実装の基本クラス ライブラリで実装されている API のセットです。 さらに厳密に言うと、コードのコンパイル対象である統一されたコントラクトのセットを構成する .NET API の仕様です。 これらのコントラクトが、.NET の複数の実装に実装されています。

.NET Standard は、[ターゲット フレームワーク](glossary.md#target-framework)です。 コードで .NET Standard の 1 つのバージョンをターゲットにした場合、そのバージョンの .NET Standard をサポートするすべての .NET 実装でそのコードを実行できます。

.NET Standard は .NET の異なる実装間での移植性を実現するために作成されましたが、現在は、.NET 5 によって、複数のプラットフォームやワークロードの間でコードを共有するための、より優れた方法が提供されています。 詳細については、「[.NET 5 と .NET Standard](net-standard.md#net-5-and-net-standard)」を参照してください。

## <a name="net-implementations"></a>.NET 実装

各 .NET 実装には、次のコンポーネントが含まれています。

- 1 つまたは複数のランタイム。 例: .NET Framework CLR、.NET 5 CLR。
- クラス ライブラリ。 例: .NET Framework 基本クラス ライブラリ、.NET 5 基本クラス ライブラリ。
- 必要に応じて、1 つまたは複数のアプリケーション フレームワーク。 次に例を示します。 .NET Framework と .NET 5 には、[ASP.NET](https://www.asp.net/)、[Windows フォーム](/dotnet/desktop/winforms/windows-forms-overview)、[Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) が含まれています。
- 必要に応じて、開発ツール。 一部の開発ツールは、複数の実装間で共有されます。

Microsoft によって、次の 4 つの .NET 実装がサポートされています。

- .NET 5 (および .NET Core) 以降のバージョン
- .NET Framework
- Mono
- UWP

今では .NET 5 が主要な実装であり、現在進行中の開発の対象になっています。 .NET 5 は、複数のプラットフォームと、Windows デスクトップ アプリ、クロスプラットフォーム コンソール アプリ、クラウド サービス、Web サイトなどの多くのワークロードをサポートする、単一のコード ベースを基にして構築されています。

### <a name="net-5"></a>.NET 5

.NET 5 は .NET のクラスプラットフォームの実装であり、サーバーとクラウドの大規模なワークロードを処理するように設計されています。 また、デスクトップ アプリなどの他のワークロードもサポートされています。 Windows、macOS、および Linux で実行されます。 .NET Standard が実装されているので、.NET Standard をターゲットとするコードは .NET 5 上で実行できます。 [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core)、[Windows フォーム](/dotnet/desktop/winforms/windows-forms-overview)、[Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) はすべて、.NET 5 で実行されます。

詳細については、次のリソースを参照してください。

- [.NET の概要](../core/introduction.md)
- [サーバー アプリ用 .NET 5 と .NET Framework の選択](choosing-core-framework-server.md)
- [.NET 5 と .NET Standard](net-standard.md#net-5-and-net-standard)

### <a name="net-framework"></a>.NET Framework

.Net Framework は、2002 年からリリースされている元の .NET 実装です。 バージョン 4.5 以降では .NET Standard が実装されているので、.NET Standard をターゲットとするすべてのコードが .NET Framework 4.5 以降で実行できます。 Windows フォームと WPF での Windows デスクトップ開発用 API など、追加の Windows 固有 API が含まれます。 .NET Framework は、Windows デスクトップ アプリケーション開発用に最適化されています。

詳細については、[.NET Framework ガイド](../framework/index.yml)に関する記事を参照してください。

### <a name="mono"></a>Mono

Mono は、主に小規模なランタイムが必要な場合に使用される .NET 実装です。 Android、macOS、iOS、tvOS、および watchOS 上の Xamarin アプリケーションで利用されるランタイムで、フットプリントが小さいことに重点を置いています。 Mono は、Unity エンジンを使用して構築されたゲームでも利用されます。

現在公開されているすべての .NET Standard バージョンをサポートしています。

これまで Mono は .NET Framework の多数の API を実装し、Unix で人気の高い機能の一部をエミュレートしていました。 また、Unix のそのような機能に依存する .NET アプリケーションを実行するために使用されることもあります。

一般的に Mono は、Just-In-Time コンパイラと共に使用されますが、iOS のようなプラットフォームに使用される完全な静的コンパイラ (Ahead Of Time コンパイル) としても機能します。

詳細については、[Mono のドキュメント](https://www.mono-project.com/docs/)を参照してください。

### <a name="universal-windows-platform-uwp"></a>ユニバーサル Windows プラットフォーム (UWP)

UWP は、モノのインターネット (IoT) 用に最新のタッチ対応の Windows アプリケーションとソフトウェアを構築するために使われる .NET 実装です。 PC、タブレット、携帯電話、Xbox など、ターゲットにされる可能性があるさまざまな種類のデバイスを統一するように設計されています。 UWP は、一元的なアプリ ストア、実行環境 (AppContainer)、Win32 の代わりに使う Windows API のセット (WinRT) など、多くのサービスを提供します。 アプリは、C++、C#、Visual Basic、および JavaScript で記述することができます。

詳細については、[ユニバーサル Windows プラットフォームの概要](/windows/uwp/get-started/universal-application-platform-guide)に関する記事を参照してください。

## <a name="net-runtimes"></a>.NET ランタイム

ランタイムは、マネージド プログラムの実行環境です。 OS は、ランタイム環境の一部ですが、.NET ランタイムの一部ではありません。 .NET ランタイムの例を次に示します。

- .NET Framework 用共通言語ランタイム (CLR)
- .NET 5 用共通言語ランタイム (CLR)
- ユニバーサル Windows プラットフォーム用 .NET Native
- Xamarin.iOS、Xamarin.Android、Xamarin.Mac、Mono デスクトップ フレームワーク用ランタイム

## <a name="net-tooling-and-common-infrastructure"></a>.NET のツールと共通インフラストラクチャ

すべての .NET 実装と連携する多様なツールやインフラストラクチャ コンポーネントにアクセスできます。 これらのツールとコンポーネントは次のとおりです。

- .NET 言語とコンパイラ
- .NET プロジェクト システム ( *.csproj*、 *.vbproj*、および *.fsproj* ファイルに基づく)
- [MSBuild](/visualstudio/msbuild/msbuild) (プロジェクトのビルドに使用されるビルド エンジン)
- [NuGet](/nuget/) (Microsoft の .NET 用パッケージ マネージャー)
- オープン ソースのビルド オーケストレーション ツール ([CAKE](https://cakebuild.net/)、[FAKE](https://fake.build/) など)

詳細については、「[ツールと生産性](../core/introduction.md#tools-and-productivity)」を参照してください。

## <a name="applicable-standards"></a>適用可能な標準

C# 言語および共通言語基盤 (CLI) の仕様は、[エクマ インターナショナル&reg;](https://www.ecma-international.org/)を介して標準化されています。 これらの標準の初版は、2001 年 12 月に Ecma によって公開されました。

標準の後続の改訂は、Programming Languages Technical Committee ([TC49](https://www.ecma-international.org/technical-committees/tc49/)) 内の TC49-TG2 (C#) および TC49-TG3 (CLI) タスク グループによって展開され、Ecma General Assembly で採用され、その後、ISO Fast-Track プロセスを介して ISO/IEC JTC 1 で採用されました。

### <a name="latest-standards"></a>最新の標準

[C#](https://www.ecma-international.org/publications-and-standards/standards/ecma-334/) および [CLI](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) ([TR-84](https://www.ecma-international.org/publications-and-standards/technical-reports/ecma-tr-84/)) については、次の公式の Ecma ドキュメントを入手できます。

- **The C# Language Standard (version 5.0)** (C# 言語標準 (バージョン 5.0)):[ECMA-334.pdf](https://www.ecma-international.org/wp-content/uploads/ECMA-334_5th_edition_december_2017.pdf)
- **The Common Language Infrastructure** (共通言語基盤):[ECMA-335.pdf](https://www.ecma-international.org/wp-content/uploads/ECMA-335_6th_edition_june_2012.pdf)。
- **Information Derived from the Partition IV XML File** (Partition IV XML ファイルから派生した情報):[ECMA-084.pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) 形式。

公式の ISO/IEC ドキュメントは、ISO/IEC の「[Publicly Available Standards](https://standards.iso.org/ittf/PubliclyAvailableStandards/)」(公開されている標準) ページから入手できます。 そのページのリンクを次に示します。

- **情報技術 - プログラミング言語 - C#** :[ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **情報技術 - 共通言語基盤 (CLI) パーティション I から VI**:[ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **情報技術 - 共通言語基盤 (CLI) - Partition IV XML ファイルから派生した情報に関するテクニカル レポート**:[ISO/IEC TR 23272:2011](https://www.ecma-international.org/wp-content/uploads/ECMA_TR-84_6th_edition_june_2012.pdf)

## <a name="see-also"></a>関連項目

- [.NET の概要](../core/introduction.md)
- [.NET Standard の概要](net-standard.md)
- [サーバー アプリ用 .NET 5 と .NET Framework の選択](choosing-core-framework-server.md)
- [.NET Framework ガイド](../framework/index.yml)
- [C# のガイド](../csharp/index.yml)
- [F# のガイド](../fsharp/index.yml)
- [Visual Basic のガイド](../visual-basic/index.yml)
