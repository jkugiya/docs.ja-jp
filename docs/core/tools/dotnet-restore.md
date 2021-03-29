---
title: dotnet restore コマンド
description: dotnet restore コマンドを使用して、依存関係とプロジェクト固有のツールを復元する方法について説明します。
ms.date: 02/27/2020
ms.openlocfilehash: 14bcf65bb78e6d1d96604c8a10a3ba94fab80db8
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874837"
---
# <a name="dotnet-restore"></a><span data-ttu-id="fd3b1-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="fd3b1-103">dotnet restore</span></span>

<span data-ttu-id="fd3b1-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="fd3b1-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fd3b1-105">名前</span><span class="sxs-lookup"><span data-stu-id="fd3b1-105">Name</span></span>

<span data-ttu-id="fd3b1-106">`dotnet restore` - プロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fd3b1-107">構文</span><span class="sxs-lookup"><span data-stu-id="fd3b1-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lock-file] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="fd3b1-108">説明</span><span class="sxs-lookup"><span data-stu-id="fd3b1-108">Description</span></span>

<span data-ttu-id="fd3b1-109">`dotnet restore` コマンドでは NuGet を使用して、依存関係と、プロジェクト ファイルに指定されているプロジェクト固有のツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span>  <span data-ttu-id="fd3b1-110">ほとんどの場合、次のコマンドを実行すると、必要に応じて NuGet の復元が暗黙的に実行されるため、`dotnet restore` コマンドを明示的に使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-110">In most cases, you don't need to explicitly use the `dotnet restore` command, since a NuGet restore is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="fd3b1-111">場合によっては、これらのコマンドを使用して NuGet の暗黙的な復元を実行するのが不便なことがあります。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-111">Sometimes, it might be inconvenient to run the implicit NuGet restore with these commands.</span></span> <span data-ttu-id="fd3b1-112">たとえば、ビルド システムなど、一部の自動化されているシステムでは、ネットワーク使用状況を制御できるように、`dotnet restore` を明示的に呼び出し、復元のタイミングを制御する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-112">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="fd3b1-113">NuGet の暗黙的な復元が行われないようにするには、`--no-restore` フラグと共にこれらのコマンドのいずれかを使用し、暗黙的復元を無効にします。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-113">To prevent the implicit NuGet restore, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="fd3b1-114">フィードを指定する</span><span class="sxs-lookup"><span data-stu-id="fd3b1-114">Specify feeds</span></span>

<span data-ttu-id="fd3b1-115">依存関係を復元するには、NuGet で、パッケージを配置するフィードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-115">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="fd3b1-116">フィードは、通常、"*nuget.config*" 構成ファイルを通じて提供されます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-116">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="fd3b1-117">既定の構成ファイルは、.NET SDK がインストールされている場合に提供されます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-117">A default configuration file is provided when the .NET SDK is installed.</span></span> <span data-ttu-id="fd3b1-118">追加のフィードを指定するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-118">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="fd3b1-119">プロジェクト ディレクトリに独自の *nuget.config* ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-119">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="fd3b1-120">詳しくは、「[一般的な NuGet 構成](/nuget/consume-packages/configuring-nuget-behavior)」と、この記事の「[nuget.config の相違点](#nugetconfig-differences)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-120">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="fd3b1-121">[`dotnet nuget add source`](dotnet-nuget-add-source.md) などの `dotnet nuget` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-121">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="fd3b1-122">`-s` オプションを使用して *nuget.config* フィードをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-122">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="fd3b1-123">認証済みフィードの使用方法の詳細については、「[認証済みフィードからのパッケージの使用](/nuget/consume-packages/consuming-packages-authenticated-feeds)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-123">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="global-packages-folder"></a><span data-ttu-id="fd3b1-124">グローバル パッケージ フォルダー</span><span class="sxs-lookup"><span data-stu-id="fd3b1-124">Global packages folder</span></span>

<span data-ttu-id="fd3b1-125">依存関係については、`--packages` 引数を使用して復元操作中に復元されたパッケージの配置場所を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-125">For dependencies, you can specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="fd3b1-126">指定されていない場合は、既定の NuGet パッケージ キャッシュが使用されます。これは、すべてのオペレーティング システムのユーザーのホーム ディレクトリ内の `.nuget/packages` ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-126">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="fd3b1-127">たとえば、Linux の場合は */home/user1*、Windows の場合は *C:\Users\user1* です。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-127">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="fd3b1-128">プロジェクト固有のツール</span><span class="sxs-lookup"><span data-stu-id="fd3b1-128">Project-specific tooling</span></span>

<span data-ttu-id="fd3b1-129">プロジェクト固有のツールについては、`dotnet restore` はまず、ツールがパックされているパッケージを復元し、プロジェクト ファイルに指定されているツールの依存関係の復元に進みます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-129">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="fd3b1-130">nuget.config の相違点</span><span class="sxs-lookup"><span data-stu-id="fd3b1-130">nuget.config differences</span></span>

<span data-ttu-id="fd3b1-131">"*nuget.config*" がある場合、`dotnet restore` コマンドの動作はその設定に影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-131">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="fd3b1-132">たとえば、"*nuget.config*" に `globalPackagesFolder` を設定すると、指定されたフォルダーに NuGet パッケージが復元されます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-132">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="fd3b1-133">これは `dotnet restore` コマンドで `--packages` オプションを指定する操作の代替方法です。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-133">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="fd3b1-134">詳細については、「[nuget の .config リファレンス](/nuget/schema/nuget-config-file)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-134">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="fd3b1-135">`dotnet restore` によって無視される、特定の設定が 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-135">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="fd3b1-136">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="fd3b1-136">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="fd3b1-137">バインド リダイレクトは、`<PackageReference>` 要素では機能しません。また、.NET は、NuGet パッケージの `<PackageReference>` 要素のみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-137">Binding redirects don't work with `<PackageReference>` elements and .NET only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="fd3b1-138">solution</span><span class="sxs-lookup"><span data-stu-id="fd3b1-138">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="fd3b1-139">これは、Visual Studio 固有の設定であり、.NET には適用されません。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-139">This setting is Visual Studio specific and doesn't apply to .NET.</span></span> <span data-ttu-id="fd3b1-140">.NET では、`packages.config` ファイルを使用しない代わりに NuGet パッケージの `<PackageReference>` 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-140">.NET doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="fd3b1-141">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="fd3b1-141">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="fd3b1-142">.NET 5.0.100 SDK では、クロスプラットフォーム パッケージの署名の検証のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-142">Support for cross-platform package signature verification was added in the .NET 5.0.100 SDK.</span></span>

## <a name="arguments"></a><span data-ttu-id="fd3b1-143">引数</span><span class="sxs-lookup"><span data-stu-id="fd3b1-143">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="fd3b1-144">復元するプロジェクト ファイルへのオプションのパスです。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-144">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="fd3b1-145">オプション</span><span class="sxs-lookup"><span data-stu-id="fd3b1-145">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="fd3b1-146">復元操作で使用する NuGet 構成ファイル ("*nuget.config*") です。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-146">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="fd3b1-147">複数プロジェクトの並行復元を無効にします。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-147">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="fd3b1-148">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="fd3b1-149">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="fd3b1-150">ロック ファイルが既に存在する場合でも、すべての依存関係を再評価するように強制的に復元します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-150">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="fd3b1-151">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-151">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="fd3b1-152">バージョン要件を満たしているパッケージがある場合は、失敗したソースに関する警告のみです。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-152">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="fd3b1-153">コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="fd3b1-154">.NET Core 2.1.400 以降。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-154">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="fd3b1-155">プロジェクトのロック ファイルの書き込み先である出力場所。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-155">Output location where project lock file is written.</span></span> <span data-ttu-id="fd3b1-156">既定でこれは *PROJECT_ROOT\packages.lock.json* です。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-156">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="fd3b1-157">プロジェクト ロック ファイルの更新は許可されません。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-157">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="fd3b1-158">HTTP 要求をキャッシュしないように指定します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-158">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="fd3b1-159">プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="fd3b1-160">復元されるパッケージのディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-160">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="fd3b1-161">パッケージの復元用のランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="fd3b1-162">これは、 *.csproj* ファイルの `<RuntimeIdentifiers>` タグに明示的にリストされていないランタイムのパッケージを復元するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="fd3b1-163">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="fd3b1-164">このオプションを複数回指定して、複数の RID を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="fd3b1-165">復元操作時に使用する NuGet パッケージ ソースの URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-165">Specifies the URI of the NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="fd3b1-166">この設定により、"*nuget.config*" ファイルに指定されているすべてのソースがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-166">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="fd3b1-167">このオプションを複数回指定することによって、複数のソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lock-file`**

  <span data-ttu-id="fd3b1-168">プロジェクト ロック ファイルを生成して復元で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-168">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="fd3b1-169">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-169">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fd3b1-170">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-170">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="fd3b1-171">既定値は `minimal`にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-171">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="fd3b1-172">使用例</span><span class="sxs-lookup"><span data-stu-id="fd3b1-172">Examples</span></span>

- <span data-ttu-id="fd3b1-173">現在のディレクトリでプロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-173">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="fd3b1-174">指定されたパスで見つかった `app1` プロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-174">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

  ```dotnetcli
  dotnet restore ./projects/app1/app1.csproj
  ```

- <span data-ttu-id="fd3b1-175">ソースとして指定されたファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-175">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="fd3b1-176">ソースとして指定された 2 つのファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-176">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="fd3b1-177">詳細な出力を示して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="fd3b1-177">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
