---
title: バージョン管理および .NET ライブラリ
description: .NET ライブラリのバージョン管理に関するベスト プラクティスの推奨事項。
ms.date: 01/26/2021
ms.openlocfilehash: 36518a607d1c375374ed7cda0e3f3484b55aff11
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259643"
---
# <a name="versioning"></a><span data-ttu-id="1de34-103">バージョン管理</span><span class="sxs-lookup"><span data-stu-id="1de34-103">Versioning</span></span>

<span data-ttu-id="1de34-104">ソフトウェア ライブラリがバージョン 1.0 で完成することは、ほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="1de34-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="1de34-105">優れたライブラリは時間と共に進化し、機能が追加され、バグが修正され、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="1de34-105">Good libraries evolve over time, adding features, fixing bugs, and improving performance.</span></span> <span data-ttu-id="1de34-106">既存のユーザーの互換性を損なわずに、各バージョンに追加の値を付与して、.NET ライブラリの新しいバージョンをリリースできることが重要です。</span><span class="sxs-lookup"><span data-stu-id="1de34-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="1de34-107">互換性に影響する変更</span><span class="sxs-lookup"><span data-stu-id="1de34-107">Breaking changes</span></span>

<span data-ttu-id="1de34-108">バージョン間の互換性に影響する変更の処理方法については、「[重大な変更](./breaking-changes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1de34-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="1de34-109">バージョン番号</span><span class="sxs-lookup"><span data-stu-id="1de34-109">Version numbers</span></span>

<span data-ttu-id="1de34-110">.NET ライブラリには、バージョンを指定する多数の方法があります。</span><span class="sxs-lookup"><span data-stu-id="1de34-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="1de34-111">最も重要なバージョンを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="1de34-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="1de34-112">NuGet パッケージ バージョン</span><span class="sxs-lookup"><span data-stu-id="1de34-112">NuGet package version</span></span>

<span data-ttu-id="1de34-113">[NuGet パッケージ バージョン](/nuget/reference/package-versioning)は NuGet.org、Visual Studio NuGet パッケージ マネージャーに表示され、パッケージの使用時にソース コードに追加されます。</span><span class="sxs-lookup"><span data-stu-id="1de34-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="1de34-114">NuGet パッケージ バージョンは、一般的にユーザーに表示されるバージョンであり、使用しているライブラリのバージョンについてユーザーが話すときは、このバージョンを参照します。</span><span class="sxs-lookup"><span data-stu-id="1de34-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="1de34-115">NuGet パッケージ バージョンは NuGet によって使用され、実行時の動作に影響を及ぼしません。</span><span class="sxs-lookup"><span data-stu-id="1de34-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="1de34-116">NuGet パッケージ バージョンと組み合わせる NuGet パッケージの識別子は、NuGet でパッケージを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1de34-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="1de34-117">たとえば、`Newtonsoft.Json` + `11.0.2` です。</span><span class="sxs-lookup"><span data-stu-id="1de34-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="1de34-118">サフィックスを持つパッケージはプレリリース パッケージであり、テストに最適な特別な動作を備えています。</span><span class="sxs-lookup"><span data-stu-id="1de34-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="1de34-119">詳細については、「[プレリリース パッケージ](./nuget.md#pre-release-packages)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1de34-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="1de34-120">NuGet パッケージ バージョンは、最も開発者の目に留まるバージョンなので、[セマンティック バージョニング (SemVer)](https://semver.org/) を使用してこれを更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1de34-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="1de34-121">SemVer はリリース間の変更の重大度を示し、使用するバージョンを選択するときに、開発者は十分な情報を基に判断できます。</span><span class="sxs-lookup"><span data-stu-id="1de34-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="1de34-122">たとえば、`1.0` から `2.0` への移行は、潜在的に互換性に影響する変更があることを示します。</span><span class="sxs-lookup"><span data-stu-id="1de34-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="1de34-123">ご利用の NuGet パッケージのバージョンに [SemVer 2.0.0](https://semver.org/) を使用することを ✔️ 検討してください。</span><span class="sxs-lookup"><span data-stu-id="1de34-123">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="1de34-124">✔️ 実行 NuGet パッケージ バージョンは一般的にユーザーに表示されるバージョン番号なので、パブリック ドキュメントにはこれを使用する。</span><span class="sxs-lookup"><span data-stu-id="1de34-124">✔️ DO use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="1de34-125">✔️ 実行 非安定版パッケージをリリースする場合は、プレリリース サフィックスを含める。</span><span class="sxs-lookup"><span data-stu-id="1de34-125">✔️ DO include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="1de34-126">ユーザーは、プレリリース パッケージを取得することを選ぶ必要があります。パッケージが完成版ではないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="1de34-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="1de34-127">アセンブリ バージョン</span><span class="sxs-lookup"><span data-stu-id="1de34-127">Assembly version</span></span>

<span data-ttu-id="1de34-128">アセンブリ バージョンは、どのバージョンのアセンブリを読み込むかを選択するために CLR が実行時に使用するバージョンです。</span><span class="sxs-lookup"><span data-stu-id="1de34-128">The assembly version is what the CLR uses at run time to select which version of an assembly to load.</span></span> <span data-ttu-id="1de34-129">バージョン管理を使用したアセンブリの選択は、厳密な名前を持つアセンブリにしか適用されません。</span><span class="sxs-lookup"><span data-stu-id="1de34-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="1de34-130">.NET Framework の CLR では、厳密な名前のアセンブリを読み込むには、完全一致が求められます。</span><span class="sxs-lookup"><span data-stu-id="1de34-130">The .NET Framework CLR demands an exact match to load a strong-named assembly.</span></span> <span data-ttu-id="1de34-131">たとえば、`Library1, Version=1.0.0.0` が `Newtonsoft.Json, Version=11.0.0.0` への参照を使ってコンパイルされたとします。</span><span class="sxs-lookup"><span data-stu-id="1de34-131">For example, `Library1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="1de34-132">.NET Framework は、バージョンが厳密に同じである `11.0.0.0` のみを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1de34-132">.NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="1de34-133">実行時に別のバージョンを読み込むには、バインド リダイレクトが .NET アプリケーションの構成ファイルに追加される必要があります。</span><span class="sxs-lookup"><span data-stu-id="1de34-133">To load a different version at run time, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="1de34-134">アセンブリ バージョンと組み合わせた厳密な名前によって、[厳密なアセンブリ バージョンの読み込み](../assembly/versioning.md)が可能になります。</span><span class="sxs-lookup"><span data-stu-id="1de34-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="1de34-135">ライブラリに厳密な名前を付与すると多くのメリットがありますが、しばしば、アセンブリが見つからないという実行時例外に陥り、修正のために `app.config` または `web.config` での[バインド リダイレクトが必要](../../framework/configure-apps/redirect-assembly-versions.md)になります。</span><span class="sxs-lookup"><span data-stu-id="1de34-135">While strong naming a library has a number of benefits, it often results in run-time exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config` or `web.config` to be fixed.</span></span> <span data-ttu-id="1de34-136">.NET Core では、アセンブリの読み込みはより緩やかです。</span><span class="sxs-lookup"><span data-stu-id="1de34-136">In .NET Core, assembly loading is more relaxed.</span></span> <span data-ttu-id="1de34-137">.NET Core ランタイムは、実行時に、より新しいバージョンのアセンブリを自動的に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1de34-137">The .NET Core runtime automatically loads assemblies with a higher version at run time.</span></span>

<span data-ttu-id="1de34-138">✔️ 検討 AssemblyVersion にメジャー バージョンのみを含める。</span><span class="sxs-lookup"><span data-stu-id="1de34-138">✔️ CONSIDER only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="1de34-139">例: Library 1.0 と Library 1.0.1 は両方とも `1.0.0.0` の AssemblyVersion を備えているのに対して、Library 2.0 は `2.0.0.0` のAssemblyVersion を備えています。</span><span class="sxs-lookup"><span data-stu-id="1de34-139">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="1de34-140">アセンブリ バージョンの変更の頻度が低い場合は、バインド リダイレクトが減少します。</span><span class="sxs-lookup"><span data-stu-id="1de34-140">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="1de34-141">✔️ 検討 AssemblyVersion のメジャー バージョン番号と NuGet パッケージ バージョンの同期を保持する。</span><span class="sxs-lookup"><span data-stu-id="1de34-141">✔️ CONSIDER keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="1de34-142">例外メッセージのアセンブリ名とアセンブリ修飾型名など、AssemblyVersion はユーザーに表示される一部の情報メッセージに含まれています。</span><span class="sxs-lookup"><span data-stu-id="1de34-142">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="1de34-143">バージョン間の関係を維持することで、使用しているバージョンに関する詳細情報を開発者に提供できます。</span><span class="sxs-lookup"><span data-stu-id="1de34-143">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="1de34-144">❌ 禁止 固定の AssemblyVersion を使用する。</span><span class="sxs-lookup"><span data-stu-id="1de34-144">❌ DO NOT have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="1de34-145">固定の AssemblyVersion ではバインド リダイレクトの必要性を回避できるものの、単一のアセンブリ バージョンしかグローバル アセンブリ キャッシュ (GAC) にインストールできないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="1de34-145">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="1de34-146">また、別のアプリケーションが、互換性に影響する変更によって GAC アセンブリを更新した場合、GAC のアセンブリを参照するアプリケーションは中断されます。</span><span class="sxs-lookup"><span data-stu-id="1de34-146">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="1de34-147">アセンブリ ファイル バージョン</span><span class="sxs-lookup"><span data-stu-id="1de34-147">Assembly file version</span></span>

<span data-ttu-id="1de34-148">アセンブリ ファイル バージョンは、Windows でファイル バージョンを表示するために使用されますが、実行時の動作には影響を及ぼしません。</span><span class="sxs-lookup"><span data-stu-id="1de34-148">The assembly file version is used to display a file version in Windows and has no effect on run-time behavior.</span></span> <span data-ttu-id="1de34-149">このバージョンの設定は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1de34-149">Setting this version is optional.</span></span> <span data-ttu-id="1de34-150">これは、Windows エクスプローラーの [ファイルのプロパティ] ダイアログに表示できます。</span><span class="sxs-lookup"><span data-stu-id="1de34-150">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="1de34-151">![Windows エクスプローラー](./media/versioning/win-properties.png "Windows エクスプローラー")</span><span class="sxs-lookup"><span data-stu-id="1de34-151">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="1de34-152">✔️ 検討 AssemblyFileVersion リビジョンとして、継続的インテグレーションのビルド番号を含める。</span><span class="sxs-lookup"><span data-stu-id="1de34-152">✔️ CONSIDER including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="1de34-153">たとえば、プロジェクトのバージョン 1.0.0 を構築しており、継続的インテグレーションのビルド番号が 99 だとすると、お使いの AssemblyFileVersion は 1.0.0.99 になります。</span><span class="sxs-lookup"><span data-stu-id="1de34-153">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="1de34-154">✔️ 実行 ファイル バージョンに形式 `Major.Minor.Build.Revision` を使用する。</span><span class="sxs-lookup"><span data-stu-id="1de34-154">✔️ DO use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="1de34-155">ファイル バージョンは .NET では使用されませんが、[Windows ではファイル バージョン](/windows/desktop/menurc/versioninfo-resource)が `Major.Minor.Build.Revision` 形式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1de34-155">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="1de34-156">バージョンがこの形式に従っていない場合は、警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1de34-156">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="1de34-157">アセンブリの情報バージョン</span><span class="sxs-lookup"><span data-stu-id="1de34-157">Assembly informational version</span></span>

<span data-ttu-id="1de34-158">アセンブリの情報バージョンは、追加のバージョン情報を記録するために使用され、実行時の動作に影響を及ぼしません。</span><span class="sxs-lookup"><span data-stu-id="1de34-158">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="1de34-159">このバージョンの設定は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1de34-159">Setting this version is optional.</span></span> <span data-ttu-id="1de34-160">ソース リンクを使用している場合、NuGet パッケージ バージョンとソース管理バージョンを使って、このバージョンがビルド上に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1de34-160">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="1de34-161">たとえば、`1.0.0-beta1+204ff0a` には、アセンブリの構成元となったソース コードのコミット ハッシュが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1de34-161">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="1de34-162">詳細については、「[ソース リンク](./sourcelink.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1de34-162">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<InformationalVersion>The quick brown fox jumped over the lazy dog.</InformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="1de34-163">このバージョンが `Major.Minor.Build.Revision` の形式に従っていない場合、古いバージョンの Visual Studio によってビルドの警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1de34-163">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="1de34-164">警告は、無視してかまいません。</span><span class="sxs-lookup"><span data-stu-id="1de34-164">The warning can be safely ignored.</span></span>

<span data-ttu-id="1de34-165">❌ 回避 アセンブリの情報バージョンを自分で設定する。</span><span class="sxs-lookup"><span data-stu-id="1de34-165">❌ AVOID setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="1de34-166">NuGet とソース管理メタデータを含むバージョンを SourceLink が自動生成することを許可します。</span><span class="sxs-lookup"><span data-stu-id="1de34-166">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1de34-167">[前へ](publish-nuget-package.md)
>[次へ](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="1de34-167">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
