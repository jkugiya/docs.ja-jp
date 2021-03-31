---
title: Microsoft.NET.Sdk の MSBuild プロパティ
description: .NET SDK によって認識される MSBuild のプロパティと項目のリファレンスです。
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 18f2be734fa10e2fd4977166ab4334332b120a91
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604763"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a>.NET SDK プロジェクトの MSBuild リファレンス

このページは、.NET プロジェクトの構成に使用できる、MSBuild のプロパティと項目のリファレンスです。

> [!NOTE]
> このページの編集は進行中であり、.NET SDK の便利な MSBuild プロパティがすべて記載されている訳ではありません。 一般的な MSBuild プロパティの一覧については、「[MSBuild プロジェクトの共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)」を参照してください。

## <a name="framework-properties"></a>フレームワークのプロパティ

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

`TargetFramework` プロパティには、アプリのターゲット フレームワーク バージョンを指定します。 有効なターゲット フレームワーク モニカーの一覧については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md#supported-target-frameworks)」を参照してください。

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

詳細については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md)」を参照してください。

### <a name="targetframeworks"></a>TargetFrameworks

アプリで複数のプラットフォームをターゲットにする場合は、`TargetFrameworks` プロパティを使用します。 有効なターゲット フレームワーク モニカーの一覧については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md#supported-target-frameworks)」を参照してください。

> [!NOTE]
> `TargetFramework` (単数形) が指定されている場合、このプロパティは無視されます。

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

詳細については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md)」を参照してください。

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> このプロパティは、`netstandard1.x` を使用するプロジェクトにのみ適用されます。 `netstandard2.x` を使用するプロジェクトには適用されません。

メタパッケージ バージョンよりも低いフレームワーク バージョンを指定する場合は、`NetStandardImplicitPackageVersion` プロパティを使用します。 次の例のプロジェクト ファイルは、`netstandard1.3` をターゲットにしていますが、`NETStandard.Library` の 1.6.0 バージョンを使用しています。

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a>パッケージのプロパティ

`PackageId`、`PackageVersion`、`PackageIcon`、`Title`、`Description` などのプロパティを指定し、プロジェクトから作成されたパッケージについて説明できます。 以上のプロパティとその他のプロパティの詳細については、「[pack ターゲット](/nuget/reference/msbuild-targets#pack-target)」を参照してください。

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-items-and-metadata"></a>プロパティ、項目、メタデータを発行する

- [AppendRuntimeIdentifierToOutputPath](#appendruntimeidentifiertooutputpath)
- [AppendTargetFrameworkToOutputPath](#appendtargetframeworktooutputpath)
- [CopyLocalLockFileAssemblies](#copylocallockfileassemblies)
- [CopyToPublishDirectory](#copytopublishdirectory)
- [LinkBase](#linkbase)
- [PreserveCompilationContext](#preservecompilationcontext)
- [PreserveCompilationReferences](#preservecompilationreferences)
- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="copytopublishdirectory"></a>CopyToPublishDirectory

MSBuild 項目の `CopyToPublishDirectory` メタデータにより、項目が発行ディレクトリにコピーされるタイミングが制御されます。 使用できる値は、項目が変更された場合にのみコピーする `PreserveNewest`、常に項目をコピーする `Always`、項目をコピーしない `Never` です。 パフォーマンスの観点からは、インクリメンタル ビルドが有効になるので `PreserveNewest` をお勧めします。

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a>LinkBase

プロジェクト ディレクトリとそのサブディレクトリの外部にある項目の場合、発行先で項目のコピー先を決定するために、項目の [Link メタデータ](/visualstudio/msbuild/common-msbuild-item-metadata)が使用されます。 また、プロジェクト ツリーの外部にある項目が Visual Studio の [ソリューション エクスプローラー] ウィンドウにどのように表示されるかも、`Link` によって決定されます。

プロジェクト コーンの外部にある項目に対して `Link` が指定されていない場合は、既定で `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)` になります。 `LinkBase` を使用して、プロジェクト コーンの外部の項目に適切なベース フォルダーを指定できます。 ベース フォルダーの下のフォルダー階層は、`RecursiveDir` によって保持されます。 `LinkBase` を指定しないと、それは `Link` パスから省略されます。

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

次の図は、前の項目の `Include` glob によって含められるファイルがソリューション エクスプローラーにどのように表示されるかを示したものです。

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="LinkBase メタデータが指定された項目が表示されているソリューション エクスプローラー。":::

### <a name="appendtargetframeworktooutputpath"></a>AppendTargetFrameworkToOutputPath

`AppendTargetFrameworkToOutputPath` プロパティは、[ターゲット フレームワーク モニカー (TFM)](../../standard/frameworks.md) を出力パス ([OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters) で定義されている) に追加するかどうかを制御します。 .NET SDK はターゲット フレームワークを、それが存在する場合にはランタイム識別子を出力パスに自動的に追加します。 `AppendTargetFrameworkToOutputPath` を `false` に設定すると、TFM が出力パスに追加されなくなります。 ただし、出力パスに TFM がないと、複数のビルド成果物が相互に上書きされる可能性があります。

たとえば、.NET 5.0 アプリの場合、出力パスは次の設定を使用して `bin\Debug\net5.0` から `bin\Debug` に変更されます。

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a>AppendRuntimeIdentifierToOutputPath

`AppendRuntimeIdentifierToOutputPath` プロパティは、[ランタイム識別子 (RID)](../rid-catalog.md) を出力パスに追加するかどうかを制御します。 .NET SDK はターゲット フレームワークを、それが存在する場合にはランタイム識別子を出力パスに自動的に追加します。 `AppendRuntimeIdentifierToOutputPath` を `false` に設定すると、RID が出力パスに追加されなくなります。

たとえば、.NET 5.0 アプリで RID が `win10-x64` の場合、出力パスは次の設定を使用して `bin\Debug\net5.0\win10-x64` から `bin\Debug\net5.0` に変更されます。

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a>CopyLocalLockFileAssemblies

`CopyLocalLockFileAssemblies` プロパティは、他のライブラリに依存しているプラグイン プロジェクトにとって便利です。 このプロパティを `true` に設定すると、NuGet パッケージの依存関係が出力ディレクトリにコピーされます。 つまり、`dotnet build` の出力を使用し、任意のコンピューターでプラグインを実行できます。

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> あるいは、`dotnet publish` を使用し、クラス ライブラリを発行できます。 詳細については、「[dotnet publish](../tools/dotnet-publish.md)」を参照してください。

### <a name="preservecompilationcontext"></a>PreserveCompilationContext

`PreserveCompilationContext` プロパティを使うと、ビルド時に使用されたのと同じ設定で、ビルドまたは発行されたアプリケーションで実行時により多くのコードをコンパイルできるようになります。 ビルド時に参照されるアセンブリは、出力ディレクトリの *ref* サブディレクトリにコピーされます。 参照アセンブリの名前は、コンパイラに渡されるオプションと共に、アプリケーションの *.deps.json* ファイルに格納されます。 この情報は、<xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> と <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> のプロパティを使用して取得できます。

この機能は、ほとんどの場合、Razor ファイルの実行時コンパイルをサポートするために ASP.NET Core MVC と Razor Pages によって内部的に使用されます。

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a>PreserveCompilationReferences

`PreserveCompilationReferences` プロパティは [PreserveCompilationContext](#preservecompilationcontext) プロパティと似ていますが、 *.deps.json* ファイルではなく、発行ディレクトリに参照アセンブリのみがコピーされる点が異なります。

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

詳細については、「[Razor SDK」の「プロパティ](/aspnet/core/razor-pages/sdk#properties)」を参照してください。

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`RuntimeIdentifier` プロパティを使用すると、プロジェクトに 1 つの[ランタイム識別子 (RID)](../rid-catalog.md) を指定できます。 RID により、自己完結型の展開を発行できます。

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`RuntimeIdentifiers` プロパティには、プロジェクトの[ランタイム識別子 (RID)](../rid-catalog.md) のセミコロン区切りリストを指定できます。 複数のランタイムに発行する必要がある場合は、このプロパティを使用します。 `RuntimeIdentifiers` は、復元時に適切な資産をグラフに確実に含めるために使用されます。

> [!TIP]
> `RuntimeIdentifier` (単数形) を使用すると、必要なランタイムが 1 つだけのとき、ビルドが速くなります。

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

`TrimmerRootAssembly` 項目ではアセンブリを "[*トリミング*](../deploying/trim-self-contained.md)" から除外できます。 トリミングとは、パッケージ化されたアプリケーションからランタイムの未使用部分を削除するプロセスです。 必要な参照がトリミングによって間違って削除されることもあります。

次の XML では、トリミングから `System.Security` アセンブリが除外されます。

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost` プロパティにより、デプロイ用にネイティブ実行可能ファイルを作成するかどうかが制御されます。 自己完結型の配置にはネイティブの実行可能ファイルが必要です。

.NET Core 3.0 以降のバージョンでは、既定でフレームワークに依存する実行可能ファイルが作成されます。 実行可能ファイルの生成を無効にするには、`UseAppHost` プロパティを `false` に設定します。

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

配置の詳細については、[.NET アプリケーションの配置](../deploying/index.md)に関するページを参照してください。

## <a name="compile-properties"></a>コンパイルのプロパティ

- [EmbeddedResourceUseDependentUponConvention](#embeddedresourceusedependentuponconvention)
- [LangVersion](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a>EmbeddedResourceUseDependentUponConvention

`EmbeddedResourceUseDependentUponConvention` プロパティは、リソース マニフェスト ファイル名が、リソース ファイルと併置されているソース ファイルの型情報から生成されるかどうかを定義します。 たとえば、*Form1.vb* が *Form1.cs* と同じフォルダーにあり、`EmbeddedResourceUseDependentUponConvention` が `true` に設定されている場合、生成された *.resources* ファイルは *Form1.cs* で定義されている最初の型から名前を受け取ります。 たとえば、`MyNamespace.Form1` が *Form1.cs* で定義されている最初の型である場合、生成されたファイル名は *MyNamespace.Form1.resources* になります。

> [!NOTE]
> `LogicalName`、`ManifestResourceName`、または `DependentUpon` メタデータが `EmbeddedResource` 項目に対して指定されている場合、そのリソース ファイルに対して生成されたマニフェスト ファイル名は、代わりにそのメタデータがベースになります。

既定では、新しい .NET プロジェクトでは、このプロパティは `true` に設定されます。 `false` に設定され、かつプロジェクト ファイルの `EmbeddedResource` 項目に `LogicalName`、`ManifestResourceName`、`DependentUpon` のメタデータがどれも指定されていない場合、リソース マニフェストのファイル名は、プロジェクトのルート名前空間と、 *.resx* ファイルへの相対ファイル パスがベースになります。 詳細については、「[リソース マニフェスト ファイルの名前付けの方法](../resources/manifest-file-names.md)」を参照してください。

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a>LangVersion

`LangVersion` プロパティを使用すると、特定のプログラミング言語バージョンを指定できます。 たとえば、C# プレビュー機能にアクセスする場合は、`LangVersion` を `preview` に設定します。

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

詳細については、「[C# 言語のバージョン管理](../../csharp/language-reference/configure-language-version.md#override-a-default)」を参照してください。

## <a name="default-item-inclusion-properties"></a>既定の項目の包含プロパティ

- [DefaultExcludesInProjectFolder](#defaultexcludesinprojectfolder)
- [DefaultItemExcludes](#defaultitemexcludes)
- [EnableDefaultCompileItems](#enabledefaultcompileitems)
- [EnableDefaultEmbeddedResourceItems](#enabledefaultembeddedresourceitems)
- [EnableDefaultItems](#enabledefaultitems)
- [EnableDefaultNoneItems](#enabledefaultnoneitems)

詳細については、「[既定で含まれるものと除外されるもの](overview.md#default-includes-and-excludes)」を参照してください。

### <a name="defaultitemexcludes"></a>DefaultItemExcludes

`DefaultItemExcludes` プロパティを使用して、含まれる、除外される、および削除の glob から除外するファイルとフォルダーの glob パターンを定義します。 既定では、 *./bin* および *./obj* フォルダーは、glob パターンから除外されます。

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a>DefaultExcludesInProjectFolder

`DefaultExcludesInProjectFolder` プロパティを使用して、含まれる、除外される、および削除の glob から除外する、プロジェクト フォルダーのファイルとフォルダーの glob パターンを定義します。 既定では、ピリオド (`.`) で始まるフォルダー ( *.git* や *.vs* など) は、glob パターンから除外されます。

このプロパティは、プロジェクト フォルダー内のファイルとフォルダーのみが考慮される点を除いて、`DefaultItemExcludes` プロパティとよく似ています。 glob パターンが意図せずにプロジェクト フォルダー外の項目と相対パスを照合する場合は、`DefaultItemExcludes` プロパティの代わりに `DefaultExcludesInProjectFolder` プロパティを使用します。

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a>EnableDefaultItems

`EnableDefaultItems` プロパティは、コンパイル項目、埋め込みリソース項目、および `None` 項目がプロジェクトに暗黙的に含まれるかどうかを制御します。 既定値は `true` です。 `EnableDefaultItems` プロパティを `false` に設定して、暗黙的なファイルの組み込みをすべて無効にします。

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a>EnableDefaultCompileItems

`EnableDefaultCompileItems` プロパティは、コンパイル項目がプロジェクトに暗黙的に含まれるかどうかを制御します。 既定値は `true` です。 `EnableDefaultCompileItems` プロパティを `false` に設定して、*.cs およびその他の言語拡張ファイルの暗黙的な包含を無効にします。

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a>EnableDefaultEmbeddedResourceItems

`EnableDefaultEmbeddedResourceItems` プロパティは、埋め込みリソース項目がプロジェクトに暗黙的に含まれるかどうかを制御します。 既定値は `true` です。 埋め込みリソース ファイルの暗黙的な包含を無効にするには、`EnableDefaultEmbeddedResourceItems` プロパティを `false` に設定します。

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a>EnableDefaultNoneItems

`EnableDefaultNoneItems` プロパティは、`None` 項目 (ビルド プロセスでロールがないファイル) がプロジェクトに暗黙的に含まれるかどうかを制御します。 既定値は `true` です。 `EnableDefaultNoneItems` プロパティを `false` に設定して、`None` 項目の暗黙的な包含を無効にします。

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a>コード分析のプロパティ

- [AnalysisLevel](#analysislevel)
- [AnalysisMode](#analysismode)
- [CodeAnalysisTreatWarningsAsErrors](#codeanalysistreatwarningsaserrors)
- [EnableNETAnalyzers](#enablenetanalyzers)
- [EnforceCodeStyleInBuild](#enforcecodestyleinbuild)

### <a name="analysislevel"></a>AnalysisLevel

`AnalysisLevel` プロパティを使用すると、コード分析レベルを指定できます。 たとえば、プレビューのコード アナライザーにアクセスする場合は、`AnalysisLevel` を `preview` に設定します。

既定値:

- プロジェクトのターゲットが .NET 5.0 以降の場合、または [AnalysisMode](#analysismode) プロパティを追加した場合、既定値は `latest` になります。
- それ以外の場合、このプロパティは、プロジェクト ファイルに明示的に追加されていない限り省略されます。

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

次の表で利用可能なオプションについて説明します。

| 値 | 説明 |
|-|-|
| `latest` | リリースされている最新のコード アナライザーが使用されます。 既定値です。 |
| `preview` | 最新のコード アナライザーが、プレビュー段階であっても使用されます。 |
| `5.0` | 新しいルールが使用可能な場合でも、.NET 5.0 リリースで有効になっていた一連のルールが使用されます。 |
| `5` | 新しいルールが使用可能な場合でも、.NET 5.0 リリースで有効になっていた一連のルールが使用されます。 |

> [!NOTE]
> このプロパティは、[プロジェクト SDK](overview.md) を参照しないプロジェクト (たとえば、Microsoft. CodeAnalysis. NetAnalyzers NuGet パッケージを参照するレガシ .NET Framework プロジェクト) のコード分析には影響しません。

### <a name="analysismode"></a>AnalysisMode

.NET 5.0 以降、.NET SDK には、すべての ["CA" コード品質ルール](../../fundamentals/code-analysis/quality-rules/index.md)が付属しています。 既定では、ビルド警告として[一部のルールが有効](../../fundamentals/code-analysis/overview.md#enabled-rules)になっています。 `AnalysisMode` プロパティを使用すると、既定で有効になるルールのセットをカスタマイズできます。 より積極的な (オプトアウト) 分析モード、またはより保守的な (オプトイン) 分析モードに切り替えることができます。 たとえば、既定ですべてのルールをビルド警告として有効にする場合は、値を `AllEnabledByDefault` に設定します。

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

次の表で利用可能なオプションについて説明します。

| 値 | 説明 |
|-|-|
| `Default` | 既定のモードでは、特定のルールがビルド警告として有効になり、特定のルールが Visual Studio IDE の提案として有効になり、残りは無効になります。 |
| `AllEnabledByDefault` | 積極的な (オプトアウト) モード。すべてのルールが既定でビルド警告として有効になっています。 個々のルールを選択的に[オプトアウト](../../fundamentals/code-analysis/configuration-options.md)して無効にすることができます。 |
| `AllDisabledByDefault` | 保守的な (オプトイン) モード。すべてのルールが既定で無効になっています。 個々のルールを選択的に[オプトイン](../../fundamentals/code-analysis/configuration-options.md)して有効にすることができます。 |

> [!NOTE]
> このプロパティは、[プロジェクト SDK](overview.md) を参照しないプロジェクト (たとえば、Microsoft. CodeAnalysis. NetAnalyzers NuGet パッケージを参照するレガシ .NET Framework プロジェクト) のコード分析には影響しません。

### <a name="codeanalysistreatwarningsaserrors"></a>CodeAnalysisTreatWarningsAsErrors

`CodeAnalysisTreatWarningsAsErrors` プロパティを使用すると、コード品質分析の警告 (CAxxxx) を警告として扱い、ビルドを中断するかどうかを構成できます。 プロジェクトをビルドするときに `-warnaserror` フラグを使用すると、[.NET コード品質分析](../../fundamentals/code-analysis/overview.md#code-quality-analysis)の警告もエラーとして扱われます。 コード品質分析の警告がエラーとして扱われないようにするには、プロジェクト ファイル内の `CodeAnalysisTreatWarningsAsErrors` MSBuild プロパティを `false` に設定します。

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a>EnableNETAnalyzers

.NET 5.0 以降をターゲットとするプロジェクトでは、[.NET コード品質分析](../../fundamentals/code-analysis/overview.md#code-quality-analysis)が既定で有効になっています。 以前のバージョンの .NET をターゲットとする SDK スタイルのプロジェクトで .NET コード分析を有効にするには、`EnableNETAnalyzers` プロパティを `true` に設定します。 任意のプロジェクトでコード分析を無効にするには、このプロパティを `false` に設定します。

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!NOTE]
> このプロパティは、特に、.NET 5+ SDK の組み込みアナライザーに適用されます。 これは NuGet コード分析パッケージをインストールするときには使用しないでください。

### <a name="enforcecodestyleinbuild"></a>EnforceCodeStyleInBuild

> [!NOTE]
> この機能は現在試験段階にあり、.NET 5 リリースと .NET 6 リリースの間で変更される可能性があります。

すべての .NET プロジェクトのビルドでは、[.NET コード スタイル分析](../../fundamentals/code-analysis/overview.md#code-style-analysis)は既定で無効になっています。 `EnforceCodeStyleInBuild` プロパティを `true` に設定して、.NET プロジェクトのコード スタイル分析を有効にできます。

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

警告またはエラーになるように[構成](../../fundamentals/code-analysis/overview.md#code-style-analysis)されているすべてのコード スタイル ルールは、ビルド時に実行され、違反を報告します。

## <a name="run-time-configuration-properties"></a>ランタイム構成プロパティ

アプリのプロジェクト ファイルに MSBuild プロパティを指定することで一部のランタイム動作を構成できます。 ランタイム動作のその他の構成方法については、[ランタイム構成設定](../run-time-config/index.md)に関する記事をご覧ください。

- [ConcurrentGarbageCollection](#concurrentgarbagecollection)
- [InvariantGlobalization](#invariantglobalization)
- [RetainVMGarbageCollection](#retainvmgarbagecollection)
- [ServerGarbageCollection](#servergarbagecollection)
- [ThreadPoolMaxThreads](#threadpoolmaxthreads)
- [ThreadPoolMinThreads](#threadpoolminthreads)
- [TieredCompilation](#tieredcompilation)
- [TieredCompilationQuickJit](#tieredcompilationquickjit)
- [TieredCompilationQuickJitForLoops](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a>ConcurrentGarbageCollection

`ConcurrentGarbageCollection` プロパティでは、[バックグラウンド (同時実行) ガベージ コレクション](../../standard/garbage-collection/background-gc.md)の有効または無効が設定されます。 この値を `false` に設定すると、バックグラウンド ガベージ コレクションが無効になります。 詳細については、「[バックグラウンド GC](../run-time-config/garbage-collector.md#background-gc)」を参照してください。

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a>InvariantGlobalization

`InvariantGlobalization` プロパティでは、アプリを *globalization-invariant* モードで実行するかどうかを設定します。このモードでは、カルチャ固有のデータにアクセスできません。 この値を `true` に設定すると、globalization-invariant モードで実行されます。 詳細については、「[インバリアント モード](../run-time-config/globalization.md#invariant-mode)」を参照してください。

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

`RetainVMGarbageCollection` プロパティでは、将来利用する目的で削除済みメモリ セグメントを待機一覧に載せるように、あるいは削除済みメモリ セグメントを解放するようにガベージ コレクターを設定します。 この値を `true` に設定すると、セグメントを待機一覧に載せるよう、ガベージ コレクターが命令されます。 詳細については、「[VM の保持](../run-time-config/garbage-collector.md#retain-vm)」を参照してください。

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

`ServerGarbageCollection` プロパティでは、アプリケーションで使用するガベージ コレクションとして[ワークステーション ガベージ コレクションまたはサーバー ガベージ コレクション](../../standard/garbage-collection/workstation-server-gc.md)を設定します。 この値を `true` に設定すると、サーバー ガベージ コレクションが使用されます。 詳細については、「[ワークステーションとサーバー](../run-time-config/garbage-collector.md#workstation-vs-server)」を参照してください。

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

`ThreadPoolMaxThreads` プロパティでは、ワーカー スレッド プールの最大スレッド数を設定します。 詳細については、「[最大スレッド数](../run-time-config/threading.md#maximum-threads)」を参照してください。

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

`ThreadPoolMinThreads` プロパティでは、ワーカー スレッド プールの最小スレッド数を設定します。 詳細については、「[最小スレッド数](../run-time-config/threading.md#minimum-threads)」を参照してください。

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a>TieredCompilation

`TieredCompilation` プロパティでは、Just-In-Time (JIT) コンパイラで[階層型コンパイル](../whats-new/dotnet-core-3-0.md#tiered-compilation)を使用するかどうかを設定します。 この値を `false` に設定すると、階層型コンパイルが無効になります。 詳細については、「[階層型コンパイル](../run-time-config/compilation.md#tiered-compilation)」を参照してください。

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a>TieredCompilationQuickJit

`TieredCompilationQuickJit` プロパティでは、JIT コンパイラでクイック JIT を使用するかどうかを設定します。 この値を `false` に設定すると、クイック JIT が無効になります。 詳細については、「[クイック JIT](../run-time-config/compilation.md#quick-jit)」を参照してください。

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a>TieredCompilationQuickJitForLoops

`TieredCompilationQuickJitForLoops` プロパティでは、ループを含むメソッドに対して JIT コンパイラでクリック JIT を使用するかどうかを設定します。 この値を `true` に設定すると、ループが含まれるメソッドでクイック JIT が有効になります。 詳細については、「[ループに対するクイック JIT](../run-time-config/compilation.md#quick-jit-for-loops)」を参照してください。

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a>プロパティと項目の参照

- [AssetTargetFallback](#assettargetfallback)
- [DisableImplicitFrameworkReferences](#disableimplicitframeworkreferences)
- [PackageReference](#packagereference)
- [ProjectReference](#projectreference)
- [参照](#reference)
- [復元関連のプロパティ](#restore-related-properties)

### <a name="assettargetfallback"></a>AssetTargetFallback

`AssetTargetFallback` プロパティを使用すると、プロジェクト参照と NuGet パッケージに対して、互換性のある追加のフレームワーク バージョンを指定できます。 たとえば、`PackageReference` を使用してパッケージの依存関係を指定し、そのパッケージにプロジェクトの `TargetFramework` と互換性のある資産が含まれない場合は、`AssetTargetFallback` プロパティが機能します。 参照されたパッケージの互換性は、`AssetTargetFallback` で指定された各ターゲット フレームワークを使用して再確認されます。 このプロパティは、非推奨のプロパティ `PackageTargetFallback` に代わるものです。

`AssetTargetFallback` プロパティを 1 つ以上の[ターゲット フレームワーク バージョン](../../standard/frameworks.md#supported-target-frameworks)に設定できます。

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a>DisableImplicitFrameworkReferences

`DisableImplicitFrameworkReferences` プロパティを使用すると、.NET Core 3.0 以降のバージョンを対象とする場合に、暗黙的な `FrameworkReference` の項目を制御できます。 .NET Core 2.1 または .NET Standard 2.0 以前のバージョンを対象としている場合は、これにより、メタパッケージ内のパッケージに対する暗黙的な [PackageReference](#packagereference) の項目が制御されます。 (メタパッケージは、他のパッケージの依存関係のみで構成されるフレームワーク ベースのパッケージです)。また、このプロパティを使用すると、.NET Framework を対象としている場合に、`System` や `System.Core` などの暗黙的な参照も制御できます。

このプロパティを `true` に設定して、暗黙的な `FrameworkReference` または [PackageReference](#packagereference) の項目を無効にします。 このプロパティを `true` に設定すると、必要なフレームワークまたはパッケージだけに明示的な参照を追加できます。

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="packagereference"></a>PackageReference

`PackageReference` 項目では、NuGet パッケージへの参照が定義されます。

`Include` 属性は、パッケージ ID を指定します。 `Version` 属性では、バージョンまたはバージョン範囲を指定します。 最小バージョン、最大バージョン、範囲、厳密一致を指定する方法については、「[バージョン範囲](/nuget/concepts/package-versioning#version-ranges)」を参照してください。 また、[アセット属性](#asset-attributes)をパッケージ参照に追加することもできます。

次の例のプロジェクト ファイル スニペットでは、[System.Runtime](https://www.nuget.org/packages/System.Runtime/) パッケージを参照しています。

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

詳細については、[プロジェクト ファイルのパッケージ参照](/nuget/consume-packages/package-references-in-project-files)に関するページを参照してください。

#### <a name="asset-attributes"></a>アセット属性

`IncludeAssets`、`ExcludeAssets`、`PrivateAssets` の各メタデータを、パッケージ参照に追加できます。

| 属性 | 説明 |
| - | - |
| `IncludeAssets` | `<PackageReference>` によって指定されているパッケージに属するアセットで、使用する必要があるものを指定します。 既定では、パッケージのすべてのアセットが含まれます。 |
| `ExcludeAssets`| `<PackageReference>` によって指定されているパッケージに属するアセットで、使用してはならないものを指定します。 |
| `PrivateAssets` | `<PackageReference>` で指定されているパッケージに属するアセットで、使用する必要はあるが、次のプロジェクトに渡してはならないものを指定します。 この属性が存在しない場合、`Analyzers`、`Build`、`ContentFiles` の各アセットは既定でプライベートになります。 |

これらの属性には以下の項目を 1 つ以上含めることができ、複数ある場合はセミコロン `;` で区切ります。

- `Compile` - コンパイルで使用できる *lib* フォルダーの内容です。
- `Runtime` - 配布する *runtime* フォルダーの内容です。
- `ContentFiles` - 使用する *contentfiles* フォルダーの内容です。
- `Build` - 使用する *build* フォルダーのプロパティ/ターゲットです。
- `Native` - ランタイムの *output* フォルダーにコピーするネイティブ アセットの内容です。
- `Analyzers` - アナライザーが使用されます。

代わりに、次の値を属性に含めることもできます。

- `None` - いずれのアセットも使用されません。
- `All` - すべてのアセットが使用されます。

### <a name="projectreference"></a>ProjectReference

`ProjectReference` 項目では、別のプロジェクトへの参照を定義します。 参照されたプロジェクトは NuGet パッケージ依存関係として追加されます。つまり、`PackageReference` と同じように処理されます。

`Include` 属性は、プロジェクトのパスを指定します。 また、メタデータ `IncludeAssets`、`ExcludeAssets`、`PrivateAssets` をプロジェクト参照に追加できます。

次の例のプロジェクト ファイル スニペットでは、`Project2` という名前のプロジェクトが参照されます。

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a>関連項目

`Reference` 項目では、アセンブリ ファイルへの参照を定義します。

`Include` 属性によってファイルの名前が指定され、`HintPath` メタデータによってアセンブリへのパスが指定されます。

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-related-properties"></a>復元関連のプロパティ

参照されたパッケージを復元すると、その直接的な依存関係と間接的な依存関係がすべてインストールされます。 `RestorePackagesPath` や `RestoreIgnoreFailedSources` など、プロパティを指定することでパッケージ復元をカスタマイズできます。 以上のプロパティとその他のプロパティの詳細については、「[restore ターゲット](/nuget/reference/msbuild-targets#restore-target)」を参照してください。

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-properties"></a>実行のプロパティ

次のプロパティは、[`dotnet run`](../tools/dotnet-run.md) コマンドを使用してアプリを起動するために使用されます。

- [RunArguments](#runarguments)
- [RunWorkingDirectory](#runworkingdirectory)

### <a name="runarguments"></a>RunArguments

`RunArguments` プロパティを使用すると、実行時にアプリに渡される引数が定義されます。

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> [`dotnet run` に ](../tools/dotnet-run.md#options)`--` オプションを使用して、アプリに渡す追加の引数を指定できます。

### <a name="runworkingdirectory"></a>RunWorkingDirectory

`RunWorkingDirectory` プロパティを使用すると、開始するアプリケーション プロセスの作業ディレクトリが定義されます。 絶対パスまたはプロジェクト ディレクトリに対する相対パスを指定できます。 ディレクトリを指定しない場合、作業ディレクトリとして `OutDir` が使用されます。

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-properties"></a>ホストのプロパティ

- [EnableComHosting](#enablecomhosting)
- [EnableDynamicLoading](#enabledynamicloading)

### <a name="enablecomhosting"></a>EnableComHosting

`EnableComHosting` プロパティは、アセンブリで COM サーバーが提供されることを示します。 `EnableComHosting` を `true` に設定することは、[EnableDynamicLoading](#enabledynamicloading) が `true` であることも意味します。

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

詳細については、[COM への .NET コンポーネントの公開](../native-interop/expose-components-to-com.md)に関するページを参照してください。

### <a name="enabledynamicloading"></a>EnableDynamicLoading

`EnableDynamicLoading` プロパティは、アセンブリが動的に読み込まれたコンポーネントであることを示します。 コンポーネントには、[COM ライブラリ](/windows/win32/com/the-component-object-model)、または[ネイティブ ホストから使用](../tutorials/netcore-hosting.md)できる非 COM ライブラリを指定できます。 このプロパティを `true` に設定すると、次のような効果があります。

- " *.runtimeconfig.json*" ファイルが生成される。
- [ロール フォワード](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)が `LatestMinor` に設定される。
- NuGet 参照がローカルにコピーされる。

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a>関連項目

- [MSBuild スキーマ リファレンス](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [MSBuild の共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)
- [NuGet pack の MSBuild プロパティ](/nuget/reference/msbuild-targets#pack-target)
- [NuGet restore の MSBuild プロパティ](/nuget/reference/msbuild-targets#restore-properties)
- [ビルドのカスタマイズ](/visualstudio/msbuild/customize-your-build)
