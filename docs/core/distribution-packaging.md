---
title: .NET の配布パッケージ
description: .NET を配布用にパッケージ化、名前付け、およびバージョン管理する方法について学習します。
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 93d040064eb739b3bd045fdb16b356732353ddc8
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216305"
---
# <a name="net-distribution-packaging"></a><span data-ttu-id="b9cab-103">.NET の配布パッケージ</span><span class="sxs-lookup"><span data-stu-id="b9cab-103">.NET distribution packaging</span></span>

<span data-ttu-id="b9cab-104">.NET 5 (および .NET Core) 以降のバージョンはますます多くのプラットフォームで利用できるようになっているため、それを使用するアプリやライブラリをパッケージ化、名前付け、およびバージョン管理する方法を知っていると便利です。</span><span class="sxs-lookup"><span data-stu-id="b9cab-104">As .NET 5 (and .NET Core) and later versions become available on more and more platforms, it's useful to learn how to package, name, and version apps and libraries that use it.</span></span> <span data-ttu-id="b9cab-105">そうすることで、パッケージの管理者は、ユーザーの .NET の実行環境に左右されることなく一貫した体験が保証されるようにサポートできます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="b9cab-106">この記事は以下のユーザーに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="b9cab-107">ソースから .NET をビルドしようとしている。</span><span class="sxs-lookup"><span data-stu-id="b9cab-107">Attempting to build .NET from source.</span></span>
- <span data-ttu-id="b9cab-108">結果として生じるレイアウトまたは生成されるパッケージに影響する可能性がある .NET CLI に変更を加えたい。</span><span class="sxs-lookup"><span data-stu-id="b9cab-108">Wanting to make changes to the .NET CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="b9cab-109">ディスク レイアウト</span><span class="sxs-lookup"><span data-stu-id="b9cab-109">Disk layout</span></span>

<span data-ttu-id="b9cab-110">インストールした .NET は複数のコンポーネントで構成されています。これらはファイル システムで次のようにレイアウトされています。</span><span class="sxs-lookup"><span data-stu-id="b9cab-110">When installed, .NET consists of several components that are laid out as follows in the file system:</span></span>

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="b9cab-111">(1) **dotnet** ホスト (別名 "muxer (マルチプレクサー)") には 2 つの異なるロールがあります。アプリケーションを起動するランタイムのアクティブ化と、コマンドをディスパッチする SDK のアクティブ化です。</span><span class="sxs-lookup"><span data-stu-id="b9cab-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="b9cab-112">ホストはネイティブの実行可能ファイルです (`dotnet.exe`)。</span><span class="sxs-lookup"><span data-stu-id="b9cab-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="b9cab-113">ホストは 1 つですが、他のコンポーネントのほとんどはバージョン管理されたディレクトリに入っています (2、3、5、6)。</span><span class="sxs-lookup"><span data-stu-id="b9cab-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="b9cab-114">つまり、複数のバージョンが並列インストールされるので、それらをシステム上に置くことができます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="b9cab-115">(2) **host/fxr/\<fxr version>** には、ホストが使用するフレームワーク解決ロジックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="b9cab-116">ホストでは、インストールされている最新の hostfxr が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="b9cab-117">hostfxr は、.NET アプリケーションの実行時に適切なランタイムを選択する役割があります。</span><span class="sxs-lookup"><span data-stu-id="b9cab-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET application.</span></span> <span data-ttu-id="b9cab-118">たとえば、.NET Core 2.0.0 用としてビルドされたアプリケーションは、2.0.5 が利用できればそれを利用します。</span><span class="sxs-lookup"><span data-stu-id="b9cab-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="b9cab-119">同様に、hostfxr は開発中、適切な SDK を選択します。</span><span class="sxs-lookup"><span data-stu-id="b9cab-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="b9cab-120">(3) **sdk/\<sdk version>** SDK ("ツール" ともいう) は、.NET のライブラリやアプリケーションを記述およびビルドするために使用されるマネージド ツールのセットです。</span><span class="sxs-lookup"><span data-stu-id="b9cab-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET libraries and applications.</span></span> <span data-ttu-id="b9cab-121">SDK には、.NET CLI、マネージ言語コンパイラ、MSBuild、関連するビルド タスクとターゲット、NuGet、新しいプロジェクト テンプレートなどが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9cab-121">The SDK includes the .NET CLI, the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="b9cab-122">(4) **sdk/NuGetFallbackFolder** には、`dotnet restore` や `dotnet build` の実行時など、復元操作中に SDK によって使用される NuGet パッケージのキャッシュが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9cab-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="b9cab-123">このフォルダーは、.NET Core 3.0 より前でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="b9cab-124">`nuget.org` からの構築済みのバイナリ アセットを含むため、ソースから作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="b9cab-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="b9cab-125">**共有** フォルダーには、フレームワークが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9cab-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="b9cab-126">共有フレームワークは、さまざまなアプリケーションで利用できるように、中央の場所で一連のライブラリを提供します。</span><span class="sxs-lookup"><span data-stu-id="b9cab-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="b9cab-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** このフレームワークには、.NET のランタイムと補助マネージド ライブラリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9cab-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="b9cab-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** には、ASP.NET Core ライブラリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="b9cab-129">`Microsoft.AspNetCore.App` の下にあるライブラリは、.NET プロジェクトの一部として開発され、サポートされています。</span><span class="sxs-lookup"><span data-stu-id="b9cab-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET project.</span></span> <span data-ttu-id="b9cab-130">`Microsoft.AspNetCore.All` の下にあるライブラリは、サードパーティ製ライブラリも含まれるスーパーセットです。</span><span class="sxs-lookup"><span data-stu-id="b9cab-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="b9cab-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** には、Windows デスクトップ ライブラリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="b9cab-132">これは、Windows 以外のプラットフォームには含まれていません。</span><span class="sxs-lookup"><span data-stu-id="b9cab-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="b9cab-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** は、それぞれ .NET ライセンスと、.NET で利用されるサードパーティ ライブラリのライセンスです。</span><span class="sxs-lookup"><span data-stu-id="b9cab-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET license and licenses of third-party libraries used in .NET, respectively.</span></span>

- <span data-ttu-id="b9cab-134">(9,10) **dotnet.1.gz、dotnet** `dotnet.1.gz` は dotnet のマニュアル ページです。</span><span class="sxs-lookup"><span data-stu-id="b9cab-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="b9cab-135">`dotnet` は dotnet host(1) のシンボリック リンクです。</span><span class="sxs-lookup"><span data-stu-id="b9cab-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="b9cab-136">これらのファイルは、システム統合のために、よく知られている場所にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-136">These files are installed at well-known locations for system integration.</span></span>

- <span data-ttu-id="b9cab-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** には、.NET と ASP.NET Core のそれぞれの `x.y` バージョンの API が記述されています。</span><span class="sxs-lookup"><span data-stu-id="b9cab-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET and ASP.NET Core respectively.</span></span> <span data-ttu-id="b9cab-138">これらのパックは、それのターゲット バージョンのコンパイル時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="b9cab-139">(13) **Microsoft.NETCore.App.Host.\<rid>**</span><span class="sxs-lookup"><span data-stu-id="b9cab-139">(13) **Microsoft.NETCore.App.Host.\<rid>**</span></span> <span data-ttu-id="b9cab-140">にはプラットフォームのネイティブ バイナリが含まれています`rid`。</span><span class="sxs-lookup"><span data-stu-id="b9cab-140">contains a native binary for platform `rid`.</span></span> <span data-ttu-id="b9cab-141">このバイナリは、.NET アプリケーションをそのプラットフォームのネイティブ バイナリにコンパイルするときのテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="b9cab-141">This binary is a template when compiling a .NET application into a native binary for that platform.</span></span>

- <span data-ttu-id="b9cab-142">(14) **Microsoft.WindowsDesktop.App.Ref** には、Windows Desktop アプリケーションの `x.y` バージョンの API が記述されています。</span><span class="sxs-lookup"><span data-stu-id="b9cab-142">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="b9cab-143">これらのファイルは、そのターゲットに対してコンパイルする場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-143">These files are used when compiling for that target.</span></span> <span data-ttu-id="b9cab-144">これは、Windows 以外のプラットフォームにはありません。</span><span class="sxs-lookup"><span data-stu-id="b9cab-144">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="b9cab-145">(15) **NETStandard.Library.Ref** には、netstandard `x.y` の API が記述されています。</span><span class="sxs-lookup"><span data-stu-id="b9cab-145">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="b9cab-146">これらのファイルは、そのターゲットに対してコンパイルする場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-146">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="b9cab-147">(16) **/etc/dotnet/install_location** は、`{dotnet_root}` の完全なパスを含むファイルです。</span><span class="sxs-lookup"><span data-stu-id="b9cab-147">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="b9cab-148">パスの末尾は改行文字である場合があります。</span><span class="sxs-lookup"><span data-stu-id="b9cab-148">The path may end with a newline.</span></span> <span data-ttu-id="b9cab-149">ルートが `/usr/share/dotnet` の場合は、このファイルを追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b9cab-149">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="b9cab-150">(17) **templates** には、SDK で使用されるテンプレートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-150">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="b9cab-151">たとえば、`dotnet new` はここからプロジェクト テンプレートを検索します。</span><span class="sxs-lookup"><span data-stu-id="b9cab-151">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="b9cab-152">`(*)` でマークされたフォルダーは、複数のパッケージによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-152">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="b9cab-153">一部のパッケージ形式 (たとえば、`rpm`) では、このようなフォルダーを特別に処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9cab-153">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="b9cab-154">パッケージのメンテナンス担当者は、このことに対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9cab-154">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="b9cab-155">推奨パッケージ</span><span class="sxs-lookup"><span data-stu-id="b9cab-155">Recommended packages</span></span>

<span data-ttu-id="b9cab-156">.NET バージョン管理は、ランタイム コンポーネント `[major].[minor]` バージョン番号に基づきます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-156">.NET versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="b9cab-157">SDK バージョンは同じ `[major].[minor]` を利用し、SDK の機能とパッチ意味論を結合する非依存の `[patch]` が与えられます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-157">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="b9cab-158">次に例を示します。SDK バージョン 2.2.302 は、2.2 ランタイム対応の SDK の第 3 機能リリースの第 2 パッチ リリースです。</span><span class="sxs-lookup"><span data-stu-id="b9cab-158">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="b9cab-159">バージョン管理のしくみの詳細については、[.NET のバージョン管理の概要](./versions/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9cab-159">For more information about how versioning works, see [.NET versioning overview](./versions/index.md).</span></span>

<span data-ttu-id="b9cab-160">パッケージには、その名前にバージョン番号の一部が含まれているものもあります。</span><span class="sxs-lookup"><span data-stu-id="b9cab-160">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="b9cab-161">それによって、特定のバージョンをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-161">This allows you to install a specific version.</span></span>
<span data-ttu-id="b9cab-162">バージョンの残りの部分はバージョン名には含まれていません。</span><span class="sxs-lookup"><span data-stu-id="b9cab-162">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="b9cab-163">それによって、OS パッケージ マネージャーはパッケージを更新できます (セキュリティ修正の自動インストールなど)。</span><span class="sxs-lookup"><span data-stu-id="b9cab-163">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="b9cab-164">サポートされるパッケージ マネージャーは Linux 固有です。</span><span class="sxs-lookup"><span data-stu-id="b9cab-164">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="b9cab-165">推奨するパッケージを、以下に示します。</span><span class="sxs-lookup"><span data-stu-id="b9cab-165">The following lists the recommended packages:</span></span>

- <span data-ttu-id="b9cab-166">`dotnet-sdk-[major].[minor]`: 特定のランタイム用に最新の sdk をインストールします</span><span class="sxs-lookup"><span data-stu-id="b9cab-166">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="b9cab-167">**バージョン:** \<sdk version></span><span class="sxs-lookup"><span data-stu-id="b9cab-167">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="b9cab-168">**例:** dotnet-sdk-2.1</span><span class="sxs-lookup"><span data-stu-id="b9cab-168">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="b9cab-169">**内容:** (3),(4)</span><span class="sxs-lookup"><span data-stu-id="b9cab-169">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="b9cab-170">**依存関係:** `dotnet-runtime-[major].[minor]`、`aspnetcore-runtime-[major].[minor]`、`dotnet-targeting-pack-[major].[minor]`、`aspnetcore-targeting-pack-[major].[minor]`、`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`、`dotnet-apphost-pack-[major].[minor]`、`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="b9cab-170">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="b9cab-171">`aspnetcore-runtime-[major].[minor]`: 特定の ASP.NET Core ランタイムをインストールします</span><span class="sxs-lookup"><span data-stu-id="b9cab-171">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="b9cab-172">**バージョン:** \<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="b9cab-172">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="b9cab-173">**例:** aspnetcore-runtime-2.1</span><span class="sxs-lookup"><span data-stu-id="b9cab-173">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="b9cab-174">**内容:** (6)</span><span class="sxs-lookup"><span data-stu-id="b9cab-174">**Contains:** (6)</span></span>
  - <span data-ttu-id="b9cab-175">**依存関係:** `dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="b9cab-175">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="b9cab-176">`dotnet-runtime-deps-[major].[minor]` _(省略可能)_ : 自己完結型アプリケーションを実行する依存関係をインストールします</span><span class="sxs-lookup"><span data-stu-id="b9cab-176">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="b9cab-177">**バージョン:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="b9cab-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b9cab-178">**例:** dotnet-runtime-deps-2.1</span><span class="sxs-lookup"><span data-stu-id="b9cab-178">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="b9cab-179">**依存関係:** _ディストリビューション固有の依存関係_</span><span class="sxs-lookup"><span data-stu-id="b9cab-179">**Dependencies:** _distribution-specific dependencies_</span></span>

- <span data-ttu-id="b9cab-180">`dotnet-runtime-[major].[minor]`: 特定のランタイムをインストールします</span><span class="sxs-lookup"><span data-stu-id="b9cab-180">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="b9cab-181">**バージョン:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="b9cab-181">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b9cab-182">**例:** dotnet-runtime-2.1</span><span class="sxs-lookup"><span data-stu-id="b9cab-182">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="b9cab-183">**内容:** (5)</span><span class="sxs-lookup"><span data-stu-id="b9cab-183">**Contains:** (5)</span></span>
  - <span data-ttu-id="b9cab-184">**依存関係:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="b9cab-184">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="b9cab-185">`dotnet-hostfxr-[major].[minor]`: 依存関係</span><span class="sxs-lookup"><span data-stu-id="b9cab-185">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="b9cab-186">**バージョン:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="b9cab-186">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b9cab-187">**例:**  dotnet-hostfxr-3.0</span><span class="sxs-lookup"><span data-stu-id="b9cab-187">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="b9cab-188">**内容:** (2)</span><span class="sxs-lookup"><span data-stu-id="b9cab-188">**Contains:** (2)</span></span>
  - <span data-ttu-id="b9cab-189">**依存関係:** `dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="b9cab-189">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="b9cab-190">`dotnet-host`: 依存関係</span><span class="sxs-lookup"><span data-stu-id="b9cab-190">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="b9cab-191">**バージョン:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="b9cab-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b9cab-192">**例:** dotnet-host</span><span class="sxs-lookup"><span data-stu-id="b9cab-192">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="b9cab-193">**内容:** (1)、(8)、(9)、(10)、(16)</span><span class="sxs-lookup"><span data-stu-id="b9cab-193">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="b9cab-194">`dotnet-apphost-pack-[major].[minor]`: 依存関係</span><span class="sxs-lookup"><span data-stu-id="b9cab-194">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="b9cab-195">**バージョン:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="b9cab-195">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b9cab-196">**内容:** (13)</span><span class="sxs-lookup"><span data-stu-id="b9cab-196">**Contains:** (13)</span></span>

- <span data-ttu-id="b9cab-197">`dotnet-targeting-pack-[major].[minor]`: 最新ではないランタイムを対象にできます</span><span class="sxs-lookup"><span data-stu-id="b9cab-197">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="b9cab-198">**バージョン:** \<runtime version></span><span class="sxs-lookup"><span data-stu-id="b9cab-198">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b9cab-199">**内容:** (12)</span><span class="sxs-lookup"><span data-stu-id="b9cab-199">**Contains:** (12)</span></span>

- <span data-ttu-id="b9cab-200">`aspnetcore-targeting-pack-[major].[minor]`: 最新ではないランタイムを対象にできます</span><span class="sxs-lookup"><span data-stu-id="b9cab-200">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="b9cab-201">**バージョン:** \<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="b9cab-201">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="b9cab-202">**内容:** (11)</span><span class="sxs-lookup"><span data-stu-id="b9cab-202">**Contains:** (11)</span></span>

- <span data-ttu-id="b9cab-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`: netstandard バージョンを対象にできます</span><span class="sxs-lookup"><span data-stu-id="b9cab-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="b9cab-204">**バージョン:** \<sdk version></span><span class="sxs-lookup"><span data-stu-id="b9cab-204">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="b9cab-205">**内容:** (15)</span><span class="sxs-lookup"><span data-stu-id="b9cab-205">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="b9cab-206">**バージョン:** \<sdk version></span><span class="sxs-lookup"><span data-stu-id="b9cab-206">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="b9cab-207">**内容:** (15)</span><span class="sxs-lookup"><span data-stu-id="b9cab-207">**Contains:** (15)</span></span>

<span data-ttu-id="b9cab-208">`dotnet-runtime-deps-[major].[minor]` では、_ディストリビューション固有の依存関係_ を理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9cab-208">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="b9cab-209">ディストリビューションのビルド システムは、これを自動的に得ることができる可能性があるため、このパッケージは省略可能です。これらの場合、これらの依存関係は `dotnet-runtime-[major].[minor]` パッケージに直接追加されます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-209">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="b9cab-210">パッケージの内容がバージョン付きフォルダーにある場合、`[major].[minor]` のパッケージ名はバージョン付きのフォルダー名と同じになります。</span><span class="sxs-lookup"><span data-stu-id="b9cab-210">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="b9cab-211">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` を除くすべてのパッケージでは、これは .NET バージョンとも同じになります。</span><span class="sxs-lookup"><span data-stu-id="b9cab-211">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET version.</span></span>

<span data-ttu-id="b9cab-212">パッケージ間の依存関係では、バージョン要件 _以上_ を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9cab-212">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="b9cab-213">たとえば、`dotnet-sdk-2.2:2.2.401` には `aspnetcore-runtime-2.2 >= 2.2.6` が必要です。</span><span class="sxs-lookup"><span data-stu-id="b9cab-213">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="b9cab-214">これにより、ユーザーはルート パッケージ (たとえば、`dnf update dotnet-sdk-2.2`) を使用してインストールをアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-214">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="b9cab-215">ほとんどのディストリビューションで、ソースからビルドするすべての成果物を必要とします。</span><span class="sxs-lookup"><span data-stu-id="b9cab-215">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="b9cab-216">これはパッケージにいくつかの影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-216">This has some impact on the packages:</span></span>

- <span data-ttu-id="b9cab-217">`shared/Microsoft.AspNetCore.All` の下にあるサードパーティ製ライブラリは、ソースから簡単にビルドできません。</span><span class="sxs-lookup"><span data-stu-id="b9cab-217">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="b9cab-218">そのため、そのフォルダーは `aspnetcore-runtime` パッケージから除外されます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-218">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="b9cab-219">`NuGetFallbackFolder` は `nuget.org` からバイナリ成果物を利用して入力されます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-219">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="b9cab-220">空のままにしてください。</span><span class="sxs-lookup"><span data-stu-id="b9cab-220">It should remain empty.</span></span>

<span data-ttu-id="b9cab-221">複数の `dotnet-sdk` パッケージで `NuGetFallbackFolder` に同じファイルが提供されることがあります。</span><span class="sxs-lookup"><span data-stu-id="b9cab-221">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="b9cab-222">パッケージ マネージャーの問題を回避するには、これらのファイルを同じにします (チェックサム、変更日など)。</span><span class="sxs-lookup"><span data-stu-id="b9cab-222">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="b9cab-223">パッケージをビルドする</span><span class="sxs-lookup"><span data-stu-id="b9cab-223">Building packages</span></span>

<span data-ttu-id="b9cab-224">[dotnet/source-build](https://github.com/dotnet/source-build) リポジトリでは、.NET SDK のソース ターボールとそのすべてのコンポーネントをビルドする方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="b9cab-224">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET SDK and all its components.</span></span> <span data-ttu-id="b9cab-225">この source-build リポジトリの出力は、この記事の最初のセクションで説明したレイアウトに一致します。</span><span class="sxs-lookup"><span data-stu-id="b9cab-225">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
