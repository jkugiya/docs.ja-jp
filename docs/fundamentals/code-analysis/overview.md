---
title: .NET のコード分析
titleSuffix: ''
description: .NET SDK のソース コード分析について説明します。
ms.date: 12/04/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: 9fbeee7475b49a5b6514d4983142ae3be5a2f026
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605296"
---
# <a name="overview-of-net-source-code-analysis"></a>.NET ソース コード分析の概要

.NET のコンパイラ プラットフォーム (Roslyn) アナライザーでは、お使いの C# または Visual Basic コードについて、コードの品質やスタイルに関する問題を検査できます。 .NET 5.0 以降、これらのアナライザーは .NET SDK に含まれており、個別にインストールする必要はありません。 プロジェクトが .NET 5 以降をターゲットとしている場合は、既定でコード分析が有効になっています。 プロジェクトが .NET Core、.NET Standard、.NET Framework などの別の .NET 実装をターゲットとしている場合は、[EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティを `true` に設定することにより、コード分析を手動で有効にする必要があります。

.NET 5 以降の SDK に移行しない場合、SDK スタイル以外の .NET Framework プロジェクトを使用する場合、または NuGet パッケージベースのモデルを使用する場合は、[Microsoft.CodeAnalysis.NetAnalyzers NuGet パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)でアナライザーを使用することもできます。 オンデマンドのバージョン更新には、パッケージベースのモデルを使用することをお勧めします。

> [!NOTE]
> .NET アナライザーは、ターゲット フレームワークに依存しません。 つまり、プロジェクトが特定の .NET 実装をターゲットにする必要はありません。 アナライザーは、`net5.0` のほか、以前のバージョンの .NET (`netcoreapp3.1` や `net472` など) をターゲットとするプロジェクトで機能します。 ただし、[EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティを使用してコード分析を有効にするには、プロジェクトが[プロジェクト SDK](../../core/project-sdk/overview.md) を参照する必要があります。

アナライザーによってルール違反が検出されると、各ルールの[構成](configuration-options.md)方法に応じて、修正候補、警告、またはエラーとして報告されます。 コード分析違反は、コンパイラ エラーと区別するために "CA" または "IDE" というプレフィックスで示されます。

## <a name="code-quality-analysis"></a>コード品質の分析

*コード品質の分析* ("CAxxxx") ルールでは、お使いの C# コードまたは Visual Basic コードにセキュリティ、パフォーマンス、設計などの問題がないか検査が行われます。 分析は、.NET 5.0 以降をターゲットとするプロジェクトで既定で有効になっています。 [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティを `true` に設定すると、以前のバージョンの .NET を対象とするプロジェクトで、.NET コード分析を有効にできます。 `EnableNETAnalyzers` を `false` に設定すると、自分のプロジェクトでコード分析を無効にすることもできます。

> [!TIP]
> Visual Studio を使用している場合:
>
> - 多くのアナライザー ルールには、"*コード修正*" が関連付けられており、これを適用して問題を修正できます。 コード修正は、電球アイコン メニューに示されます。
> - コード分析を有効または無効にするには、ソリューション エクスプローラーでプロジェクトを右クリックし、 **[プロパティ]**  >  **[コード分析]** タブ > **[Enable .NET analyzers]\(.NET アナライザーの有効化\)** を選択します。

### <a name="enabled-rules"></a>有効なルール

.NET 5.0 では、既定で次のルールが有効になっています。

| 診断 ID | カテゴリ | 重大度 | 説明 |
| - | - | - | - |
| [CA1416](/visualstudio/code-quality/ca1416) | 相互運用性 | 警告 | プラットフォーム互換性アナライザー |
| [CA1417](/visualstudio/code-quality/ca1417) | 相互運用性 | 警告 | P/Invoke の文字列パラメーターに `OutAttribute` を使用しないでください |
| [CA1831](/visualstudio/code-quality/ca1831) | パフォーマンス | 警告 | 該当する場合、文字列に範囲ベースのインデクサーの代わりに `AsSpan` を使用します |
| [CA2013](/visualstudio/code-quality/ca2013) | [信頼性] | 警告 | 値の型に `ReferenceEquals` を使用しないでください |
| [CA2014](/visualstudio/code-quality/ca2014) | [信頼性] | 警告 | ループで `stackalloc` を使用しないでください |
| [CA2015](/visualstudio/code-quality/ca2015) | [信頼性] | 警告 | <xref:System.Buffers.MemoryManager%601> から派生した型にはファイナライザーを定義しないでください |
| [CA2200](/visualstudio/code-quality/ca2200) | 使用法 | 警告 | スタック詳細を保持するために再度スローします
| [CA2247](/visualstudio/code-quality/ca2247) | 使用法 | 警告 | TaskCompletionSource コンストラクターに渡される引数は、<xref:System.Threading.Tasks.TaskContinuationOptions> ではなく <xref:System.Threading.Tasks.TaskCreationOptions> 列挙型である必要があります |

これらのルールの重要度を変更して、無効にするか、エラーに昇格させることができます。 [追加のルールを有効にする](#enable-additional-rules)こともできます。

- 各 .NET SDK バージョンに含まれるルールの一覧については、[アナライザーのリリース](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)に関するページを参照してください。
- すべてのコード品質ルールの一覧については、「[コード品質ルール](quality-rules/index.md)」を参照してください。

### <a name="enable-additional-rules"></a>追加のルールを有効にする

"*分析モード*" とは、事前に定義されたコード分析構成 (いずれのルールも有効になっていない、一部またはすべてのルールが有効になっている) を意味します。 既定の分析モードでは、少数のルールのみが[ビルド警告として有効](#enabled-rules)になっています。 プロジェクト ファイルで [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) プロパティを設定することにより、プロジェクトの分析モードを変更できます。 次の値を使用できます。

| 値 | 説明 |
| - | - |
| `AllDisabledByDefault` | これは、最も標準のモードです。 すべてのルールは、既定で無効になっています。 個々のルールを選択的に[オプトイン](configuration-options.md)して有効にすることができます。<br /><br />`<AnalysisMode>AllDisabledByDefault</AnalysisMode>` |
| `AllEnabledByDefault` | これは、最もアグレッシブなモードです。 すべてのルールがビルド警告として有効になっています。 個々のルールを選択的に[オプトアウト](configuration-options.md)して無効にすることができます。<br /><br />`<AnalysisMode>AllEnabledByDefault</AnalysisMode>` |
| `Default` | 既定のモード。この場合、いくつかのルールは警告として有効になっており、一部のルールは対応するコード修正の Visual Studio IDE 修正候補としてのみ有効になっており、残りは完全に無効になっています。 個々のルールを選択的に[オプトインまたはオプトアウト](configuration-options.md)して無効にすることができます。<br /><br />`<AnalysisMode>Default</AnalysisMode>` |

使用可能な各ルールの既定の重要度と、既定の分析モードでルールが有効になっているかどうかを確認するには、[ルールの完全な一覧](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)を参照してください。

### <a name="treat-warnings-as-errors"></a>警告をエラーとして扱う

プロジェクトをビルドするときに `-warnaserror` フラグを使用すると、すべてのコード分析の警告もエラーとして扱われます。 `-warnaserror` の存在下でコード品質の警告 (CAxxxx) がエラーとして扱われないようにするには、プロジェクト ファイル内の `CodeAnalysisTreatWarningsAsErrors` MSBuild プロパティを `false` に設定します。

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

コード分析の警告は引き続き表示されますが、ビルドが中断することはありません。

### <a name="latest-updates"></a>最新の更新プログラム

既定では、新しいバージョンの .NET SDK にアップグレードするときに、最新のコード分析ルールと、ルールの既定の重要度を取得します。 この動作が望ましくない (たとえば、新しいルールが有効または無効にならないようにする) 場合は、次のいずれかの方法でオーバーライドできます。

- `AnalysisLevel` MSBuild プロパティを特定の値に設定して、警告をそのセットにロックします。 より新しい SDK にアップグレードすると、これらの警告のバグ修正が引き続き表示されますが、新しい警告は有効にならず、既存の警告は無効になりません。 たとえば、ルールのセットを、.NET SDK バージョン 5.0 に付属するセットにロックするには、プロジェクト ファイルに次のエントリを追加します。

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > `AnalysisLevel` プロパティの既定値は `latest` です。これは、より新しいバージョンの .NET SDK に移行するときに、常に最新のコード分析ルールを取得することを意味します。

  詳細情報、および使用可能な値の一覧については、「[AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel)」を参照してください。

- [Microsoft.CodeAnalysis.NetAnalyzers NuGet パッケージ](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers)をインストールして、.NET SDK の更新プログラムからルールの更新を分離します。 .NET 5 以降をターゲットとするプロジェクトでは、パッケージをインストールすると、組み込みの SDK アナライザーがオフになります。 NuGet パッケージよりも新しいバージョンのアナライザー アセンブリが SDK に含まれている場合は、ビルド警告が表示されます。 警告を無効にするには、`_SkipUpgradeNetAnalyzersNuGetWarning` プロパティを `true` に設定します。

  > [!NOTE]
  > Microsoft.CodeAnalysis.NetAnalyzers NuGet パッケージをインストールする場合は、プロジェクト ファイルまたは *Directory.Build.props* ファイルに [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティを追加しないでください。 NuGet パッケージがインストールされ、`EnableNETAnalyzers` プロパティが `true` に設定されると、ビルド警告が生成されます。

## <a name="code-style-analysis"></a>コードスタイルの分析

"*コードスタイルの分析*" ("IDExxxx") ルールを使用すると、コードベースで一貫性のあるコードスタイルを定義および維持することができます。 既定の有効化設定は次のとおりです。

- コマンドライン ビルド: コードスタイルの分析は、既定でコマンドライン ビルドのすべての .NET プロジェクトに対して無効になっています。

  .NET 5.0 以降では、コマンド ラインと Visual Studio 内の両方で、[ビルド時にコードスタイルの分析を有効にする](#enable-on-build)ことができます。 コード スタイルに違反すると、"IDE" プレフィックスが付いた警告またはエラーが表示されます。 これにより、ビルド時に一貫したコード スタイルを適用できます。

- Visual Studio: コードスタイルの分析は、既定で Visual Studio 内のすべての .NET プロジェクトに対して[コード リファクタリングのクイック アクション](/visualstudio/ide/code-generation-in-visual-studio)として有効になっています。

コードスタイルの分析ルールの完全な一覧については、「[コードスタイル ルール](style-rules/index.md)」を参照してください。

### <a name="enable-on-build"></a>ビルド時に有効にする

.NET 5.0 SDK 以降のバージョンでは、コマンドラインや Visual Studio でビルドするときに、コードスタイルの分析を有効にすることができます (ただし、パフォーマンス上の理由から、[いくつかのコードスタイル ルール](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95)は Visual Studio IDE にのみ適用されます)。

ビルド時にコードスタイルの分析を有効にするには、次の手順に従います。

1. MSBuild プロパティ [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) を `true` に設定します。

1. *.editorconfig* ファイルで、ビルド時に実行する各 "IDE" コード スタイル ルールを警告またはエラーとして[構成](configuration-options.md)します。 次に例を示します。

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   また、既定では、カテゴリ全体を警告またはエラーとして構成してから、ビルド時に実行しないカテゴリのルールを選択的にオフにすることもできます。 次に例を示します。

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

> [!NOTE]
> コードスタイルの分析機能は試験段階にあり、.NET 5 リリースと .NET 6 リリースの間で変更される可能性があります。

## <a name="suppress-a-warning"></a>警告を抑制する

ルール違反を抑制する方法の 1 つとして、EditorConfig ファイルでそのルール ID の重要度オプションを `none` に設定します。 次に例を示します。

```ini
dotnet_diagnostic.CA1822.severity = none
```

詳細情報、および警告を非表示にするその他の方法については、「[コード分析の警告を抑制する方法](suppress-warnings.md)」を参照してください。

## <a name="third-party-analyzers"></a>サード パーティのアナライザー

公式の .NET アナライザーに加えて、[StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、[Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/)、[XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/)、[Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/) などのサードパーティ製アナライザーをインストールすることもできます。

## <a name="see-also"></a>関連項目

- [コード品質の分析ルールのリファレンス](quality-rules/index.md)
- [コード スタイルの分析ルールのリファレンス](style-rules/index.md)
- [Visual Studio でのコード分析](/visualstudio/code-quality/roslyn-analyzers-overview)
- [.NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md)
- [チュートリアル: 最初のアナライザーとコード修正を作成する](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
