---
title: 単一ファイル アプリケーション
description: 単一ファイル アプリケーションの概要、およびこのアプリケーション デプロイ モデルの使用を検討すべき理由について説明します。
author: lakshanf
ms.author: lakshanf
ms.date: 12/17/2020
ms.openlocfilehash: 10ffc947f6a3adcf2889a03edd2616007ce236f3
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536139"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="5cac4-103">単一ファイルの配置と実行可能ファイル</span><span class="sxs-lookup"><span data-stu-id="5cac4-103">Single file deployment and executable</span></span>

<span data-ttu-id="5cac4-104">アプリケーションに依存するすべてのファイルを単一のバイナリにバンドルすることで、アプリケーション開発者は、アプリケーションを単一ファイルとして配置し、配布することができます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="5cac4-105">このデプロイ モデルは、.NET Core 3.0 以降で利用可能であり、.NET 5.0 で拡張されています。</span><span class="sxs-lookup"><span data-stu-id="5cac4-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="5cac4-106">以前の .NET Core 3.0 では、ユーザーが単一ファイル アプリを実行する場合、そのアプリケーションが実行される前に、まず .NET Core ホストがすべてのファイルを一時ディレクトリに抽出します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="5cac4-107">.NET 5.0 では、アプリからファイルを抽出する必要がなく、コードを直接実行するので、このエクスペリエンスが向上しています。</span><span class="sxs-lookup"><span data-stu-id="5cac4-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="5cac4-108">[フレームワークに依存するデプロイ モデル](index.md#publish-framework-dependent)と[自己完結型アプリケーション](index.md#publish-self-contained)の両方で、単一ファイルの配置が可能です。</span><span class="sxs-lookup"><span data-stu-id="5cac4-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="5cac4-109">自己完結型アプリケーション内にある単一ファイルは、ランタイム ライブラリとフレームワーク ライブラリが含まれるため、大きなサイズとなります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="5cac4-110">単一ファイル配置オプションは、[ReadyToRun](ready-to-run.md) と [Trim (.NET 5.0 の試験的な機能)](trim-self-contained.md) の各発行オプションと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-110">The single file deployment option can be combined with [ReadyToRun](ready-to-run.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

## <a name="api-incompatibility"></a><span data-ttu-id="5cac4-111">API の非互換性</span><span class="sxs-lookup"><span data-stu-id="5cac4-111">API incompatibility</span></span>

<span data-ttu-id="5cac4-112">一部の API は、単一ファイルの配置と互換性がありません。また、これらの API を使用する場合、アプリケーションで変更が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-112">Some APIs are not compatible with single-file deployment and applications may require modification if they use these APIs.</span></span> <span data-ttu-id="5cac4-113">サードパーティのフレームワークまたはパッケージを使用する場合、それらでこれらの API のいずれかが使用されていて、変更が必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-113">If you use a third-party framework or package, it's possible that they may also use one of these APIs and need modification.</span></span> <span data-ttu-id="5cac4-114">問題の最も一般的な原因は、アプリケーションに付属するファイルまたは DLL のファイル パスに依存していることです。</span><span class="sxs-lookup"><span data-stu-id="5cac4-114">The most common cause of problems is dependence on file paths for files or DLLs shipped with the application.</span></span>

<span data-ttu-id="5cac4-115">次の表では、単一ファイルの使用に関連するランタイム ライブラリ API の詳細を示します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-115">The table below has the relevant runtime library API details for single-file use.</span></span>

| <span data-ttu-id="5cac4-116">API</span><span class="sxs-lookup"><span data-stu-id="5cac4-116">API</span></span>                            | <span data-ttu-id="5cac4-117">Note</span><span class="sxs-lookup"><span data-stu-id="5cac4-117">Note</span></span>                                                                   |
|--------------------------------|------------------------------------------------------------------------|
| `Assembly.Location`            | <span data-ttu-id="5cac4-118">空の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-118">Returns an empty string.</span></span>                                               |
| `Module.FullyQualifiedName`    | <span data-ttu-id="5cac4-119">値が `<Unknown>` である文字列が返されるか、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-119">Returns a string with the value of `<Unknown>` or throws an exception.</span></span> |
| `Module.Name`                  | <span data-ttu-id="5cac4-120">値が `<Unknown>` である文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-120">Returns a string with the value of `<Unknown>`.</span></span>                        |
| `Assembly.GetFile`             | <span data-ttu-id="5cac4-121"><xref:System.IO.IOException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="5cac4-121">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.GetFiles`            | <span data-ttu-id="5cac4-122"><xref:System.IO.IOException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="5cac4-122">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.CodeBase`            | <span data-ttu-id="5cac4-123"><xref:System.PlatformNotSupportedException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="5cac4-123">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `Assembly.EscapedCodeBase`     | <span data-ttu-id="5cac4-124"><xref:System.PlatformNotSupportedException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="5cac4-124">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `AssemblyName.CodeBase`        | <span data-ttu-id="5cac4-125">`null` を返します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-125">Returns `null`.</span></span>                                                        |
| `AssemblyName.EscapedCodeBase` | <span data-ttu-id="5cac4-126">`null` を返します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-126">Returns `null`.</span></span>                                                        |

<span data-ttu-id="5cac4-127">一般的なシナリオを修正するための推奨事項がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-127">We have some recommendations for fixing common scenarios:</span></span>

* <span data-ttu-id="5cac4-128">実行可能ファイルの隣にあるファイルにアクセスするには、<xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-128">To access files next to the executable, use <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="5cac4-129">実行可能ファイルのファイル名を検索するには、<xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType> の最初の要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-129">To find the file name of the executable, use the first element of <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="5cac4-130">Loose ファイルが完全に配布されないようにするには、[埋め込みリソース](../../framework/resources/creating-resource-files-for-desktop-apps.md)を使用することを検討します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-130">To avoid shipping loose files entirely, consider using [embedded resources](../../framework/resources/creating-resource-files-for-desktop-apps.md).</span></span>

## <a name="attaching-a-debugger"></a><span data-ttu-id="5cac4-131">デバッガーのアタッチ</span><span class="sxs-lookup"><span data-stu-id="5cac4-131">Attaching a debugger</span></span>

<span data-ttu-id="5cac4-132">Linux では、自己完結型の単一ファイル プロセスにアタッチしたり、クラッシュ ダンプをデバッグしたりできる唯一のデバッガーは、[LLDB を使用する SOS](../diagnostics/dotnet-sos.md) です。</span><span class="sxs-lookup"><span data-stu-id="5cac4-132">On Linux, the only debugger which can attach to self-contained single-file processes or debug crash dumps is [SOS with LLDB](../diagnostics/dotnet-sos.md).</span></span>

<span data-ttu-id="5cac4-133">Windows と Mac では、Visual Studio と VS Code を使用してクラッシュ ダンプをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-133">On Windows and Mac, Visual Studio and VS Code can be used to debug crash dumps.</span></span> <span data-ttu-id="5cac4-134">実行中の自己完結型単一ファイルの実行可能ファイルにアタッチするには、余分なファイル _mscordbi.{dll,so}_ が必要です。</span><span class="sxs-lookup"><span data-stu-id="5cac4-134">Attaching to a running self-contained single-file executable requires an extra file: _mscordbi.{dll,so}_.</span></span>

<span data-ttu-id="5cac4-135">このファイルがないと、Visual Studio で次のエラーが発生することがあります: "プロセスにアタッチできません。</span><span class="sxs-lookup"><span data-stu-id="5cac4-135">Without this file Visual Studio may produce the error "Unable to attach to the process.</span></span> <span data-ttu-id="5cac4-136">デバッグ コンポーネントはインストールされていません。"</span><span class="sxs-lookup"><span data-stu-id="5cac4-136">A debug component is not installed."</span></span> <span data-ttu-id="5cac4-137">また、VS Code では、次のエラーが発生することがあります: "プロセスにアタッチできませんでした: 不明なエラー: 0x80131c3c。"</span><span class="sxs-lookup"><span data-stu-id="5cac4-137">and VS Code may produce the error "Failed to attach to process: Unknown Error: 0x80131c3c."</span></span>

<span data-ttu-id="5cac4-138">これらのエラーを修正するには、実行可能ファイルの隣に _mscordbi_ をコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-138">To fix these errors, _mscordbi_ needs to be copied next to the executable.</span></span> <span data-ttu-id="5cac4-139">_mscordbi_ は、既定では、アプリケーションのランタイム ID でサブディレクトリに `publish` されます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-139">_mscordbi_ is `publish`ed by default in the subdirectory with the application's runtime ID.</span></span> <span data-ttu-id="5cac4-140">そのため、たとえば、`dotnet` CLI と `-r win-x64` パラメーターを使用して Windows 用に自己完結型単一ファイルの実行可能ファイルを発行する場合、実行可能ファイルは _bin/Debug/net5.0/win-x64/publish_ に配置されます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-140">So, for example, if one were to publish a self-contained single-file executable using the `dotnet` CLI for Windows using the parameters `-r win-x64`, the executable would be placed in _bin/Debug/net5.0/win-x64/publish_.</span></span> <span data-ttu-id="5cac4-141">_mscordbi.dll_ のコピーは _bin/Debug/net5.0/win-x64_ にあります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-141">A copy of _mscordbi.dll_ would be present in _bin/Debug/net5.0/win-x64_.</span></span>

## <a name="other-considerations"></a><span data-ttu-id="5cac4-142">その他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="5cac4-142">Other considerations</span></span>

<span data-ttu-id="5cac4-143">既定では、単一ファイルを使用してネイティブ ライブラリをバンドルすることができません。</span><span class="sxs-lookup"><span data-stu-id="5cac4-143">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="5cac4-144">Linux では、ランタイム ライブラリをバンドルに事前にリンクして、アプリケーション ネイティブ ライブラリのみを単一ファイル アプリと同じディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-144">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="5cac4-145">Windows では、ホスト コードのみを事前にリンクして、ランタイム ライブラリとアプリケーション ネイティブ ライブラリの両方を単一ファイル アプリと同じディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-145">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="5cac4-146">これにより、優れたデバッグ エクスペリエンスが確保されます。それには、ネイティブ ファイルを単一ファイルから除外する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-146">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="5cac4-147">単一ファイル バンドルにネイティブ ライブラリを含めるようにフラグ `IncludeNativeLibrariesForSelfExtract` を設定するオプションがありますが、これらのファイルは、単一ファイル アプリケーションが実行されるときに、クライアント コンピューターの一時ディレクトリに抽出されます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-147">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

<span data-ttu-id="5cac4-148">`IncludeAllContentForSelfExtract` を指定すると、実行可能ファイルを実行する前にすべてのファイルが抽出されます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-148">Specifying `IncludeAllContentForSelfExtract` will extract all files before running the executable.</span></span> <span data-ttu-id="5cac4-149">これにより、元の .NET Core の単一ファイル展開動作が保持されます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-149">This preserves the original .NET Core single-file deployment behavior.</span></span>

<span data-ttu-id="5cac4-150">単一ファイル アプリケーションでは、関連するすべての PDB ファイルは隣に配置され、既定ではバンドルされません。</span><span class="sxs-lookup"><span data-stu-id="5cac4-150">Single-file application will have all related PDB files alongside it and will not be bundled by default.</span></span> <span data-ttu-id="5cac4-151">ビルドするプロジェクトのアセンブリ内に PDB を含めるには、[以下](#include-pdb-files-inside-the-bundle)で詳しく説明するように、`DebugType` を `embedded` に設定します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-151">If you want to include PDBs inside the assembly for projects you build, set the `DebugType` to `embedded` as described [below](#include-pdb-files-inside-the-bundle) in detail.</span></span>

<span data-ttu-id="5cac4-152">マネージド C++ コンポーネントは、単一ファイルの配置には適していません。単一ファイルとの互換性を確保するには、アプリケーションを C# または別の非マネージド C++ 言語で記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5cac4-152">Managed C++ components aren't well suited for single-file deployment and we recommend that you write applications in C# or another non-managed C++ language to be single-file compatible.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="5cac4-153">ファイルを埋め込み対象から除外する</span><span class="sxs-lookup"><span data-stu-id="5cac4-153">Exclude files from being embedded</span></span>

<span data-ttu-id="5cac4-154">次のメタデータを設定すると、特定のファイルを単一ファイルの埋め込み対象から明示的に除外することができます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-154">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="5cac4-155">たとえば、いくつかのファイルを発行ディレクトリに配置するものの、単一ファイルへのバンドルは行わない場合などです。</span><span class="sxs-lookup"><span data-stu-id="5cac4-155">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="include-pdb-files-inside-the-bundle"></a><span data-ttu-id="5cac4-156">バンドル内に PDB ファイルを含める</span><span class="sxs-lookup"><span data-stu-id="5cac4-156">Include PDB files inside the bundle</span></span>

<span data-ttu-id="5cac4-157">アセンブリの PDB ファイルは、次の設定を使用して、アセンブリ自体 (`.dll`) に埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-157">The PDB file for an assembly can be embedded into the assembly itself (the `.dll`) using the setting below.</span></span> <span data-ttu-id="5cac4-158">シンボルはアセンブリの一部であるため、単一ファイル アプリケーションの一部にもなります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-158">Since the symbols are part of the assembly, they will be part of the single-file application as well:</span></span>

```xml
<DebugType>embedded</DebugType>
```

<span data-ttu-id="5cac4-159">たとえば、アセンブリに PDB ファイルを埋め込むには、そのアセンブリのプロジェクト ファイルに次のプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-159">For example, add the following property to the project file of an assembly to embed the PDB file to that assembly:</span></span>

```xml
<PropertyGroup>
  <DebugType>embedded</DebugType>
</PropertyGroup>
```

## <a name="publish-a-single-file-app---sample-project-file"></a><span data-ttu-id="5cac4-160">単一のファイル アプリを発行する - サンプル プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="5cac4-160">Publish a single file app - sample project file</span></span>

<span data-ttu-id="5cac4-161">単一ファイルの発行を指定するサンプル プロジェクト ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-161">Here's a sample project file that specifies single-file publishing:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <PublishSingleFile>true</PublishSingleFile>
    <SelfContained>true</SelfContained>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <PublishReadyToRun>true</PublishReadyToRun>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="5cac4-162">これらのプロパティには、次の関数があります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-162">These properties have the following functions:</span></span>

* <span data-ttu-id="5cac4-163">`PublishSingleFile` - 単一ファイルの発行を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5cac4-163">`PublishSingleFile` - Enables single-file publishing.</span></span>
* <span data-ttu-id="5cac4-164">`SelfContained` - アプリが自己完結型またはフレームワーク依存であるかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-164">`SelfContained` - Determines whether the app will be self-contained or framework-dependent.</span></span>
* <span data-ttu-id="5cac4-165">`RuntimeIdentifier` - ターゲットとする [OS と CPU の種類](../rid-catalog.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-165">`RuntimeIdentifier` - Specifies the [OS and CPU type](../rid-catalog.md) you are targeting.</span></span>
* <span data-ttu-id="5cac4-166">`PublishTrimmed` - 自己完結型アプリでのみサポートされている[アセンブリのトリミング](trim-self-contained.md)の使用を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5cac4-166">`PublishTrimmed` - Enables use of [assembly trimming](trim-self-contained.md), which is only supported for self-contained apps.</span></span>
* <span data-ttu-id="5cac4-167">`PublishReadyToRun` - [Ahead-Of-Time (AOT) コンパイル](ready-to-run.md)を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5cac4-167">`PublishReadyToRun` - Enables [ahead-of-time (AOT) compilation](ready-to-run.md).</span></span>

<span data-ttu-id="5cac4-168">**注:**</span><span class="sxs-lookup"><span data-stu-id="5cac4-168">**Notes:**</span></span>

* <span data-ttu-id="5cac4-169">アプリは OS とアーキテクチャに固有のものです。</span><span class="sxs-lookup"><span data-stu-id="5cac4-169">Apps are OS and architecture-specific.</span></span> <span data-ttu-id="5cac4-170">Linux x64、Linux ARM64、Windows x64 など、構成ごとに発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-170">You need to publish for each configuration, such as Linux x64, Linux ARM64, Windows x64, and so forth.</span></span>
* <span data-ttu-id="5cac4-171">構成ファイル ( *\*.runtimeconfig.json* など) は、単一ファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="5cac4-171">Configuration files, such as *\*.runtimeconfig.json*, are included in the single file.</span></span> <span data-ttu-id="5cac4-172">追加の構成ファイルが必要な場合は、その単一ファイルの横に配置することができます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-172">If an additional configuration file is needed, you can place it beside the single file.</span></span>

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="5cac4-173">単一ファイル アプリを発行する - CLI</span><span class="sxs-lookup"><span data-stu-id="5cac4-173">Publish a single file app - CLI</span></span>

<span data-ttu-id="5cac4-174">[dotnet publish](../tools/dotnet-publish.md) コマンドを使用して、単一ファイル アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-174">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="5cac4-175">アプリを発行する場合、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-175">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="5cac4-176">特定のランタイムに対して発行する: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="5cac4-176">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="5cac4-177">単一ファイルとして発行する: `-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="5cac4-177">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="5cac4-178">次の例では、Windows 用のアプリを自己完結型の単一ファイル アプリケーションとして発行します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-178">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="5cac4-179">次の例では、Linux 用のアプリをフレームワークに依存する単一ファイル アプリケーションとして発行します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-179">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="5cac4-180">詳細については、「[.NET Core CLI を使用して .NET Core アプリを発行する](deploy-with-cli.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cac4-180">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="5cac4-181">単一ファイル アプリを発行する - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5cac4-181">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="5cac4-182">Visual Studio を使用すると、アプリケーションの発行方法を制御する再利用可能な発行プロファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5cac4-182">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="5cac4-183">**[ソリューション エクスプローラー]** ペインで、発行するプロジェクトを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="5cac4-183">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="5cac4-184">**[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-184">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="右クリック メニューの [発行] オプションが強調表示されたソリューション エクスプローラー。":::

    <span data-ttu-id="5cac4-186">発行プロファイルがまだない場合は、指示に従って作成し、ターゲットの種類として **[フォルダー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-186">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="5cac4-187">**[編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-187">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Visual Studio の発行プロファイルと [編集] ボタン":::

01. <span data-ttu-id="5cac4-189">**[プロファイル設定]** ダイアログで、次のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-189">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="5cac4-190">**[配置モード]** を **[自己完結]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-190">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="5cac4-191">**[ターゲット ランタイム]** を発行先のプラットフォームに設定します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-191">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="5cac4-192">**[単一ファイルの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-192">Select **Produce single file**.</span></span>

    <span data-ttu-id="5cac4-193">**[保存]** を選択して設定を保存し、 **[発行]** ダイアログに戻ります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-193">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="[配置モード]、[ターゲット ランタイム]、[単一ファイルの作成] の各オプションが強調表示されている [プロファイル設定] ダイアログ。":::

01. <span data-ttu-id="5cac4-195">**[発行]** を選択して、アプリを単一ファイルとして発行します。</span><span class="sxs-lookup"><span data-stu-id="5cac4-195">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="5cac4-196">詳細については、[Visual Studio を使用した .NET Core アプリの発行](deploy-with-vs.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cac4-196">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="5cac4-197">単一ファイル アプリを発行する - Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="5cac4-197">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="5cac4-198">Visual Studio for Mac には、アプリを単一ファイルとして発行するためのオプションがありません。</span><span class="sxs-lookup"><span data-stu-id="5cac4-198">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="5cac4-199">「[単一ファイル アプリを発行する - CLI](#publish-a-single-file-app---cli)」セクションの手順に従って、手動で発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5cac4-199">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="5cac4-200">詳細については、「[.NET Core CLI を使用して .NET Core アプリを発行する](deploy-with-cli.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cac4-200">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5cac4-201">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cac4-201">See also</span></span>

- <span data-ttu-id="5cac4-202">[.NET Core アプリケーションの配置](index.md)。</span><span class="sxs-lookup"><span data-stu-id="5cac4-202">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="5cac4-203">[.NET Core CLI を使用して .NET Core アプリを発行する](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="5cac4-203">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="5cac4-204">[Visual Studio を使用して .NET Core アプリを発行する](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="5cac4-204">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="5cac4-205">[`dotnet publish` コマンド](../tools/dotnet-publish.md)。</span><span class="sxs-lookup"><span data-stu-id="5cac4-205">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
