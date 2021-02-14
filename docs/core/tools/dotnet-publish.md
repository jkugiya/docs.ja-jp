---
title: dotnet publish コマンド
description: dotnet publish コマンドを実行すると、.NET プロジェクトまたはソリューションがディレクトリに発行されます。
ms.date: 02/03/2021
ms.openlocfilehash: 5391e56a88f782294c3a71c523d0fc27a09e0dd8
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585677"
---
# <a name="dotnet-publish"></a><span data-ttu-id="1ca18-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="1ca18-103">dotnet publish</span></span>

<span data-ttu-id="1ca18-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="1ca18-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1ca18-105">名前</span><span class="sxs-lookup"><span data-stu-id="1ca18-105">Name</span></span>

<span data-ttu-id="1ca18-106">`dotnet publish` - ホスティング システムへの展開のため、アプリケーションとその依存関係をフォルダーに発行します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1ca18-107">構文</span><span class="sxs-lookup"><span data-stu-id="1ca18-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a><span data-ttu-id="1ca18-108">説明</span><span class="sxs-lookup"><span data-stu-id="1ca18-108">Description</span></span>

<span data-ttu-id="1ca18-109">`dotnet publish` はアプリケーションをコンパイルし、プロジェクト ファイルに指定されたその依存関係を読み取り、結果のファイル セットをディレクトリに発行します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="1ca18-110">出力には次のアセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-110">The output includes the following assets:</span></span>

- <span data-ttu-id="1ca18-111">アセンブリの中間言語 (IL) コード (*dll* 拡張子)。</span><span class="sxs-lookup"><span data-stu-id="1ca18-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="1ca18-112">*.deps.json* ファイル。プロジェクトのすべての依存関係が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="1ca18-113">*.runtimeconfig.json* ファイル。アプリケーションが想定する共有ランタイムと、ランタイム用の他の構成オプション (ガベージ コレクションの種類など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="1ca18-114">アプリケーションの依存関係。NuGet キャッシュから出力フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="1ca18-115">`dotnet publish` コマンドの出力は、実行のためにホスト システム (サーバー、PC、Mac、ラップトップなど) にすぐに展開できます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="1ca18-116">これは、アプリケーションの展開を準備するための正式にサポートされている唯一の方法です。</span><span class="sxs-lookup"><span data-stu-id="1ca18-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="1ca18-117">プロジェクトで指定されている展開の種類によっては、ホスティング システムに .NET 共有ランタイムがインストールされている場合とされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET shared runtime installed on it.</span></span> <span data-ttu-id="1ca18-118">詳細については、[.NET CLI を使用した .NET アプリの発行](../deploying/deploy-with-cli.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-118">For more information, see [Publish .NET apps with the .NET CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="1ca18-119">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="1ca18-119">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](../../../includes/dotnet-restore-note.md)]

### <a name="msbuild"></a><span data-ttu-id="1ca18-120">MSBuild</span><span class="sxs-lookup"><span data-stu-id="1ca18-120">MSBuild</span></span>

<span data-ttu-id="1ca18-121">`dotnet publish` コマンドは、`Publish` ターゲットを呼び出す MSBuild を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-121">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="1ca18-122">`dotnet publish` に渡されたすべてのパラメーターが MSBuild に渡されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-122">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="1ca18-123">`-c` と `-o` のパラメーターは、それぞれ MSBuild の `Configuration` と `PublishDir` にマップします。</span><span class="sxs-lookup"><span data-stu-id="1ca18-123">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `PublishDir` properties, respectively.</span></span>

<span data-ttu-id="1ca18-124">`dotnet publish` コマンドは、プロパティを設定する `-p` やロガーを定義する `-l` などの MSBuild オプションも受け入れます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-124">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="1ca18-125">たとえば、`-p:<NAME>=<VALUE>` という形式を使用して、MSBuild プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-125">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span>

<span data-ttu-id="1ca18-126">また、(.NET Core 3.1 SDK 以降で入手可能な) *.pubxml* ファイルを参照することで、公開関連のプロパティを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-126">You can also set publish-related properties by referring to a *.pubxml* file (available since .NET Core 3.1 SDK).</span></span> <span data-ttu-id="1ca18-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-127">For example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=FolderProfile
```

<span data-ttu-id="1ca18-128">前記の例では、 *\<project_folder>/Properties/PublishProfiles* フォルダー内に見つかった *FolderProfile.pubxml* ファイルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="1ca18-128">The preceding example uses the *FolderProfile.pubxml* file that is found in the *\<project_folder>/Properties/PublishProfiles* folder.</span></span> <span data-ttu-id="1ca18-129">`PublishProfile` プロパティの設定時にパスとファイル拡張子を指定した場合、それらは無視されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-129">If you specify a path and file extension when setting the `PublishProfile` property, they are ignored.</span></span> <span data-ttu-id="1ca18-130">既定では、MSBuild によって *Properties/PublishProfiles* フォルダー内が調べられ、*pubxml* ファイル拡張子が前提とされます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-130">MSBuild by default looks in the *Properties/PublishProfiles* folder and assumes the *pubxml* file extension.</span></span> <span data-ttu-id="1ca18-131">パスと拡張子を含むファイル名を指定するには、`PublishProfile` プロパティではなく `PublishProfileFullPath` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-131">To specify the path and filename including extension, set the `PublishProfileFullPath` property instead of the `PublishProfile` property.</span></span>

<span data-ttu-id="1ca18-132">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-132">For more information, see the following resources:</span></span>

- [<span data-ttu-id="1ca18-133">MSBuild コマンド ライン リファレンス</span><span class="sxs-lookup"><span data-stu-id="1ca18-133">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="1ca18-134">ASP.NET Core アプリを配置するための Visual Studio 発行プロファイル (.pubxml)</span><span class="sxs-lookup"><span data-stu-id="1ca18-134">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="1ca18-135">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="1ca18-135">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="1ca18-136">引数</span><span class="sxs-lookup"><span data-stu-id="1ca18-136">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="1ca18-137">発行するプロジェクトまたはソリューション。</span><span class="sxs-lookup"><span data-stu-id="1ca18-137">The project or solution to publish.</span></span>

  * <span data-ttu-id="1ca18-138">`PROJECT` は、C#、F#、Visual Basic のプロジェクト ファイルのパスとファイル名、または C#、F#、Visual Basic のプロジェクト ファイルが含まれるディレクトリへのパスです。</span><span class="sxs-lookup"><span data-stu-id="1ca18-138">`PROJECT` is the path and filename of a C#, F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="1ca18-139">ディレクトリが指定されていない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-139">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="1ca18-140">`SOLUTION` は、ソリューション ファイルのパスとファイル名 ( *.sln* 拡張子)、またはソリューション ファイルを含むディレクトリのパスです。</span><span class="sxs-lookup"><span data-stu-id="1ca18-140">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="1ca18-141">ディレクトリが指定されていない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-141">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="1ca18-142">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-142">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="1ca18-143">オプション</span><span class="sxs-lookup"><span data-stu-id="1ca18-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="1ca18-144">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-144">Defines the build configuration.</span></span> <span data-ttu-id="1ca18-145">ほとんどのプロジェクトの既定値は `Debug` ですが、プロジェクトでビルド構成設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="1ca18-146">指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-146">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="1ca18-147">ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-147">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="1ca18-148">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="1ca18-149">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="1ca18-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1ca18-150">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="1ca18-151">コマンドを停止して、ユーザーの入力または操作のために待機させることができます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="1ca18-152">たとえば、認証を完了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-152">For example, to complete authentication.</span></span> <span data-ttu-id="1ca18-153">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="1ca18-154">アプリによって公開された一連のパッケージをトリミングするために使用する[ターゲット マニフェスト](../deploying/runtime-store.md)を 1 つまたは複数指定します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-154">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="1ca18-155">マニフェスト ファイルは、[`dotnet store` コマンド](dotnet-store.md)の出力の一部です。</span><span class="sxs-lookup"><span data-stu-id="1ca18-155">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="1ca18-156">複数のマニフェストを指定するには、マニフェストごとに `--manifest` を追加します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-156">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="1ca18-157">発行の前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="1ca18-157">Doesn't build the project before publishing.</span></span> <span data-ttu-id="1ca18-158">また、`--no-restore` フラグが暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-158">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="1ca18-159">プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-159">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="1ca18-160">著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="1ca18-160">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="1ca18-161">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-161">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="1ca18-162">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="1ca18-162">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="1ca18-163">出力ディレクトリのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-163">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="1ca18-164">指定しない場合、フレームワークに依存する実行可能ファイルおよびクロスプラットフォーム バイナリの既定値は *[project_file_folder]/bin/[configuration]/[framework]/publish/* に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-164">If not specified, it defaults to *[project_file_folder]/bin/[configuration]/[framework]/publish/* for a framework-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="1ca18-165">自己完結型の実行可能ファイルの場合、既定値は *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-165">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="1ca18-166">Web プロジェクトで、出力フォルダーがプロジェクト フォルダー内にある場合、`dotnet publish` コマンドを連続して実行すると、出力フォルダーが入れ子になって生成されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-166">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="1ca18-167">たとえば、プロジェクト フォルダーが *myproject* で、発行の出力フォルダーが *myproject/publish* であり、`dotnet publish` を 2 回実行した場合、2 回目の実行では *myproject/publish/publish* に *.config* および *.json* ファイルなどのコンテンツ ファイルが配置されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-167">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="1ca18-168">発行フォルダーが入れ子にならないようにするには、プロジェクト フォルダーの **直下以外** の発行フォルダーを指定するか、またはプロジェクトから発行フォルダーを除外します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-168">To avoid nesting publish folders, specify a publish folder that is not **directly** under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="1ca18-169">*publishoutput* という名前の発行フォルダーを除外するには、 *.csproj* ファイルの `PropertyGroup` 要素に次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-169">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="1ca18-170">.NET Core 3.x SDK 以降</span><span class="sxs-lookup"><span data-stu-id="1ca18-170">.NET Core 3.x SDK and later</span></span>

    <span data-ttu-id="1ca18-171">プロジェクトを発行するときに相対パスを指定した場合、生成される出力ディレクトリは、プロジェクト ファイルの場所ではなく、現在の作業ディレクトリに相対的なパスとなります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-171">If you specify a relative path when publishing a project, the generated output directory is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="1ca18-172">ソリューションを発行するときに相対パスを指定した場合、すべてのプロジェクトに対する出力はすべて、現在の作業ディレクトリと相対的な指定されたフォルダーに移動されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-172">If you specify a relative path when publishing a solution, all output for all projects goes into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="1ca18-173">発行の出力が各プロジェクトの個別のフォルダーに移動されるようにするには、`--output` オプションの代わりに、msbuild `PublishDir` プロパティを使用して相対パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-173">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="1ca18-174">たとえば、`dotnet publish -p:PublishDir=.\publish` を使用すると、プロジェクト ファイルが格納されているフォルダーの下にある `publish` フォルダーに、各プロジェクトの発行の出力が送信されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-174">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="1ca18-175">.NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="1ca18-175">.NET Core 2.x SDK</span></span>

    <span data-ttu-id="1ca18-176">プロジェクトを発行するときに相対パスを指定した場合、生成される出力ディレクトリは、現在の作業ディレクトリではなく、プロジェクト ファイルの場所に相対的なパスとなります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-176">If you specify a relative path when publishing a project, the generated output directory is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="1ca18-177">ソリューションを発行するときに相対パスを指定した場合、各プロジェクトの出力は、プロジェクト ファイルの場所に相対的な別のフォルダーに移動されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-177">If you specify a relative path when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="1ca18-178">ソリューションを発行するときに絶対パスを指定した場合、すべてのプロジェクトに対する発行の出力はすべて、指定されたフォルダーに移動されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-178">If you specify an absolute path when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun=true`**

  <span data-ttu-id="1ca18-179">アプリケーション アセンブリは ReadyToRun (R2R) 形式にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-179">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="1ca18-180">R2R とは、Ahead-Of-Time (AOT) コンパイルの一種です。</span><span class="sxs-lookup"><span data-stu-id="1ca18-180">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="1ca18-181">詳細については、「[ReadyToRun イメージ](../deploying/ready-to-run.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-181">For more information, see [ReadyToRun images](../deploying/ready-to-run.md).</span></span> <span data-ttu-id="1ca18-182">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-182">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="1ca18-183">実行時エラーの原因になる可能性のある足りない依存関係に関する警告を表示するには、`-p:PublishReadyToRunShowWarnings=true` を使用します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-183">To see warnings about missing dependencies that could cause runtime failures, use `-p:PublishReadyToRunShowWarnings=true`.</span></span>

  <span data-ttu-id="1ca18-184">このオプションは、コマンド ラインではなく、発行プロファイルで指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1ca18-184">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="1ca18-185">詳細については、「[MSBuild](#msbuild)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-185">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile=true`**

  <span data-ttu-id="1ca18-186">アプリを、プラットフォームごとに単一の実行可能ファイルにパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-186">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="1ca18-187">この実行可能ファイルは自己展開型であり、アプリの実行に必要なすべての依存関係 (ネイティブを含む) を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-187">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="1ca18-188">アプリを初めて実行すると、アプリ名とビルド ID に基づいてアプリケーションがディレクトリに抽出されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-188">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="1ca18-189">アプリケーションを再実行すると、起動は速くなります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-189">Startup is faster when the application is run again.</span></span> <span data-ttu-id="1ca18-190">新しいバージョンが使用されない限り、アプリケーションは自身を 2 回抽出する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="1ca18-190">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="1ca18-191">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-191">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="1ca18-192">単一ファイルの発行の詳細については、[単一ファイル バンドラー設計のドキュメント](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-192">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="1ca18-193">このオプションは、コマンド ラインではなく、発行プロファイルで指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1ca18-193">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="1ca18-194">詳細については、「[MSBuild](#msbuild)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-194">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed=true`**

  <span data-ttu-id="1ca18-195">自己完結型の実行可能ファイルを発行するとき、使用されていないライブラリをトリミングして、アプリの展開サイズを減らします。</span><span class="sxs-lookup"><span data-stu-id="1ca18-195">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="1ca18-196">詳細については、「[自己完結型の展開と実行可能ファイルのトリミング](../deploying/trim-self-contained.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-196">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="1ca18-197">.NET Core 3.0 SDK 以降では、プレビュー機能として利用できます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-197">Available since .NET Core 3.0 SDK as a preview feature.</span></span>

  <span data-ttu-id="1ca18-198">このオプションは、コマンド ラインではなく、発行プロファイルで指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1ca18-198">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="1ca18-199">詳細については、「[MSBuild](#msbuild)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-199">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="1ca18-200">アプリケーションと併せて .NET ランタイムを発行します。これにより、ランタイムをターゲット コンピューターにインストールする必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-200">Publishes the .NET runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="1ca18-201">ランタイム識別子が指定され、プロジェクトが (ライブラリ プロジェクトではなく) 実行可能なプロジェクトである場合、既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="1ca18-201">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="1ca18-202">詳細については、[.NET アプリケーションの発行](../deploying/index.md)、および [.NET CLI を使用した .NET アプリの発行](../deploying/deploy-with-cli.md)に関する各記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-202">For more information, see [.NET application publishing](../deploying/index.md) and [Publish .NET apps with the .NET CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="1ca18-203">`true` または `false` を指定せずに、このオプションを使用した場合、既定値は `true` になります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-203">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="1ca18-204">その場合は、その位置で `true` または `false` が想定されているため、`--self-contained` の直後にソリューションまたはプロジェクト引数を配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-204">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="1ca18-205">これは、`--self-contained false` に相当します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-205">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="1ca18-206">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-206">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="1ca18-207">指定されたランタイムのアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-207">Publishes the application for a given runtime.</span></span> <span data-ttu-id="1ca18-208">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-208">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="1ca18-209">詳細については、[.NET アプリケーションの発行](../deploying/index.md)、および [.NET CLI を使用した .NET アプリの発行](../deploying/deploy-with-cli.md)に関する各記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-209">For more information, see [.NET application publishing](../deploying/index.md) and [Publish .NET apps with the .NET CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="1ca18-210">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-210">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1ca18-211">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="1ca18-211">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="1ca18-212">既定値は `minimal`にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-212">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="1ca18-213">プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-213">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="1ca18-214">使用例</span><span class="sxs-lookup"><span data-stu-id="1ca18-214">Examples</span></span>

- <span data-ttu-id="1ca18-215">現在のディレクトリに、プロジェクト用の[フレームワークに依存するクロスプラットフォーム バイナリ](../deploying/index.md#produce-a-cross-platform-binary)を作成します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-215">Create a [framework-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="1ca18-216">この例では、.NET Core 3.0 SDK 以降、現在のプラットフォーム用の[フレームワークに依存する実行可能ファイル](../deploying/index.md#publish-framework-dependent)も作成されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-216">Starting with .NET Core 3.0 SDK, this example also creates a [framework-dependent executable](../deploying/index.md#publish-framework-dependent) for the current platform.</span></span>

- <span data-ttu-id="1ca18-217">特定のランタイムに対して、現在のディレクトリ内にプロジェクト用の[自己完結型の実行可能ファイル](../deploying/index.md#publish-self-contained)を作成します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-217">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="1ca18-218">RID をプロジェクト ファイルに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-218">The RID must be in the project file.</span></span>

- <span data-ttu-id="1ca18-219">特定のプラットフォーム用に、プロジェクト用の[フレームワークに依存する実行可能ファイル](../deploying/index.md#publish-framework-dependent)を現在のディレクトリに作成します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-219">Create a [framework-dependent executable](../deploying/index.md#publish-framework-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="1ca18-220">RID をプロジェクト ファイルに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ca18-220">The RID must be in the project file.</span></span> <span data-ttu-id="1ca18-221">この例は、.NET Core 3.0 SDK 以降のバージョンに適用されます。</span><span class="sxs-lookup"><span data-stu-id="1ca18-221">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="1ca18-222">特定のランタイムとターゲット フレームワーク用に、現在のディレクトリのプロジェクトを発行します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-222">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="1ca18-223">指定されたプロジェクト ファイルを発行します。</span><span class="sxs-lookup"><span data-stu-id="1ca18-223">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="1ca18-224">現在のアプリケーションを発行します。ただし、復元操作中はルート プロジェクトのみを復元し、プロジェクト間 (P2P) 参照は復元しないでください。</span><span class="sxs-lookup"><span data-stu-id="1ca18-224">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="1ca18-225">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ca18-225">See also</span></span>

- [<span data-ttu-id="1ca18-226">.NET アプリケーションの発行の概要</span><span class="sxs-lookup"><span data-stu-id="1ca18-226">.NET application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="1ca18-227">.NET CLI を使用した .NET アプリの発行</span><span class="sxs-lookup"><span data-stu-id="1ca18-227">Publish .NET apps with the .NET CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="1ca18-228">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="1ca18-228">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="1ca18-229">Runtime Identifier (RID) カタログ</span><span class="sxs-lookup"><span data-stu-id="1ca18-229">Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="1ca18-230">macOS Catalina の公証に対応する</span><span class="sxs-lookup"><span data-stu-id="1ca18-230">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="1ca18-231">発行されたアプリケーションのディレクトリ構造</span><span class="sxs-lookup"><span data-stu-id="1ca18-231">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="1ca18-232">MSBuild コマンド ライン リファレンス</span><span class="sxs-lookup"><span data-stu-id="1ca18-232">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="1ca18-233">ASP.NET Core アプリを配置するための Visual Studio 発行プロファイル (.pubxml)</span><span class="sxs-lookup"><span data-stu-id="1ca18-233">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="1ca18-234">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="1ca18-234">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="1ca18-235">ILLInk.Tasks</span><span class="sxs-lookup"><span data-stu-id="1ca18-235">ILLInk.Tasks</span></span>](../deploying/trim-self-contained.md)
