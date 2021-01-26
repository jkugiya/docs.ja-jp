---
title: ランタイムの構成オプション
description: ランタイム構成設定を使用して .NET Core アプリケーションを構成する方法について説明します。
ms.date: 01/21/2020
ms.openlocfilehash: 5e9f292476cf953c3e63bb8e89268f7cc06b3bfc
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757851"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="737fc-103">.NET Core ランタイム構成設定</span><span class="sxs-lookup"><span data-stu-id="737fc-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="737fc-104">.NET Core では、実行時に .NET Core アプリケーションの動作を構成するために、構成ファイルと環境変数の使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="737fc-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="737fc-105">ランタイムの構成は、次の場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="737fc-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="737fc-106">アプリケーションのソースコードを所有または制御していないため、プログラムで構成することができない。</span><span class="sxs-lookup"><span data-stu-id="737fc-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="737fc-107">アプリケーションの複数のインスタンスが 1 つのシステムで同時に実行され、最適なパフォーマンスを実現するために各インスタンスを構成する必要がある。</span><span class="sxs-lookup"><span data-stu-id="737fc-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="737fc-108">このドキュメントは現在作成中です。</span><span class="sxs-lookup"><span data-stu-id="737fc-108">This documentation is a work in progress.</span></span> <span data-ttu-id="737fc-109">ここに記載されている情報が不完全であるか、不正確であることがわかった場合は、[イシューを作成](https://github.com/dotnet/docs/issues)してお知らせになるか、[pull request を送信](https://github.com/dotnet/docs/pulls)してイシューに対処してください。</span><span class="sxs-lookup"><span data-stu-id="737fc-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="737fc-110">dotnet/docs リポジトリに対する pull request の送信については、[共同作成者のガイド](/contribute/dotnet/dotnet-contribute)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="737fc-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](/contribute/dotnet/dotnet-contribute).</span></span>

<span data-ttu-id="737fc-111">.NET Core には、実行時にアプリケーションを構成する次のメカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="737fc-111">.NET Core provides the following mechanisms for configuring application behavior at run time:</span></span>

- <span data-ttu-id="737fc-112">[runtimeconfig.json ファイル](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="737fc-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="737fc-113">MSBuild プロパティ</span><span class="sxs-lookup"><span data-stu-id="737fc-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="737fc-114">環境変数</span><span class="sxs-lookup"><span data-stu-id="737fc-114">Environment variables</span></span>](#environment-variables)

> [!TIP]
> <span data-ttu-id="737fc-115">環境変数を使用して実行時オプションを構成すると、すべての .NET Core アプリに設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="737fc-115">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="737fc-116">*runtimeconfig.json* またはプロジェクト ファイルで実行時オプションを構成すると、そのアプリケーションにのみ設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="737fc-116">Configuring a run-time option in the *runtimeconfig.json* or project file applies the setting to that application only.</span></span>

<span data-ttu-id="737fc-117">一部の構成値は、<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> メソッドを呼び出すことによって、プログラムで設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="737fc-117">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="737fc-118">ドキュメントのこのセクションの記事は、[デバッグ](debugging-profiling.md)や[ガベージ コレクション](garbage-collector.md)などのカテゴリに分類されています。</span><span class="sxs-lookup"><span data-stu-id="737fc-118">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="737fc-119">必要に応じて、*runtimeconfig.json* ファイル、MSBuild のプロパティ、環境変数用の構成オプションを示しています。また相互参照用に .NET Framework プロジェクトの *app.config* ファイルも示しています。</span><span class="sxs-lookup"><span data-stu-id="737fc-119">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="737fc-120">runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="737fc-120">runtimeconfig.json</span></span>

<span data-ttu-id="737fc-121">プロジェクトが [ビルドされた](../tools/dotnet-build.md)場合、出力ディレクトリに *[appname].runtimeconfig.json* ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="737fc-121">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="737fc-122">*runtimeconfig.template.json* ファイルがプロジェクト ファイルと同じフォルダーにある場合、それに設定されているすべてのオプションは *[appname].runtimeconfig.json* ファイルに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="737fc-122">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are inserted into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="737fc-123">そのアプリをご自分でビルドする場合は、構成オプションはすべて *runtimeconfig.template.json* ファイルに追加してください。</span><span class="sxs-lookup"><span data-stu-id="737fc-123">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="737fc-124">そのアプリを実行しているだけの場合は、 *[appname].runtimeconfig.json* ファイルに直接挿入します。</span><span class="sxs-lookup"><span data-stu-id="737fc-124">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="737fc-125">この *[appname].runtimeconfig.json* ファイルは、以降のビルドで上書きされます。</span><span class="sxs-lookup"><span data-stu-id="737fc-125">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="737fc-126">*runtimeconfig.json* ファイルの **configProperties** セクションに、ランタイム構成オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="737fc-126">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="737fc-127">このセクションには次の形式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="737fc-127">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="737fc-128">[appname].runtimeconfig.json ファイルの例</span><span class="sxs-lookup"><span data-stu-id="737fc-128">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="737fc-129">このオプションを出力 JSON ファイルに入力する場合、`runtimeOptions` プロパティの下に入れます。</span><span class="sxs-lookup"><span data-stu-id="737fc-129">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="737fc-130">runtimeconfig.template.json ファイルの例</span><span class="sxs-lookup"><span data-stu-id="737fc-130">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="737fc-131">このオプションをテンプレート JSON ファイルに入力する場合、`runtimeOptions` プロパティを省略します。</span><span class="sxs-lookup"><span data-stu-id="737fc-131">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="737fc-132">MSBuild プロパティ</span><span class="sxs-lookup"><span data-stu-id="737fc-132">MSBuild properties</span></span>

<span data-ttu-id="737fc-133">一部の実行構成オプションは、 *.csproj* の MSBuild のプロパティ、または SDK 形式の .NET Core プロジェクトの *.vbproj* ファイルを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="737fc-133">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="737fc-134">MSBuild のプロパティは、*runtimeconfig.template.json* ファイルで設定されているオプションよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="737fc-134">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span>

<span data-ttu-id="737fc-135">次に、ランタイム動作を構成する MSBuild のプロパティがある SDK 形式のプロジェクト ファイルの例を示します。</span><span class="sxs-lookup"><span data-stu-id="737fc-135">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="737fc-136">実行時の動作を構成する MSBuild プロパティについては、[ガベージ コレクション](garbage-collector.md)に関するページなど、各領域の個々の記事に記載されています。</span><span class="sxs-lookup"><span data-stu-id="737fc-136">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="737fc-137">これらは、SDK スタイルのプロジェクトの MSBuild プロパティ リファレンスの「[実行時構成](../project-sdk/msbuild-props.md#run-time-configuration-properties)」セクションにも記載されています。</span><span class="sxs-lookup"><span data-stu-id="737fc-137">They are also listed in the [Run-time configuration](../project-sdk/msbuild-props.md#run-time-configuration-properties) section of the MSBuild properties reference for SDK-style projects.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="737fc-138">環境変数</span><span class="sxs-lookup"><span data-stu-id="737fc-138">Environment variables</span></span>

<span data-ttu-id="737fc-139">環境変数を使用すると、ランタイムの構成情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="737fc-139">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="737fc-140">環境変数を使用して実行時オプションを構成すると、すべての .NET Core アプリに設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="737fc-140">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="737fc-141">環境変数として指定された構成ノブには、一般に **COMPlus_** のプレフィックスが付いています。</span><span class="sxs-lookup"><span data-stu-id="737fc-141">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="737fc-142">環境変数は、Windows のコントロール パネル、コマンド ライン、または Windows と Unix ベースのシステムの両方で <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> メソッドを呼び出すことによって、プログラムで定義できます。</span><span class="sxs-lookup"><span data-stu-id="737fc-142">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="737fc-143">次の例は、コマンド ラインで環境変数を設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="737fc-143">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
