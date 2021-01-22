---
title: dotnet pack コマンド
description: dotnet pack コマンドを実行すると、.NET プロジェクトの NuGet パッケージが作成されます。
ms.date: 04/28/2020
ms.openlocfilehash: a9a634c358f5de4f28c3de06edc9a2b4d2eb8d57
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190079"
---
# <a name="dotnet-pack"></a><span data-ttu-id="40cc8-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="40cc8-103">dotnet pack</span></span>

<span data-ttu-id="40cc8-104">**この記事の対象:** ✔️ .NET Core 2.x SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="40cc8-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="40cc8-105">名前</span><span class="sxs-lookup"><span data-stu-id="40cc8-105">Name</span></span>

<span data-ttu-id="40cc8-106">`dotnet pack` - NuGet パッケージにコードをパックします。</span><span class="sxs-lookup"><span data-stu-id="40cc8-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="40cc8-107">構文</span><span class="sxs-lookup"><span data-stu-id="40cc8-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a><span data-ttu-id="40cc8-108">説明</span><span class="sxs-lookup"><span data-stu-id="40cc8-108">Description</span></span>

<span data-ttu-id="40cc8-109">`dotnet pack` コマンドはプロジェクトをビルドし、NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="40cc8-110">このコマンドの結果が NuGet パッケージ (つまり、 *.nupkg* ファイル) です。</span><span class="sxs-lookup"><span data-stu-id="40cc8-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="40cc8-111">デバッグ シンボルを含むパッケージを生成する場合、使用可能なオプションが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="40cc8-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="40cc8-112">`--include-symbols` -シンボル パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="40cc8-113">`--include-source` -ソース ファイルが含まれた `src` フォルダーを含むシンボル パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="40cc8-114">パックされるプロジェクトの NuGet 依存関係が *.nuspec* ファイルに追加されるため、パッケージのインストール時に適切に解決されます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="40cc8-115">プロジェクト間参照はプロジェクト内にはパッケージ化されません。</span><span class="sxs-lookup"><span data-stu-id="40cc8-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="40cc8-116">現時点では、プロジェクト間の依存関係がある場合は、プロジェクトごとにパッケージが必要になります。</span><span class="sxs-lookup"><span data-stu-id="40cc8-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="40cc8-117">既定では、`dotnet pack` は最初にプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="40cc8-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="40cc8-118">この動作を避けたい場合は、`--no-build` オプションを渡します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="40cc8-119">このオプションは、コードが既にビルドされていることがわかっている場合の継続的インテグレーション (CI) ビルド シナリオで役立つことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="40cc8-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

> [!NOTE]
> <span data-ttu-id="40cc8-120">場合によっては、暗黙的なビルドは実行できません。</span><span class="sxs-lookup"><span data-stu-id="40cc8-120">In some cases, the implicit build cannot be performed.</span></span> <span data-ttu-id="40cc8-121">これは、ビルドとパック ターゲット間の循環依存を回避するため `GeneratePackageOnBuild` が設定されている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-121">This can occur when `GeneratePackageOnBuild` is set, to avoid a cyclic dependency between build and pack targets.</span></span> <span data-ttu-id="40cc8-122">ロックされているファイルがある場合や、その他の問題がある場合にも、ビルドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-122">The build can also fail if there is a locked file or other issue.</span></span>

<span data-ttu-id="40cc8-123">パッキング プロセスのために `dotnet pack` コマンドに MSBuild のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-123">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="40cc8-124">詳細については、[NuGet の pack ターゲットのプロパティ](/nuget/reference/msbuild-targets#pack-target)に関するページと、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40cc8-124">For more information, see [NuGet pack target properties](/nuget/reference/msbuild-targets#pack-target) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="40cc8-125">「[使用例](#examples)」のセクションでは、MSBuild の `-p` スイッチを使用する方法を、2 つの異なるシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-125">The [Examples](#examples) section shows how to use the MSBuild `-p` switch for a couple of different scenarios.</span></span>

<span data-ttu-id="40cc8-126">Web プロジェクトは既定でパッケージ化可能ではありません。</span><span class="sxs-lookup"><span data-stu-id="40cc8-126">Web projects aren't packable by default.</span></span> <span data-ttu-id="40cc8-127">既定の動作をオーバーライドするには、 *.csproj* ファイルに次のプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-127">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

### <a name="implicit-restore"></a><span data-ttu-id="40cc8-128">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="40cc8-128">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="40cc8-129">引数</span><span class="sxs-lookup"><span data-stu-id="40cc8-129">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="40cc8-130">パックするプロジェクトまたはソリューション。</span><span class="sxs-lookup"><span data-stu-id="40cc8-130">The project or solution to pack.</span></span> <span data-ttu-id="40cc8-131">csproj、vbproj、または fsproj ファイル、ソリューション ファイル、またはディレクトリのいずれかへのパスです。</span><span class="sxs-lookup"><span data-stu-id="40cc8-131">It's either a path to a csproj, vbproj, or fsproj file, or to a solution file or directory.</span></span> <span data-ttu-id="40cc8-132">指定されていない場合、コマンドによりプロジェクトまたはソリューション ファイルが現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-132">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="40cc8-133">オプション</span><span class="sxs-lookup"><span data-stu-id="40cc8-133">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="40cc8-134">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-134">Defines the build configuration.</span></span> <span data-ttu-id="40cc8-135">ほとんどのプロジェクトの既定値は `Debug` ですが、プロジェクトでビルド構成設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-135">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="40cc8-136">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-136">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="40cc8-137">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="40cc8-137">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="40cc8-138">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-138">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="40cc8-139">通常の NuGet パッケージに加えて、デバッグ シンボル NuGet パッケージが出力ディレクトリ内に含まれます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-139">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="40cc8-140">ソース ファイルは、シンボル パッケージ内の `src` フォルダーに含まれます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-140">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="40cc8-141">通常の NuGet パッケージに加えて、デバッグ シンボル NuGet パッケージが出力ディレクトリ内に含まれます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-141">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="40cc8-142">コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。</span><span class="sxs-lookup"><span data-stu-id="40cc8-142">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="40cc8-143">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="40cc8-144">パッキングの前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="40cc8-144">Doesn't build the project before packing.</span></span> <span data-ttu-id="40cc8-145">また、`--no-restore` フラグが暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-145">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="40cc8-146">プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-146">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="40cc8-147">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="40cc8-147">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="40cc8-148">著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="40cc8-148">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="40cc8-149">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="40cc8-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="40cc8-150">指定したディレクトリにビルド済みパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-150">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="40cc8-151">パッケージを復元するターゲット ランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="40cc8-152">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="40cc8-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="40cc8-153">パッケージに処理可能フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="40cc8-154">詳細については、[ .NET Framework 4.5.1 での .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムのサポートに関する .NET ブログ](https://aka.ms/nupkgservicing)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40cc8-154">For more information, see [.NET Blog: .NET Framework 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="40cc8-155">プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="40cc8-156">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="40cc8-157">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="40cc8-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="40cc8-158">使用例</span><span class="sxs-lookup"><span data-stu-id="40cc8-158">Examples</span></span>

- <span data-ttu-id="40cc8-159">現在のディレクトリのプロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="40cc8-159">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="40cc8-160">`app1` プロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="40cc8-160">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="40cc8-161">プロジェクトを現在のディレクトリにパックし、`nupkgs` フォルダーに生成されたパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="40cc8-162">現在のディレクトリのプロジェクトを `nupkgs` フォルダーにパックし、ビルド ステップをスキップします。</span><span class="sxs-lookup"><span data-stu-id="40cc8-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="40cc8-163">*.csproj* ファイルで `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` として構成されているプロジェクトのバージョン サフィックスで、現在のプロジェクトをパックし、結果のパッケージ バージョンを指定されたサフィックスで更新します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="40cc8-164">`PackageVersion` MSBuild プロパティで `2.1.0` にパッケージ バージョンを設定します。</span><span class="sxs-lookup"><span data-stu-id="40cc8-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="40cc8-165">プロジェクトを特定の[ターゲット フレームワーク](../../standard/frameworks.md)用にパックします。</span><span class="sxs-lookup"><span data-stu-id="40cc8-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="40cc8-166">プロジェクトをパックして、復元操作用の特定のランタイム (Windows 10) を使用する:</span><span class="sxs-lookup"><span data-stu-id="40cc8-166">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="40cc8-167">*.nuspec ファイル* を使用してプロジェクトをパックします。</span><span class="sxs-lookup"><span data-stu-id="40cc8-167">Pack the project using a *.nuspec* file:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```

  <span data-ttu-id="40cc8-168">`NuspecFile`、`NuspecBasePath`、`NuspecProperties` の詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40cc8-168">For information about how to use `NuspecFile`, `NuspecBasePath`, and `NuspecProperties`, see the following resources:</span></span>

  - [<span data-ttu-id="40cc8-169">.nuspec を使用したパック</span><span class="sxs-lookup"><span data-stu-id="40cc8-169">Packing using a .nuspec</span></span>](/nuget/reference/msbuild-targets#packing-using-a-nuspec)
  - [<span data-ttu-id="40cc8-170">カスタマイズされたパッケージを作成するための高度な拡張ポイント</span><span class="sxs-lookup"><span data-stu-id="40cc8-170">Advanced extension points to create customized package</span></span>](/nuget/reference/msbuild-targets#advanced-extension-points-to-create-customized-package)
  - [<span data-ttu-id="40cc8-171">グローバル プロパティ</span><span class="sxs-lookup"><span data-stu-id="40cc8-171">Global properties</span></span>](/visualstudio/msbuild/msbuild-properties#global-properties)
