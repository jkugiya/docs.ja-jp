---
title: dotnet build コマンド
description: dotnet build コマンドは、プロジェクトとそのすべての依存関係をビルドします。
ms.date: 02/14/2020
ms.openlocfilehash: cc8c6ed30dbf8ff0602fb19e5001f618a8380f16
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189957"
---
# <a name="dotnet-build"></a><span data-ttu-id="f1ce5-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="f1ce5-103">dotnet build</span></span>

<span data-ttu-id="f1ce5-104">**この記事の対象:** ✔️ .NET Core 2.x SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="f1ce5-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f1ce5-105">名前</span><span class="sxs-lookup"><span data-stu-id="f1ce5-105">Name</span></span>

<span data-ttu-id="f1ce5-106">`dotnet build` - プロジェクトとそのすべての依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f1ce5-107">構文</span><span class="sxs-lookup"><span data-stu-id="f1ce5-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--source <SOURCE>]
    [-v|--verbosity <LEVEL>] [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a><span data-ttu-id="f1ce5-108">説明</span><span class="sxs-lookup"><span data-stu-id="f1ce5-108">Description</span></span>

<span data-ttu-id="f1ce5-109">`dotnet build` コマンドは、プロジェクトとその依存関係をバイナリ セットにビルドします。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="f1ce5-110">バイナリには、拡張子が *.dll* である中間言語 (IL) ファイルのプロジェクトのコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="f1ce5-111">プロジェクトの種類と設定に応じて、次などのファイルを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="f1ce5-112">プロジェクトの種類が .NET Core 3.0 以降を対象とする実行可能ファイルである場合、アプリケーションの実行に使用できる実行可能ファイル。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="f1ce5-113">拡張子が *.pdb* であるデバッグに使用されるシンボル ファイル。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="f1ce5-114">アプリケーションまたはライブラリの依存関係が列挙されている *.deps.json* ファイル。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="f1ce5-115">アプリケーションの共有ランタイムとそのバージョンを指定する、 *.runtimeconfig.json* ファイル。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="f1ce5-116">(プロジェクト参照または NuGet パッケージの参照を介して) プロジェクトが依存する他のライブラリ。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="f1ce5-117">.NET Core 3.0 より前のバージョンを対象とする実行可能なプロジェクトでは、NuGet からのライブラリの依存関係は、通常出力フォルダーにコピーされません。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="f1ce5-118">これらは、実行時に NuGet グローバル パッケージ フォルダーで解決されます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="f1ce5-119">この点を考慮すると、`dotnet build` の生成物は別のコンピューターに転送して実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="f1ce5-120">展開できるアプリケーションのバージョンを作成するには、(たとえば、[dotnet publish](dotnet-publish.md) コマンドを使用して) アプリケーションを発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="f1ce5-121">詳細については、[.NET アプリケーションの展開](../deploying/index.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-121">For more information, see [.NET Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="f1ce5-122">.NET Core 3.0 以降を対象とする実行可能なプロジェクトでは、ライブラリの依存関係は出力フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="f1ce5-123">つまり、(Web プロジェクトなどが持つ) 発行専用のロジックが他にない場合、ビルドの出力は展開できるはずです。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="f1ce5-124">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="f1ce5-124">Implicit restore</span></span>

<span data-ttu-id="f1ce5-125">ビルドには *project.assets.json* ファイルが必要です。このファイルには、アプリケーションの依存関係が一覧表示されています。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-125">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="f1ce5-126">このファイルは、[`dotnet restore`](dotnet-restore.md) を実行すると作成されます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-126">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="f1ce5-127">アセット ファイルが配置されていないと、ツールは参照アセンブリを解決できないため、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-127">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a><span data-ttu-id="f1ce5-128">実行可能ファイルまたはライブラリ出力</span><span class="sxs-lookup"><span data-stu-id="f1ce5-128">Executable or library output</span></span>

<span data-ttu-id="f1ce5-129">プロジェクトを実行できるかどうかは、プロジェクト ファイルの `<OutputType>` プロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="f1ce5-130">次の例は、実行可能なコードを生成するプロジェクトを示しています。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="f1ce5-131">ライブラリを生成するには、`<OutputType>` プロパティを省略するか、その値を `Library` に変更します。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-131">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="f1ce5-132">ライブラリの IL DLL にはエントリ ポイントが含まれず、実行できません。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-132">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="f1ce5-133">MSBuild</span><span class="sxs-lookup"><span data-stu-id="f1ce5-133">MSBuild</span></span>

<span data-ttu-id="f1ce5-134">`dotnet build` では MSBuild を使用してプロジェクトをビルドするため、並列ビルドとインクリメンタル ビルドの両方がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-134">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="f1ce5-135">詳しくは、「[インクリメンタル ビルド](/visualstudio/msbuild/incremental-builds)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-135">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="f1ce5-136">このオプションに加え、`dotnet build` コマンドは、プロパティを設定する `-p` やロガーを定義する `-l` などの MSBuild オプションも受け入れます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-136">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="f1ce5-137">これらのオプションの詳細については、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-137">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="f1ce5-138">また、[dotnet msbuild](dotnet-msbuild.md) コマンドを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-138">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="f1ce5-139">`dotnet build` を実行することは、`dotnet msbuild -restore` を実行することと同じです。ただし、出力の既定の詳細度は異なります。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-139">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="f1ce5-140">引数</span><span class="sxs-lookup"><span data-stu-id="f1ce5-140">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="f1ce5-141">ビルドするプロジェクトまたはソリューションのファイル。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-141">The project or solution file to build.</span></span> <span data-ttu-id="f1ce5-142">プロジェクトまたはソリューションのファイルを指定しない場合、MSBuild は、現在の作業ディレクトリから *proj* または *sln* のどちらかで終わるファイル拡張子を持つファイルを検索して、そのファイルを使います。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-142">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="f1ce5-143">オプション</span><span class="sxs-lookup"><span data-stu-id="f1ce5-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="f1ce5-144">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-144">Defines the build configuration.</span></span> <span data-ttu-id="f1ce5-145">ほとんどのプロジェクトの既定値は `Debug` ですが、プロジェクトでビルド構成設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1ce5-146">特定の[フレームワーク](../../standard/frameworks.md)用にコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-146">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="f1ce5-147">フレームワークは、[プロジェクト ファイル](../project-sdk/overview.md)で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-147">The framework must be defined in the [project file](../project-sdk/overview.md).</span></span>

- **`--force`**

  <span data-ttu-id="f1ce5-148">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="f1ce5-149">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f1ce5-150">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="f1ce5-151">コマンドを停止して、ユーザーの入力または操作のために待機させることができます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="f1ce5-152">たとえば、認証を完了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-152">For example, to complete authentication.</span></span> <span data-ttu-id="f1ce5-153">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="f1ce5-154">プロジェクト間 (P2P) 参照を無視し、指定されたルート プロジェクトのみをビルドします。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-154">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="f1ce5-155">インクリメンタル ビルドとして安全でないビルドをマークします。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-155">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="f1ce5-156">このフラグにより、インクリメンタル コンパイルは無効になり、プロジェクトの依存関係グラフのクリーン再ビルドが強制的に行われます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-156">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1ce5-157">ビルド時に暗黙的な復元は実行されません。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-157">Doesn't execute an implicit restore during build.</span></span>

- **`--nologo`**

  <span data-ttu-id="f1ce5-158">著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-158">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="f1ce5-159">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-159">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f1ce5-160">ビルド済みバイナリを配置するディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-160">Directory in which to place the built binaries.</span></span> <span data-ttu-id="f1ce5-161">指定しない場合、既定のパスは `./bin/<configuration>/<framework>/` になります。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-161">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="f1ce5-162">(`TargetFrameworks` プロパティを使用した) ターゲット フレームワークが複数あるプロジェクトの場合は、このオプションを指定するときに `--framework` も定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-162">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f1ce5-163">ターゲットのランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-163">Specifies the target runtime.</span></span> <span data-ttu-id="f1ce5-164">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-164">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`--source <SOURCE>`**

  <span data-ttu-id="f1ce5-165">復元操作時に使用する NuGet パッケージ ソースの URI。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-165">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f1ce5-166">MSBuild の詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-166">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="f1ce5-167">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-167">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f1ce5-168">既定値は、`minimal` です。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-168">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="f1ce5-169">プロジェクトをビルドするときに使用する `$(VersionSuffix)` プロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-169">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="f1ce5-170">これは、`$(Version)` プロパティが設定されていない場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-170">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="f1ce5-171">次に、`$(Version)` には、ダッシュで区切り `$(VersionSuffix)` と組み合わせた `$(VersionPrefix)` が設定されます。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-171">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="f1ce5-172">使用例</span><span class="sxs-lookup"><span data-stu-id="f1ce5-172">Examples</span></span>

- <span data-ttu-id="f1ce5-173">プロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-173">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="f1ce5-174">リリース構成を使用して、プロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-174">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="f1ce5-175">特定のランタイム (この例では、Ubuntu 18.04) 用にプロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-175">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="f1ce5-176">プロジェクトをビルドし、復元操作中に指定した NuGet パッケージ ソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-176">Build the project and use the specified NuGet package source during the restore operation:</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="f1ce5-177">`-p` [MSBuild オプション](#msbuild)を使用してプロジェクトをビルドし、バージョン 1.2.3.4 をビルド パラメーターとして設定します。</span><span class="sxs-lookup"><span data-stu-id="f1ce5-177">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
