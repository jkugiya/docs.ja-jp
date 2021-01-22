---
title: dotnet list package コマンド
description: "\"dotnet list package\" コマンドでは、プロジェクトまたはソリューションのパッケージ参照を列挙する便利なオプションが提供されています。"
ms.date: 11/11/2020
ms.openlocfilehash: 684b73dec553a424252e1368c265847622fb7850
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189897"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="a3907-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="a3907-103">dotnet list package</span></span>

<span data-ttu-id="a3907-104">**この記事の対象:** ✔️ .NET Core 2.2 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="a3907-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a3907-105">名前</span><span class="sxs-lookup"><span data-stu-id="a3907-105">Name</span></span>

<span data-ttu-id="a3907-106">`dotnet list package` - プロジェクトまたはソリューションのパッケージ参照を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a3907-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a3907-107">構文</span><span class="sxs-lookup"><span data-stu-id="a3907-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--deprecated]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>] [-v|--verbosity <LEVEL>]

dotnet list package -h|--help
```

## <a name="description"></a><span data-ttu-id="a3907-108">説明</span><span class="sxs-lookup"><span data-stu-id="a3907-108">Description</span></span>

<span data-ttu-id="a3907-109">`dotnet list package` コマンドでは、特定のプロジェクトまたはソリューションのすべての NuGet パッケージ参照を列挙する便利なオプションが提供されています。</span><span class="sxs-lookup"><span data-stu-id="a3907-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="a3907-110">このコマンドで処理するために必要なアセットを用意するには、最初にプロジェクトをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3907-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="a3907-111">次の例では、[SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) プロジェクトに対する `dotnet list package` コマンドの出力を示します。</span><span class="sxs-lookup"><span data-stu-id="a3907-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="a3907-112">**[Requested]** 列は、プロジェクト ファイルで指定されているパッケージのバージョンを示し、範囲で示されることもあります。</span><span class="sxs-lookup"><span data-stu-id="a3907-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="a3907-113">**[Resolved]** 列には、プロジェクトで現在使用されているバージョンが一覧表示され、常に単一の値です。</span><span class="sxs-lookup"><span data-stu-id="a3907-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="a3907-114">名前の隣に `(A)` と表示されているパッケージは、プロジェクトの設定から推論される暗黙的なパッケージ参照を表します (`Sdk` 型、`<TargetFramework>` プロパティ、`<TargetFrameworks>` プロパティなど)。</span><span class="sxs-lookup"><span data-stu-id="a3907-114">The packages displaying an `(A)` right next to their names represent implicit package references that are inferred from your project settings (`Sdk` type, or `<TargetFramework>` or `<TargetFrameworks>` property).</span></span>

<span data-ttu-id="a3907-115">プロジェクトで使用されているパッケージのさらに新しいバージョンを利用可能かどうかを調べるには、`--outdated` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3907-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="a3907-116">既定では、解決済みのバージョンがプレリリース バージョンでもある場合を除き、`--outdated` では最新の安定したパッケージが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3907-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="a3907-117">新しいバージョンを一覧表示するときにプレリリース版を含めるには、`--include-prerelease` オプションも指定します。</span><span class="sxs-lookup"><span data-stu-id="a3907-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="a3907-118">次の例では、前の例と同じプロジェクトに対する `dotnet list package --outdated --include-prerelease` コマンドの出力を示します。</span><span class="sxs-lookup"><span data-stu-id="a3907-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="a3907-119">プロジェクトに推移的依存関係があるかどうかを確認する必要がある場合は、`--include-transitive` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3907-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="a3907-120">推移的依存関係は、プロジェクトに追加したパッケージがさらに別のパッケージに依存している場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a3907-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="a3907-121">次の例では、[HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) プロジェクトに対して `dotnet list package --include-transitive` コマンドを実行した出力を示します、最上位のパッケージと、それらが依存しているパッケージが表示されています。</span><span class="sxs-lookup"><span data-stu-id="a3907-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="a3907-122">引数</span><span class="sxs-lookup"><span data-stu-id="a3907-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="a3907-123">対象のプロジェクトまたはソリューションのファイル。</span><span class="sxs-lookup"><span data-stu-id="a3907-123">The project or solution file to operate on.</span></span> <span data-ttu-id="a3907-124">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="a3907-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="a3907-125">複数のソリューションまたはプロジェクトが見つかった場合は、エラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="a3907-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="a3907-126">オプション</span><span class="sxs-lookup"><span data-stu-id="a3907-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="a3907-127">より新しいパッケージを検索するときに使用する NuGet ソース。</span><span class="sxs-lookup"><span data-stu-id="a3907-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="a3907-128">`--outdated` オプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="a3907-128">Requires the `--outdated` option.</span></span>

- **`--deprecated`**

  <span data-ttu-id="a3907-129">非推奨となったパッケージを表示します。</span><span class="sxs-lookup"><span data-stu-id="a3907-129">Displays packages that have been deprecated.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="a3907-130">指定した[ターゲット フレームワーク](../../standard/frameworks.md)に該当するパッケージのみを表示します。</span><span class="sxs-lookup"><span data-stu-id="a3907-130">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a3907-131">複数のフレームワークを指定するには、オプションを複数回繰り返します。</span><span class="sxs-lookup"><span data-stu-id="a3907-131">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="a3907-132">たとえば、`--framework netcoreapp2.2 --framework netstandard2.0` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="a3907-132">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a3907-133">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="a3907-133">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="a3907-134">新しいパッケージを検索するときに、メジャー バージョン番号が一致するパッケージのみを考慮します。</span><span class="sxs-lookup"><span data-stu-id="a3907-134">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="a3907-135">`--outdated` オプション、または `--deprecated` オプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="a3907-135">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="a3907-136">新しいパッケージを検索するときに、メジャー バージョン番号とマイナー バージョン番号が一致するパッケージのみを考慮します。</span><span class="sxs-lookup"><span data-stu-id="a3907-136">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="a3907-137">`--outdated` オプション、または `--deprecated` オプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="a3907-137">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="a3907-138">新しいパッケージを検索するときに、プレリリース バージョンのパッケージを考慮します。</span><span class="sxs-lookup"><span data-stu-id="a3907-138">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="a3907-139">`--outdated` オプション、または `--deprecated` オプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="a3907-139">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="a3907-140">最上位のパッケージに加えて、推移的なパッケージを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a3907-140">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="a3907-141">このオプションを指定すると、最上位のパッケージが依存しているパッケージの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3907-141">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="a3907-142">コマンドを停止して、ユーザーの入力または操作のために待機させることができます。</span><span class="sxs-lookup"><span data-stu-id="a3907-142">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="a3907-143">たとえば、認証を完了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3907-143">For example, to complete authentication.</span></span> <span data-ttu-id="a3907-144">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3907-144">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="a3907-145">より新しいバージョンを使用できるパッケージを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a3907-145">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="a3907-146">より新しいパッケージを検索するときに使用する NuGet ソース。</span><span class="sxs-lookup"><span data-stu-id="a3907-146">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="a3907-147">`--outdated` オプション、または `--deprecated` オプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="a3907-147">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a3907-148">MSBuild の詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="a3907-148">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="a3907-149">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="a3907-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a3907-150">既定値は、`minimal` です。</span><span class="sxs-lookup"><span data-stu-id="a3907-150">The default is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="a3907-151">使用例</span><span class="sxs-lookup"><span data-stu-id="a3907-151">Examples</span></span>

- <span data-ttu-id="a3907-152">特定のプロジェクトのパッケージ参照を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a3907-152">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="a3907-153">プレリリース バージョンを含め、さらに新しいバージョンを使用できるパッケージ参照を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a3907-153">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="a3907-154">特定のターゲット フレームワークのパッケージ参照を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a3907-154">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
