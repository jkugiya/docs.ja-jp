---
title: コードを移植するために依存関係を分析する
description: .NET Framework から .NET にプロジェクトを移植するために、外部の依存関係を分析する方法を説明します。
author: cartermp
ms.date: 03/04/2021
ms.openlocfilehash: 4619243cf300e248be45e4b2a4d5541c3b3e1cb5
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604919"
---
# <a name="analyze-your-dependencies-to-port-code-from-net-framework-to-net"></a>.NET Framework から .NET にコードを移植するために依存関係を分析する

.NET または .NET Standard にコードを移植するには、依存関係を理解する必要があります。 外部の依存関係は、プロジェクトで参照する NuGet パッケージまたは `.dll` ファイルですが、これはユーザーが構築するものではありません。

コードを .NET Standard 2.0 以前に移植すると、.NET Framework と .NET の両方で使用できるようになります。 ただし、.NET Framework でライブラリを使用する必要がない場合は、最新バージョンの .NET をターゲットにすることを検討してください。

## <a name="migrate-your-nuget-packages-to-packagereference"></a>NuGet パッケージを `PackageReference` に移行する

.NET では、NuGet 参照に [_packages.config_](/nuget/reference/packages-config) ファイルを使用することはできません。 .NET と .NET Framework はどちらも [PackageReference](/nuget/consume-packages/package-references-in-project-files) を使用してパッケージの依存関係を指定できます。 _packages.config_ を使用してプロジェクトにパッケージを指定している場合は、`PackageReference` 形式に変換します。

移行方法については、「[packages.config から PackageReference への移行](/nuget/reference/migrate-packages-config-to-package-reference)」を参照してください。

## <a name="upgrade-your-nuget-packages"></a>NuGet パッケージをアップグレードする

プロジェクトを `PackageReference` 形式に移行した後、お使いのパッケージが .NET と互換性があるかどうかを確認します。

まず、パッケージを使用可能な最新バージョンにアップグレードします。 これは、Visual Studio の NuGet パッケージマネージャーの UI で行うことができます。 パッケージの新しいバージョンの依存関係は、既に .NET Core と互換性がある可能性があります。

## <a name="analyze-your-package-dependencies"></a>パッケージの依存関係を分析する

変換およびアップグレードしたパッケージの依存関係が .NET Core で動作することをまだ確認していない場合は、次のいくつかの方法で行うことができます。

### <a name="analyze-nuget-packages-using-nugetorg"></a>nuget.org を使用して NuGet パッケージを分析する

[nuget.org](https://www.nuget.org/) のパッケージのページの **[Dependencies]\(依存関係\)** のセクションで、各パッケージでサポートされる TFM (ターゲット フレームワーク モニカー) を確認できます。

互換性はこのサイトを使用して確認するのが簡単ですが、**依存関係** の情報はすべてのパッケージのサイトにはありません。

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>NuGet パッケージ エクスプローラーを使用して NuGet パッケージを分析する

NuGet パッケージ自体はフォルダーのセットであり、プラットフォーム固有のアセンブリが含まれます。 パッケージ内に互換性のあるアセンブリを含むフォルダーがあるかどうかを確認します。

NuGet パッケージ フォルダーを調べる最も簡単な方法は、[NuGet パッケージ エクスプローラー](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ツールを使用することです。 これをインストールした後、次の手順を使用してフォルダー名を確認します。

1. NuGet パッケージ エクスプローラーを開きます。
2. **[Open package from online feed]\(オンライン フィードからパッケージを開く\)** をクリックします。
3. パッケージの名前を検索します。
4. 検索結果からパッケージ名を選択し、 **[開く]** をクリックします。
5. 右側にある *lib* フォルダーを展開し、フォルダー名を確認します。

`netstandardX.Y`、`netX.Y`、`netcoreappX.Y` のパターンのいずれかを使用するフォルダー名を検索します。

これらの値は[ターゲット フレームワーク モニカー (TFM)](../../standard/frameworks.md) であり、[.NET Standard](../../standard/net-standard.md)、.NET、.NET Core のバージョンにマップされます。これらはすべて .NET と互換性があります。

> [!IMPORTANT]
> パッケージでサポートされている TFM を調べる場合は、`netstandard*` 以外の TFM は、.NET 5、.Net Core、.NET Framework など、.NET の特定の実装をターゲットとしていることにご注意ください。 .NET 5 以降では、`net*` TFM (オペレーティング システムの指定なし) によって、`netstandard*` が[移植可能なターゲット](../../standard/net-standard.md#net-5-and-net-standard)として効果的に置き換えられます。 たとえば、`net5.0` は .NET 5 API サーフェイスをターゲットとし、クロスプラットフォームに対応していますが、`net5.0-windows` は Windows オペレーティング システムに実装されている .NET 5 API サーフェイスをターゲットとしています。

## <a name="net-framework-compatibility-mode"></a>.NET Framework 互換モード

NuGet パッケージの分析後、.NET Framework のみをターゲットとしていることがわかる場合があります。

.NET Standard 2.0 以降、.NET Framework 互換モードが導入されました。 この互換モードにより、.NET Standard および .NET Core プロジェクトは .NET Framework ライブラリを参照できます。 .NET Framework ライブラリの参照はすべてのプロジェクトで機能するわけではありません (例えばライブラリで Windows Presentation Foundation (WPF) API を使用していても、多くの移植シナリオがブロック解除される場合など)。

[`Huitian.PowerCollections`](https://www.nuget.org/packages/Huitian.PowerCollections) など、プロジェクトで .NET Framework をターゲットとする NuGet パッケージを参照すると、次の例のようなパッケージ フォールバック警告 ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) が表示されます。

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

この警告は、パッケージを追加したとき、およびプロジェクトでそのパッケージを確実にテストするためにビルドするたびに表示されます。 プロジェクトが予期したとおりに動作している場合は、Visual Studio でパッケージ プロパティを編集するか、任意のコード エディターでプロジェクト ファイルを手動で編集して、この警告を非表示にすることができます。

プロジェクト ファイルを編集して警告を非表示にするには、警告を非表示にするパッケージの `PackageReference` エントリを見つけて、`NoWarn` 属性を追加します。 `NoWarn` 属性では、すべての警告 ID のコンマ区切りリストを受け入れます。 次の例は、プロジェクト ファイルを手動で編集して、`Huitian.PowerCollections` パッケージの `NU1701` 警告を非表示にする方法を示しています。

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Visual Studio でコンパイラ警告を非表示にする方法の詳細については、「[NuGet パッケージの警告を非表示にする](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages)」を参照してください。

## <a name="if-nuget-packages-wont-run-on-net"></a>NuGet パッケージが .NET で実行されない場合

依存している NuGet パッケージが .NET Core で動作しない場合の対処方法はいくつかあります。

- プロジェクトがオープン ソースで、GitHub のような場所にホストされている場合、直接開発者に連絡することができます。
- [nuget.org](https://www.nuget.org/) で直接作成者に連絡することができます。パッケージを検索し、パッケージのページの左側にある **[Contact Owners]\(所有者に問い合わせる\)** をクリックします。
- 使用していたパッケージと同じタスクを実行する、.NET Core で実行される別のパッケージを検索することができます。
- パッケージが行っていたコードを自分で記述できます。
- 少なくともパッケージの互換バージョンが利用可能になるまでは、アプリの機能を変更することで、パッケージの依存関係を削除することができます。

オープン ソース プロジェクトの保守管理者および NuGet パッケージの発行者の多くは、ボランティアであることを忘れないでください。 彼らは、その分野に関心があるために無償で作業を行っており、多くの場合、日中に別の仕事を抱えています。 .NET Core のサポートを求めるために連絡する際には、この点を考慮してください。

これらの方法のいずれでも問題を解決できない場合、後日 .NET Core に移植しなければならない場合があります。

.NET チームは .NET Core のサポートでどのライブラリが最も重要かを知りたいと考えています。 使用したいライブラリについて、dotnet@microsoft.com にメールを送ることができます。

## <a name="analyze-non-nuget-dependencies"></a>NuGet 以外の依存関係の分析

ファイル システム内の DLL など、NuGet パッケージではない依存関係がある場合もあります。 その依存関係の移植性を調べる唯一の方法が、[.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) ツールを実行することです。 このツールでは、.NET Framework をターゲットとするアセンブリを分析し、.NET Core などの他の .NET プラットフォームに移植できない API を特定します。 このツールはコンソール アプリケーションまたは [Visual Studio 拡張機能](../../standard/analyzers/portability-analyzer.md)として実行できます。

## <a name="next-steps"></a>次の手順

- [.NET Framework から .NET への移植の概要](index.md)
- [ライブラリを移植する](libraries.md)
