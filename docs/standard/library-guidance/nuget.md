---
title: NuGet および .NET ライブラリ
description: .NET ライブラリ対応の NuGet によるパッケージ化のベスト プラクティスの推奨事項
ms.date: 01/15/2019
ms.openlocfilehash: 251e5b10db7eab731133e157dc5ac2c95a6ef317
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872445"
---
# <a name="nuget"></a><span data-ttu-id="35ee5-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="35ee5-103">NuGet</span></span>

<span data-ttu-id="35ee5-104">NuGet は .NET エコシステムのパッケージ マネージャーであり、開発者が .NET オープンソース ライブラリを見つけて入手するための主要な方法です。</span><span class="sxs-lookup"><span data-stu-id="35ee5-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="35ee5-105">NuGet パッケージをホストするために Microsoft が提供している無料サービスの [NuGet.org](https://www.nuget.org/) は、パブリック NuGet パッケージのプライマリ ホストですが、[MyGet](https://www.myget.org/) および [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/) などのカスタム NuGet サービスに公開できます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="35ee5-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="35ee5-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="35ee5-107">NuGet パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="35ee5-107">Create a NuGet package</span></span>

<span data-ttu-id="35ee5-108">NuGet パッケージ (`*.nupkg`) は、.NET アセンブリと関連するメタデータを含む zip ファイルです。</span><span class="sxs-lookup"><span data-stu-id="35ee5-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="35ee5-109">NuGet パッケージを作成するには、主な方法が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="35ee5-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="35ee5-110">より新しいお勧めの方法は、SDK 形式のプロジェクト (コンテンツが `<Project Sdk="Microsoft.NET.Sdk">` から始まるプロジェクト ファイル) からパッケージを作成することです。</span><span class="sxs-lookup"><span data-stu-id="35ee5-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="35ee5-111">アセンブリとターゲットが自動的にパッケージに追加され、パッケージ名やバージョン番号などの残りのメタデータが、MSBuild ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="35ee5-112">[`dotnet pack`](../../core/tools/dotnet-pack.md) コマンドを使ってコンパイルすると、アセンブリの代わりに `*.nupkg` ファイルが出力されます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="35ee5-113">NuGet パッケージを作成する従来からの方法では、`*.nuspec` ファイルと `nuget.exe` コマンドライン ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="35ee5-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="35ee5-114">nuspec ファイルを使用すると、優れた制御を利用できますが、最終的な NuGet パッケージに含めるアセンブリとターゲットを慎重に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35ee5-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="35ee5-115">間違えやすいうえに、変更を加える際にユーザーは nuspec の更新を忘れやすいです。</span><span class="sxs-lookup"><span data-stu-id="35ee5-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="35ee5-116">nuspec の利点は、まだ SDK 形式のプロジェクト ファイルをサポートしていないフレームワークの NuGet パッケージを作成するために使用できることです。</span><span class="sxs-lookup"><span data-stu-id="35ee5-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="35ee5-117">✔️ SDK 形式のプロジェクト ファイルを使用して NuGet パッケージを作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-117">✔️ CONSIDER using an SDK-style project file to create the NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="35ee5-118">パッケージの依存関係</span><span class="sxs-lookup"><span data-stu-id="35ee5-118">Package dependencies</span></span>

<span data-ttu-id="35ee5-119">NuGet パッケージの依存関係については、「[Dependencies](./dependencies.md)」 (依存関係) の記事で説明しています。</span><span class="sxs-lookup"><span data-stu-id="35ee5-119">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="35ee5-120">重要な NuGet パッケージ メタデータ</span><span class="sxs-lookup"><span data-stu-id="35ee5-120">Important NuGet package metadata</span></span>

<span data-ttu-id="35ee5-121">NuGet パッケージは、多数の[メタデータ プロパティ](/nuget/reference/nuspec)をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="35ee5-121">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="35ee5-122">次の表に、NuGet.org 上のすべてのパッケージで指定する必要があるコア メタデータを示します。</span><span class="sxs-lookup"><span data-stu-id="35ee5-122">The following table contains the core metadata that every package on NuGet.org should provide:</span></span>

| <span data-ttu-id="35ee5-123">MSBuild プロパティの名前</span><span class="sxs-lookup"><span data-stu-id="35ee5-123">MSBuild Property name</span></span>              | <span data-ttu-id="35ee5-124">Nuspec の名前</span><span class="sxs-lookup"><span data-stu-id="35ee5-124">Nuspec name</span></span>              | <span data-ttu-id="35ee5-125">説明</span><span class="sxs-lookup"><span data-stu-id="35ee5-125">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="35ee5-126">パッケージ ID。</span><span class="sxs-lookup"><span data-stu-id="35ee5-126">The package identifier.</span></span> <span data-ttu-id="35ee5-127">[条件](/nuget/reference/id-prefix-reservation)を満たしている場合、ID のプレフィックスは予約できます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-127">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="35ee5-128">NuGet パッケージ バージョン。</span><span class="sxs-lookup"><span data-stu-id="35ee5-128">NuGet package version.</span></span> <span data-ttu-id="35ee5-129">詳細については、「[NuGet package version](./versioning.md#nuget-package-version)」(NuGet package version パッケージ バージョン) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-129">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="35ee5-130">わかりやすいパッケージ タイトル。</span><span class="sxs-lookup"><span data-stu-id="35ee5-130">A human-friendly title of the package.</span></span> <span data-ttu-id="35ee5-131">既定値は `PackageId` です。</span><span class="sxs-lookup"><span data-stu-id="35ee5-131">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="35ee5-132">UI に表示されるパッケージの長い説明。</span><span class="sxs-lookup"><span data-stu-id="35ee5-132">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="35ee5-133">パッケージ作成者のコンマで区切りの一覧。nuget.org のプロファイル名と一致します。</span><span class="sxs-lookup"><span data-stu-id="35ee5-133">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="35ee5-134">空白またはセミコロンで区切られた、パッケージを記述するタグとキーワードの一覧。</span><span class="sxs-lookup"><span data-stu-id="35ee5-134">A space or semicolon-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="35ee5-135">タグは、パッケージを検索するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-135">Tags are used when searching for packages.</span></span>             |
| `PackageIcon`                   | `icon`                  | <span data-ttu-id="35ee5-136">パッケージ アイコンとして使用するパッケージ内の画像へのパス。</span><span class="sxs-lookup"><span data-stu-id="35ee5-136">A path to an image in the package to use as a package icon.</span></span> <span data-ttu-id="35ee5-137">`icon` メタデータの詳細については、[こちら](/nuget/reference/nuspec#icon)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-137">Read more about [`icon` metadata](/nuget/reference/nuspec#icon).</span></span> |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="35ee5-138">プロジェクトのホーム ページまたはソース リポジトリの URL。</span><span class="sxs-lookup"><span data-stu-id="35ee5-138">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseExpression`         | `license`                  | <span data-ttu-id="35ee5-139">プロジェクト ライセンスの [SPDX 識別子](https://spdx.org/licenses/)。</span><span class="sxs-lookup"><span data-stu-id="35ee5-139">The project license's [SPDX identifier](https://spdx.org/licenses/).</span></span> <span data-ttu-id="35ee5-140">OSI と FSF によって承認されたライセンスのみが識別子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-140">Only OSI and FSF approved licenses can use an identifier.</span></span> <span data-ttu-id="35ee5-141">その他のライセンスでは、`PackageLicenseFile` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35ee5-141">Other licenses should use `PackageLicenseFile`.</span></span> <span data-ttu-id="35ee5-142">`license` メタデータの詳細については、[こちら](/nuget/reference/nuspec#license)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-142">Read more about [`license` metadata](/nuget/reference/nuspec#license).</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="35ee5-143">ライセンスのないプロジェクトは、[排他的な著作権](https://choosealicense.com/no-permission/)を侵害しているため、他のユーザーが合法的に使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="35ee5-143">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it legally impossible for other people to use.</span></span>

<span data-ttu-id="35ee5-144">✔️ NuGet のプレフィックスの予約[条件](/nuget/reference/id-prefix-reservation)を満たしているプレフィックスを持つ NuGet パッケージ名を選択することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-144">✔️ CONSIDER choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="35ee5-145">✔️ パッケージのアイコンに HTTPS href を使用してください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-145">✔️ DO use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="35ee5-146">NuGet.org のようなサイトは HTTPS を有効にした状態で実行され、HTTPS ではないイメージを表示すると、コンテンツの混合を示す警告が作成されます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-146">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="35ee5-147">✔️ 最良な表示結果になるように、64 x 64 で透明な背景を持つパッケージ アイコン イメージを使用してください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-147">✔️ DO use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

<span data-ttu-id="35ee5-148">✔️ [ソース リンク](./sourcelink.md)を設定して、お使いのアセンブリと NuGet パッケージにソース管理のメタデータを追加することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-148">✔️ CONSIDER setting up [Source Link](./sourcelink.md) to add source control metadata to your assemblies and NuGet package.</span></span>

> <span data-ttu-id="35ee5-149">ソース リンクによってメタデータの `RepositoryUrl` と `RepositoryType` が NuGet パッケージに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-149">Source Link automatically adds `RepositoryUrl` and `RepositoryType` metadata to the NuGet package.</span></span> <span data-ttu-id="35ee5-150">また、ソース リンクによって、パッケージの作成元のソース コードに関する情報が追加されます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-150">Source Link also adds information about the exact source code the package was built from.</span></span> <span data-ttu-id="35ee5-151">たとえば、Git リポジトリから作成されたパッケージでは、コミット ハッシュがメタデータとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-151">For example, a package created from a Git repository will have the commit hash added as metadata.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="35ee5-152">プレリリース パッケージ</span><span class="sxs-lookup"><span data-stu-id="35ee5-152">Pre-release packages</span></span>

<span data-ttu-id="35ee5-153">バージョン サフィックスがある NuGet パッケージは、[プレリリース](/nuget/create-packages/prerelease-packages)と見なされます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-153">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="35ee5-154">プレリリース パッケージが制限付きユーザーのテスト実行に最適になるように、ユーザーがプレリリース パッケージを選択しない限り、既定では、NuGet パッケージ マネージャーの UI は、安定版リリースを表示します。</span><span class="sxs-lookup"><span data-stu-id="35ee5-154">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="35ee5-155">安定版パッケージは、プレリリース パッケージに依存できません。</span><span class="sxs-lookup"><span data-stu-id="35ee5-155">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="35ee5-156">独自のパッケージをプレリリースにするか、または旧来の安定版バージョンに依存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35ee5-156">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="35ee5-157">![NuGet プレリリース パッケージの依存関係](./media/nuget/nuget-prerelease-package.png "NuGet プレリリース パッケージの依存関係")</span><span class="sxs-lookup"><span data-stu-id="35ee5-157">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="35ee5-158">✔️ テスト、プレビュー、または実験時には、プレリリース パッケージを公開してください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-158">✔️ DO publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="35ee5-159">✔️ 他の安定版パッケージから参照できるように、準備ができ次第、安定版パッケージを公開してください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-159">✔️ DO publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="35ee5-160">シンボル パッケージ</span><span class="sxs-lookup"><span data-stu-id="35ee5-160">Symbol packages</span></span>

<span data-ttu-id="35ee5-161">シンボル ファイル (`*.pdb`) は、アセンブリと共に .NET コンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-161">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="35ee5-162">デバッガ―を使用して実行しながらソース コード全体をステップ実行できるように、シンボル ファイルは、実行場所を元のソース コードにマップします。</span><span class="sxs-lookup"><span data-stu-id="35ee5-162">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="35ee5-163">NuGet では、.NET アセンブリを含む主要なパッケージと共に、シンボル ファイルを格納している[別個のシンボル パッケージ (`*.snupkg`) の生成](/nuget/create-packages/symbol-packages-snupkg)をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="35ee5-163">NuGet supports [generating a separate symbol package (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="35ee5-164">シンボル サーバー上でホストされ、Visual Studio などのツールによってオンデマンドでしかダウンロードできないのが、シンボル パッケージの考え方です。</span><span class="sxs-lookup"><span data-stu-id="35ee5-164">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="35ee5-165">NuGet.org は独自の[シンボル サーバー リポジトリ](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server)をホストしています。</span><span class="sxs-lookup"><span data-stu-id="35ee5-165">NuGet.org hosts its own [symbols server repository](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span></span> <span data-ttu-id="35ee5-166">開発者は [Visual Studio でシンボル ソース](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)に `https://symbols.nuget.org/download/symbols` を追加することで NuGet.org シンボル サーバーに公開されたシンボルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-166">Developers can use the symbols published to the NuGet.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their [symbol sources in Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35ee5-167">NuGet.org シンボル サーバーでは、SDK スタイルのプロジェクトで作成された新しい[ポータブル シンボル ファイル](https://github.com/dotnet/core/blob/main/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-167">The NuGet.org symbol server only supports the new [portable symbol files](https://github.com/dotnet/core/blob/main/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects.</span></span>
>
> <span data-ttu-id="35ee5-168">.NET ライブラリのデバッグ時に NuGet.org シンボル サーバーを使用するには、開発者が Visual Studio 2017 バージョン 15.9 以降を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="35ee5-168">To use the NuGet.org symbol server when debugging a .NET library, developers must have Visual Studio 2017 version 15.9 or later.</span></span>

<span data-ttu-id="35ee5-169">シンボル パッケージを作成する代わりに、主要 NuGet パッケージにシンボル ファイルを埋め込むという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="35ee5-169">An alternative to creating a symbol package is embedding symbol files in the main NuGet package.</span></span> <span data-ttu-id="35ee5-170">主要 NuGet パッケージは大容量になりますが、シンボル ファイルを埋め込む場合、開発者は NuGet.org シンボル サーバーを設定する必要がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="35ee5-170">The main NuGet package will be larger, but the embedded symbol files means developers don't need to configure the NuGet.org symbol server.</span></span> <span data-ttu-id="35ee5-171">SDK 形式のプロジェクトを使用して NuGet パッケージを構築している場合、`AllowedOutputExtensionsInPackageBuildOutputFolder` プロパティを設定してシンボル ファイルを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="35ee5-171">If you're building your NuGet package using an SDK-style project, then you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="35ee5-172">シンボル ファイルを埋め込むことの短所は、SDK スタイルのプロジェクトでコンパイルした .NET ライブラリの場合、パッケージ サイズが約 30% 増えるということです。</span><span class="sxs-lookup"><span data-stu-id="35ee5-172">The downside of embedding symbol files is that they increase the package size by about 30% for .NET libraries compiled using SDK-style projects.</span></span> <span data-ttu-id="35ee5-173">パッケージ サイズが問題であれば、代わりにシンボル パッケージでシンボルを公開してください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-173">If package size is a concern, you should publish symbols in a symbol package instead.</span></span>

<span data-ttu-id="35ee5-174">✔️ シンボルをシンボル パッケージ (`*.snupkg`) として NuGet.org に発行することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="35ee5-174">✔️ CONSIDER publishing symbols as a symbol package (`*.snupkg`) to NuGet.org</span></span>

> <span data-ttu-id="35ee5-175">シンボル パッケージ (`*.snupkg`) は、メイン パッケージのサイズを肥大化させることなく、また NuGet パッケージをデバッグする予定のない人の復元パフォーマンスに影響を及ぼすことなく、オンデマンドの良好なデバッグ エクスペリエンスを開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="35ee5-175">Symbol packages (`*.snupkg`) provide developers a good on-demand debugging experience without bloating the main package size and impacting restore performance for those who don't intend to debug the NuGet package.</span></span>
>
> <span data-ttu-id="35ee5-176">注意点は、ユーザーが自分の IDE 内で NuGet シンボル サーバーを見つけ、(1 回限りのセットアップとして) 構成し、シンボル ファイルを取得する必要があることです。</span><span class="sxs-lookup"><span data-stu-id="35ee5-176">The caveat is that users may need to find and configure the NuGet symbol server in their IDE (as a one-time setup) to get symbol files.</span></span> <span data-ttu-id="35ee5-177">Visual Studio 2019 バージョン 16.1 では、既定のシンボル サーバーの一覧に NuGet.org のシンボル サーバーが追加されました。</span><span class="sxs-lookup"><span data-stu-id="35ee5-177">Visual Studio 2019 version 16.1 added NuGet.org's symbol server to the list of default symbol servers.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="35ee5-178">[前へ](strong-naming.md)
>[次へ](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="35ee5-178">[Previous](strong-naming.md)
[Next](dependencies.md)</span></span>
