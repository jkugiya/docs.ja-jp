---
title: カスタム .NET Core ランタイム ホストを作成する
description: .NET Core ランタイムの動作を制御する必要がある高度なシナリオをサポートするために、ネイティブ コードから .NET Core ランタイムをホストする方法について説明します。
author: mjrousos
ms.topic: how-to
ms.date: 12/21/2018
ms.openlocfilehash: a05e1e1d09f1f988ad8354f98521681e3f6cbea8
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875851"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a><span data-ttu-id="b2364-103">ネイティブ コードから .NET ランタイムを制御するカスタム .NET Core ホストを作成する</span><span class="sxs-lookup"><span data-stu-id="b2364-103">Write a custom .NET Core host to control the .NET runtime from your native code</span></span>

<span data-ttu-id="b2364-104">あらゆるマネージド コードと同様に、.NET Core アプリケーションはホストにより実行されます。</span><span class="sxs-lookup"><span data-stu-id="b2364-104">Like all managed code, .NET Core applications are executed by a host.</span></span> <span data-ttu-id="b2364-105">ホストは、ランタイム (JIT やガベージ コレクターのようなコンポーネントを含む) の開始、マネージド エントリ ポイントの呼び出しを担当します。</span><span class="sxs-lookup"><span data-stu-id="b2364-105">The host is responsible for starting the runtime (including components like the JIT and garbage collector) and invoking managed entry points.</span></span>

<span data-ttu-id="b2364-106">.NET Core ランタイムのホスティングは高度なシナリオです。ほとんどの場合、.NET Core 開発者はホスティングについて心配する必要がありません。 .NET Core ビルド プロセスが .NET Core アプリケーションを実行するための既定ホストを提供するためです。</span><span class="sxs-lookup"><span data-stu-id="b2364-106">Hosting the .NET Core runtime is an advanced scenario and, in most cases, .NET Core developers don't need to worry about hosting because .NET Core build processes provide a default host to run .NET Core applications.</span></span> <span data-ttu-id="b2364-107">ただし、特別な状況で、ネイティブ プロセスのマネージド コードを呼び出す手段として、あるいはランタイムの動作をさらに細かくコントロールする目的で .NET Core ランタイムを明示的にホスティングすると効果的な場合があります。</span><span class="sxs-lookup"><span data-stu-id="b2364-107">In some specialized circumstances, though, it can be useful to explicitly host the .NET Core runtime, either as a means of invoking managed code in a native process or in order to gain more control over how the runtime works.</span></span>

<span data-ttu-id="b2364-108">この記事では、ネイティブ コードから .NET Core ランタイムを開始し、その中でマネージド コードを実行するために必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2364-108">This article gives an overview of the steps necessary to start the .NET Core runtime from native code and execute managed code in it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2364-109">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b2364-109">Prerequisites</span></span>

<span data-ttu-id="b2364-110">ホストはネイティブ アプリケーションであるため、このチュートリアルでは、C++ アプリケーションを構築して .NET Core をホスティングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2364-110">Because hosts are native applications, this tutorial covers constructing a C++ application to host .NET Core.</span></span> <span data-ttu-id="b2364-111">C++ 開発環境が必要になります ([Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) に付属のものなど)。</span><span class="sxs-lookup"><span data-stu-id="b2364-111">You will need a C++ development environment (such as that provided by [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).</span></span>

<span data-ttu-id="b2364-112">ホストをテストするための単純な .NET Core アプリケーションも必要です。そのため、[.NET Core SDK](https://dotnet.microsoft.com/download) をインストールし、[小さい .NET Core テスト アプリを作成](with-visual-studio.md)してください ('Hello World' アプリなど)。</span><span class="sxs-lookup"><span data-stu-id="b2364-112">You will also want a simple .NET Core application to test the host with, so you should install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [build a small .NET Core test app](with-visual-studio.md) (such as a 'Hello World' app).</span></span> <span data-ttu-id="b2364-113">新しい .NET Core コンソール プロジェクト テンプレートで作成される 'Hello World' アプリで十分です。</span><span class="sxs-lookup"><span data-stu-id="b2364-113">The 'Hello World' app created by the new .NET Core console project template is sufficient.</span></span>

## <a name="hosting-apis"></a><span data-ttu-id="b2364-114">ホスト API</span><span class="sxs-lookup"><span data-stu-id="b2364-114">Hosting APIs</span></span>

<span data-ttu-id="b2364-115">.NET Core をホストするために使用できる API が 2 種類あります。</span><span class="sxs-lookup"><span data-stu-id="b2364-115">There are two different APIs that can be used to host .NET Core.</span></span> <span data-ttu-id="b2364-116">この記事 (とそれに関連する[サンプル](https://github.com/dotnet/samples/tree/main/core/hosting)) では、これら 2 つのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b2364-116">This article (and its associated [samples](https://github.com/dotnet/samples/tree/main/core/hosting)) covers these 2 options.</span></span>

* <span data-ttu-id="b2364-117">.NET Core 3.0 以降の .NET Core ランタイムをホストする推奨される方法は、`nethost` および `hostfxr` ライブラリの API を使うことです。</span><span class="sxs-lookup"><span data-stu-id="b2364-117">The preferred method of hosting the .NET Core runtime in .NET Core 3.0 and above is with the `nethost` and `hostfxr` libraries' APIs.</span></span> <span data-ttu-id="b2364-118">これらのエントリ ポイントは、初期化のためにランタイムを検索して設定する複雑な処理が行われ、マネージド アプリケーションの起動と静的マネージド メソッドの呼び出しの両方が可能です。</span><span class="sxs-lookup"><span data-stu-id="b2364-118">These entry points handle the complexity of finding and setting up the runtime for initialization and allow both launching a managed application and calling into a static managed method.</span></span>
* <span data-ttu-id="b2364-119">.NET Core 3.0 より前の .NET Core ランタイムをホストする推奨される方法は、[`coreclrhost.h`](https://github.com/dotnet/runtime/blob/main/src/coreclr/hosts/inc/coreclrhost.h) API を使うことです。</span><span class="sxs-lookup"><span data-stu-id="b2364-119">The preferred method of hosting the .NET Core runtime prior to .NET Core 3.0 is with the [`coreclrhost.h`](https://github.com/dotnet/runtime/blob/main/src/coreclr/hosts/inc/coreclrhost.h) API.</span></span> <span data-ttu-id="b2364-120">この API では、ランタイムを簡単に開始および停止し、(マネージド exe を起動するか、静的マネージド メソッドを呼び出すことで) マネージド コードを呼び出すために関数が公開されます。</span><span class="sxs-lookup"><span data-stu-id="b2364-120">This API exposes functions for easily starting and stopping the runtime and invoking managed code (either by launching a managed exe or by calling static managed methods).</span></span>

## <a name="sample-hosts"></a><span data-ttu-id="b2364-121">サンプル ホスト</span><span class="sxs-lookup"><span data-stu-id="b2364-121">Sample Hosts</span></span>

<span data-ttu-id="b2364-122">dotnet/samples GitHub リポジトリには、以下のチュートリアルで説明する手順を実演する[サンプル ホスト](https://github.com/dotnet/samples/tree/main/core/hosting)があります。</span><span class="sxs-lookup"><span data-stu-id="b2364-122">[Sample hosts](https://github.com/dotnet/samples/tree/main/core/hosting) demonstrating the steps outlined in the tutorials below are available in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="b2364-123">サンプルのコメントを見れば、これらのチュートリアルで番号が付けられている手順がサンプルのどこで実行されるかわかります。</span><span class="sxs-lookup"><span data-stu-id="b2364-123">Comments in the samples clearly associate the numbered steps from these tutorials with where they're performed in the sample.</span></span> <span data-ttu-id="b2364-124">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2364-124">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

<span data-ttu-id="b2364-125">サンプル ホストは学習目的のために利用されるものです。エラーのチェック時に軽くなっており、効率性より読みやすさを重視して設計されています。</span><span class="sxs-lookup"><span data-stu-id="b2364-125">Keep in mind that the sample hosts are meant to be used for learning purposes, so they are light on error checking and are designed to emphasize readability over efficiency.</span></span>

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a><span data-ttu-id="b2364-126">`nethost.h` と `hostfxr.h` を使用してホストを作成する</span><span class="sxs-lookup"><span data-stu-id="b2364-126">Create a host using `nethost.h` and `hostfxr.h`</span></span>

<span data-ttu-id="b2364-127">以下は、`nethost` および `hostfxr` ライブラリを使用してネイティブ アプリケーションで .NET Core ランタイムを起動し、静的マネージド メソッドを呼び出す手順を詳しくまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="b2364-127">The following steps detail how to use the `nethost` and `hostfxr` libraries to start the .NET Core runtime in a native application and call into a managed static method.</span></span> <span data-ttu-id="b2364-128">[サンプル](https://github.com/dotnet/samples/tree/main/core/hosting/HostWithHostFxr)では、.NET SDK でインストールされる `nethost` ヘッダーとライブラリ、および [dotnet/runtime](https://github.com/dotnet/runtime) リポジトリからの [`coreclr_delegates.h`](https://github.com/dotnet/runtime/blob/main/src/native/corehost/coreclr_delegates.h) および [`hostfxr.h`](https://github.com/dotnet/runtime/blob/main/src/native/corehost/hostfxr.h) ファイルのコピーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2364-128">The [sample](https://github.com/dotnet/samples/tree/main/core/hosting/HostWithHostFxr) uses the `nethost` header and library installed with the .NET SDK and copies of the [`coreclr_delegates.h`](https://github.com/dotnet/runtime/blob/main/src/native/corehost/coreclr_delegates.h) and [`hostfxr.h`](https://github.com/dotnet/runtime/blob/main/src/native/corehost/hostfxr.h) files from the [dotnet/runtime](https://github.com/dotnet/runtime) repository.</span></span>

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a><span data-ttu-id="b2364-129">ステップ 1 - `hostfxr` を読み込んで、エクスポートされたホスティング関数を取得する</span><span class="sxs-lookup"><span data-stu-id="b2364-129">Step 1 - Load `hostfxr` and get exported hosting functions</span></span>

<span data-ttu-id="b2364-130">`nethost` ライブラリでは、`hostfxr` ライブラリを検索するための `get_hostfxr_path` 関数が提供されています。</span><span class="sxs-lookup"><span data-stu-id="b2364-130">The `nethost` library provides the `get_hostfxr_path` function for locating the `hostfxr` library.</span></span> <span data-ttu-id="b2364-131">`hostfxr` ライブラリでは、.NET Core ランタイムをホストするための関数が公開されています。</span><span class="sxs-lookup"><span data-stu-id="b2364-131">The `hostfxr` library exposes functions for hosting the .NET Core runtime.</span></span> <span data-ttu-id="b2364-132">関数の完全な一覧については、[`hostfxr.h`](https://github.com/dotnet/runtime/blob/main/src/native/corehost/hostfxr.h) および[ネイティブ ホスティング デザインのドキュメント](https://github.com/dotnet/runtime/blob/main/docs/design/features/native-hosting.md)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b2364-132">The full list of functions can be found in [`hostfxr.h`](https://github.com/dotnet/runtime/blob/main/src/native/corehost/hostfxr.h) and the [native hosting design document](https://github.com/dotnet/runtime/blob/main/docs/design/features/native-hosting.md).</span></span> <span data-ttu-id="b2364-133">サンプルとこのチュートリアルでは以下を使います。</span><span class="sxs-lookup"><span data-stu-id="b2364-133">The sample and this tutorial use the following:</span></span>

* <span data-ttu-id="b2364-134">`hostfxr_initialize_for_runtime_config`:ホスト コンテキストを初期化し、指定されたランタイム構成を使って .NET Core ランタイムの初期化を準備します。</span><span class="sxs-lookup"><span data-stu-id="b2364-134">`hostfxr_initialize_for_runtime_config`: Initializes a host context and prepares for initialization of the .NET Core runtime using the specified runtime configuration.</span></span>
* <span data-ttu-id="b2364-135">`hostfxr_get_runtime_delegate`:ランタイム機能に対するデリゲートを取得します。</span><span class="sxs-lookup"><span data-stu-id="b2364-135">`hostfxr_get_runtime_delegate`: Gets a delegate for runtime functionality.</span></span>
* <span data-ttu-id="b2364-136">`hostfxr_close`:ホスト コンテキストを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b2364-136">`hostfxr_close`: Closes a host context.</span></span>

<span data-ttu-id="b2364-137">`hostfxr` ライブラリは、`get_hostfxr_path` を使って検索されます。</span><span class="sxs-lookup"><span data-stu-id="b2364-137">The `hostfxr` library is found using `get_hostfxr_path`.</span></span> <span data-ttu-id="b2364-138">その後、読み込まれて、そのエクスポートが取得されます。</span><span class="sxs-lookup"><span data-stu-id="b2364-138">It is then loaded and its exports are retrieved.</span></span>

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a><span data-ttu-id="b2364-139">ステップ 2 - .NET Core ランタイムを初期化して開始する</span><span class="sxs-lookup"><span data-stu-id="b2364-139">Step 2 - Initialize and start the .NET Core runtime</span></span>

<span data-ttu-id="b2364-140">`hostfxr_initialize_for_runtime_config` および `hostfxr_get_runtime_delegate` 関数では、後で読み込まれるマネージド コンポーネントに対するランタイム構成を使って、.NET Core ランタイムが初期化されて開始されます。</span><span class="sxs-lookup"><span data-stu-id="b2364-140">The `hostfxr_initialize_for_runtime_config` and `hostfxr_get_runtime_delegate` functions initialize and start the .NET Core runtime using the runtime configuration for the managed component that will be loaded.</span></span> <span data-ttu-id="b2364-141">マネージド アセンブリの読み込み、およびそのアセンブリ内の静的メソッドへの関数ポインターの取得を可能にするランタイムのデリゲートを取得するには、`hostfxr_get_runtime_delegate` 関数を使います。</span><span class="sxs-lookup"><span data-stu-id="b2364-141">The `hostfxr_get_runtime_delegate` function is used to get a runtime delegate that allows loading a managed assembly and getting a function pointer to a static method in that assembly.</span></span>

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a><span data-ttu-id="b2364-142">ステップ 3 - マネージド アセンブリを読み込み、マネージド メソッドへの関数ポインターを取得する</span><span class="sxs-lookup"><span data-stu-id="b2364-142">Step 3 - Load managed assembly and get function pointer to a managed method</span></span>

<span data-ttu-id="b2364-143">マネージド アセンブリを読み込んで、マネージド メソッドへの関数ポインターを取得するには、ランタイムのデリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b2364-143">The runtime delegate is called to load the managed assembly and get a function pointer to a managed method.</span></span> <span data-ttu-id="b2364-144">デリゲートでは、入力としてアセンブリのパス、型の名前、およびメソッドの名前が必要であり、マネージド メソッドの呼び出しに使用できる関数ポインターが返されます。</span><span class="sxs-lookup"><span data-stu-id="b2364-144">The delegate requires the assembly path, type name, and method name as inputs and returns a function pointer that can be used to invoke the managed method.</span></span>

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

<span data-ttu-id="b2364-145">ランタイムのデリゲートを呼び出すときにデリゲートの型の名前として `nullptr` を渡すことにより、サンプルではマネージド メソッドに対して既定のシグネチャを使います。</span><span class="sxs-lookup"><span data-stu-id="b2364-145">By passing `nullptr` as the delegate type name when calling the runtime delegate, the sample uses a default signature for the managed method:</span></span>

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

<span data-ttu-id="b2364-146">ランタイムのデリゲートを呼び出すときに、デリゲートの型名を指定することにより、異なるシグネチャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b2364-146">A different signature can be used by specifying the delegate type name when calling the runtime delegate.</span></span>

### <a name="step-4---run-managed-code"></a><span data-ttu-id="b2364-147">ステップ 4 - マネージド コードを実行する</span><span class="sxs-lookup"><span data-stu-id="b2364-147">Step 4 - Run managed code!</span></span>

<span data-ttu-id="b2364-148">ネイティブ ホストでは、マネージド メソッドを呼び出し、目的のパラメーターを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b2364-148">The native host can now call the managed method and pass it the desired parameters.</span></span>

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a><span data-ttu-id="b2364-149">`coreclrhost.h` を使用してホストを作成する</span><span class="sxs-lookup"><span data-stu-id="b2364-149">Create a host using `coreclrhost.h`</span></span>

<span data-ttu-id="b2364-150">以下は、`coreclrhost.h` API を使用してネイティブ アプリケーションで .NET Core ランタイムを起動し、静的マネージド メソッドを呼び出す手順を詳しくまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="b2364-150">The following steps detail how to use the `coreclrhost.h` API to start the .NET Core runtime in a native application and call into a managed static method.</span></span> <span data-ttu-id="b2364-151">このドキュメントのコード スニペットでは Windows 固有の API が使用されてますが、[こちら](https://github.com/dotnet/samples/tree/main/core/hosting/HostWithCoreClrHost)にある完全版サンプル ホストでは、Windows コード パスと Linux コード パスの両方を確認できます。</span><span class="sxs-lookup"><span data-stu-id="b2364-151">The code snippets in this document use some Windows-specific APIs, but the [full sample host](https://github.com/dotnet/samples/tree/main/core/hosting/HostWithCoreClrHost) shows both Windows and Linux code paths.</span></span>

<span data-ttu-id="b2364-152">[corerun ホスト](https://github.com/dotnet/runtime/tree/main/src/coreclr/hosts/corerun)では、`coreclrhost.h` を使ったホスティングの、より複雑で現実的なクロスプラットフォームの例が示されています。</span><span class="sxs-lookup"><span data-stu-id="b2364-152">The [corerun host](https://github.com/dotnet/runtime/tree/main/src/coreclr/hosts/corerun) shows a more complex, real-world, cross-platform example of hosting using `coreclrhost.h`.</span></span>

### <a name="step-1---find-and-load-coreclr"></a><span data-ttu-id="b2364-153">手順 1 - CoreCLR を見つけて読み込む</span><span class="sxs-lookup"><span data-stu-id="b2364-153">Step 1 - Find and load CoreCLR</span></span>

<span data-ttu-id="b2364-154">.NET Core ランタイム API は *coreclr.dll* (Windows の場合)、*libcoreclr.so* (Linux の場合)、*libcoreclr.dylib* (macOS の場合) にあります。</span><span class="sxs-lookup"><span data-stu-id="b2364-154">The .NET Core runtime APIs are in *coreclr.dll* (on Windows), in *libcoreclr.so* (on Linux), or in *libcoreclr.dylib* (on macOS).</span></span> <span data-ttu-id="b2364-155">.NET Core をホストする最初の手順は CoreCLR ライブラリを読み込むことです。</span><span class="sxs-lookup"><span data-stu-id="b2364-155">The first step to hosting .NET Core is to load the CoreCLR library.</span></span> <span data-ttu-id="b2364-156">ホストによってはさまざまなパスを探るか、入力パラメーターを使用してライブラリを見つけるものもあれば、特定のパスから (ホストの隣やコンピューター全体からなど) 読み込むことが認識されているものもあります。</span><span class="sxs-lookup"><span data-stu-id="b2364-156">Some hosts probe different paths or use input parameters to find the library while others know to load it from a certain path (next to the host, for example, or from a machine-wide location).</span></span>

<span data-ttu-id="b2364-157">ライブラリが見つかると、それが `LoadLibraryEx` (Windows の場合) か `dlopen` (Linux/macOS の場合) によって読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="b2364-157">Once found, the library is loaded with `LoadLibraryEx` (on Windows) or `dlopen` (on Linux/macOS).</span></span>

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a><span data-ttu-id="b2364-158">手順 2 - .NET Core をホストする関数を取得する</span><span class="sxs-lookup"><span data-stu-id="b2364-158">Step 2 - Get .NET Core hosting functions</span></span>

<span data-ttu-id="b2364-159">CoreClrHost には、.NET Core をホストするために役立つ重要なメソッドがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="b2364-159">CoreClrHost has several important methods useful for hosting .NET Core:</span></span>

* <span data-ttu-id="b2364-160">`coreclr_initialize`:.NET Core ランタイムを起動し、既定 (で唯一) の AppDomain を設定します。</span><span class="sxs-lookup"><span data-stu-id="b2364-160">`coreclr_initialize`: Starts the .NET Core runtime and sets up the default (and only) AppDomain.</span></span>
* <span data-ttu-id="b2364-161">`coreclr_execute_assembly`:マネージド アセンブリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b2364-161">`coreclr_execute_assembly`: Executes a managed assembly.</span></span>
* <span data-ttu-id="b2364-162">`coreclr_create_delegate`:マネージド メソッドを指す関数ポインターを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2364-162">`coreclr_create_delegate`: Creates a function pointer to a managed method.</span></span>
* <span data-ttu-id="b2364-163">`coreclr_shutdown`:.NET Core ランタイムをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="b2364-163">`coreclr_shutdown`: Shuts down the .NET Core runtime.</span></span>
* <span data-ttu-id="b2364-164">`coreclr_shutdown_2`:`coreclr_shutdown` など。ただし、マネージド コードの終了コードも取得されます。</span><span class="sxs-lookup"><span data-stu-id="b2364-164">`coreclr_shutdown_2`: Like `coreclr_shutdown`, but also retrieves the managed code's exit code.</span></span>

<span data-ttu-id="b2364-165">CoreCLR ライブラリを読み込んだ後、次の手順は、`GetProcAddress` (Windows の場合) または `dlsym` (Linux/macOS の場合) を使用してこれらの関数の参照を取得することです。</span><span class="sxs-lookup"><span data-stu-id="b2364-165">After loading the CoreCLR library, the next step is to get references to these functions using `GetProcAddress` (on Windows) or `dlsym` (on Linux/macOS).</span></span>

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a><span data-ttu-id="b2364-166">手順 3 - ランタイム プロパティを準備する</span><span class="sxs-lookup"><span data-stu-id="b2364-166">Step 3 - Prepare runtime properties</span></span>

<span data-ttu-id="b2364-167">ランタイムを開始する前に、(特に、アセンブリ ローダーに関連して) 動作を指定するいくつかのプロパティを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2364-167">Before starting the runtime, it is necessary to prepare some properties to specify behavior (especially concerning the assembly loader).</span></span>

<span data-ttu-id="b2364-168">共通プロパティには次があります。</span><span class="sxs-lookup"><span data-stu-id="b2364-168">Common properties include:</span></span>

* <span data-ttu-id="b2364-169">`TRUSTED_PLATFORM_ASSEMBLIES` これはランタイムが既定で解決できるアセンブリ パスのリストです (Windows の場合は ';' で、Linux の場合は ':' で区切られます)。</span><span class="sxs-lookup"><span data-stu-id="b2364-169">`TRUSTED_PLATFORM_ASSEMBLIES` This is a list of assembly paths (delimited by ';' on Windows and ':' on Linux) which the runtime will be able to resolve by default.</span></span> <span data-ttu-id="b2364-170">一部のホストでは、アセンブリを一覧表示するマニフェストがハードコードされており、それを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b2364-170">Some hosts have hard-coded manifests listing assemblies they can load.</span></span> <span data-ttu-id="b2364-171">他のホストの場合、このリストにある特定の場所にライブラリが置かれます (*coreclr.dll* の隣など)。</span><span class="sxs-lookup"><span data-stu-id="b2364-171">Others will put any library in certain locations (next to *coreclr.dll*, for example) on this list.</span></span>
* <span data-ttu-id="b2364-172">`APP_PATHS` これは、信頼されるプラットフォーム アセンブリ (TPA) リストでアセンブリが見つからない場合、アセンブリを探すパスのリストです。</span><span class="sxs-lookup"><span data-stu-id="b2364-172">`APP_PATHS` This is a list of paths to probe in for an assembly if it can't be found in the trusted platform assemblies (TPA) list.</span></span> <span data-ttu-id="b2364-173">TPA リストの場合、読み込まれるアセンブリをホスト側でより細かく制御できるため、ホストで読み込み、列挙するアセンブリを明示的に決定することがホストにとってはベスト プラクティスです。</span><span class="sxs-lookup"><span data-stu-id="b2364-173">Because the host has more control over which assemblies are loaded using the TPA list, it is a best practice for hosts to determine which assemblies they expect to load and list them explicitly.</span></span> <span data-ttu-id="b2364-174">ただし、実行時にプローブが必要な場合は、このプロパティでそのシナリオに対処できます。</span><span class="sxs-lookup"><span data-stu-id="b2364-174">If probing at run time is needed, however, this property can enable that scenario.</span></span>
* <span data-ttu-id="b2364-175">`APP_NI_PATHS` このリストは、ネイティブ イメージを探すパスであることを除き、APP_PATHS と似ています。</span><span class="sxs-lookup"><span data-stu-id="b2364-175">`APP_NI_PATHS` This list is similar to APP_PATHS except that it's meant to be paths that will be probed for native images.</span></span>
* <span data-ttu-id="b2364-176">`NATIVE_DLL_SEARCH_DIRECTORIES` このプロパティは、p/invoke で呼び出されたネイティブ ライブラリを探すときにローダーが調べるパスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="b2364-176">`NATIVE_DLL_SEARCH_DIRECTORIES` This property is a list of paths the loader should probe when looking for native libraries called via p/invoke.</span></span>
* <span data-ttu-id="b2364-177">`PLATFORM_RESOURCE_ROOTS` このリストには、(カルチャ固有の下位ディレクトリで) リソース サテライト アセンブリを探すパスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b2364-177">`PLATFORM_RESOURCE_ROOTS` This list includes paths to probe in for resource satellite assemblies (in culture-specific subdirectories).</span></span>

<span data-ttu-id="b2364-178">このサンプル ホストでは、現在のディレクトリにあるすべてのライブラリを単純に列挙することで TPA リストが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b2364-178">In this sample host, the TPA list is constructed by simply listing all libraries in the current directory:</span></span>

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

<span data-ttu-id="b2364-179">サンプルが単純なため、`TRUSTED_PLATFORM_ASSEMBLIES` プロパティのみを必要とします。</span><span class="sxs-lookup"><span data-stu-id="b2364-179">Because the sample is simple, it only needs the `TRUSTED_PLATFORM_ASSEMBLIES` property:</span></span>

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a><span data-ttu-id="b2364-180">手順 4 - ランタイムを起動する</span><span class="sxs-lookup"><span data-stu-id="b2364-180">Step 4 - Start the runtime</span></span>

<span data-ttu-id="b2364-181">`coreclrhost.h` API により、1 回の呼び出しでランタイムの起動と既定の AppDomain の作成が行われます。</span><span class="sxs-lookup"><span data-stu-id="b2364-181">`coreclrhost.h` APIs start the runtime and create the default AppDomain all with a single call.</span></span> <span data-ttu-id="b2364-182">`coreclr_initialize` 関数はベース パス、名前、前述のプロパティを取得し、`hostHandle` パラメーターを介してホストにハンドルを戻します。</span><span class="sxs-lookup"><span data-stu-id="b2364-182">The `coreclr_initialize` function takes a base path, name, and the properties described earlier and returns back a handle to the host via the `hostHandle` parameter.</span></span>

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a><span data-ttu-id="b2364-183">手順 5 - マネージド コードを実行する</span><span class="sxs-lookup"><span data-stu-id="b2364-183">Step 5 - Run managed code!</span></span>

<span data-ttu-id="b2364-184">ランタイムが起動すると、ホストではマネージド コードを呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="b2364-184">With the runtime started, the host can call managed code.</span></span> <span data-ttu-id="b2364-185">これにはさまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="b2364-185">This can be done in a couple of different ways.</span></span> <span data-ttu-id="b2364-186">このチュートリアルにリンクされているサンプル コードでは、`coreclr_create_delegate` 関数を使用して静的マネージド メソッドのデリゲートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b2364-186">The sample code linked to this tutorial uses the `coreclr_create_delegate` function to create a delegate to a static managed method.</span></span> <span data-ttu-id="b2364-187">この API は、[アセンブリ名](../../standard/assembly/names.md)、名前空間で修飾された型名、メソッド名を入力として取得し、メソッドの呼び出しに使用できるデリゲートを返します。</span><span class="sxs-lookup"><span data-stu-id="b2364-187">This API takes the [assembly name](../../standard/assembly/names.md), namespace-qualified type name, and method name as inputs and returns a delegate that can be used to invoke the method.</span></span>

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

<span data-ttu-id="b2364-188">このサンプルでは、これでホストは `managedDelegate` を呼び出し、`ManagedWorker.DoWork` メソッドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b2364-188">In this sample, the host can now call `managedDelegate` to run the `ManagedWorker.DoWork` method.</span></span>

<span data-ttu-id="b2364-189">あるいは、`coreclr_execute_assembly` 関数を使用し、マネージド実行可能ファイルを起動できます。</span><span class="sxs-lookup"><span data-stu-id="b2364-189">Alternatively, the `coreclr_execute_assembly` function can be used to launch a managed executable.</span></span> <span data-ttu-id="b2364-190">この API は、入力パラメーターとしてアセンブリのパスと一連の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b2364-190">This API takes an assembly path and array of arguments as input parameters.</span></span> <span data-ttu-id="b2364-191">そのパスでアセンブリを読み込み、そのメイン メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b2364-191">It loads the assembly at that path and invokes its main method.</span></span>

```c++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a><span data-ttu-id="b2364-192">手順 6 - シャットダウンとクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="b2364-192">Step 6 - Shutdown and clean up</span></span>

<span data-ttu-id="b2364-193">最後になりますが、ホストでマネージド コードの実行が完了すると、.NET Core ランタイムが `coreclr_shutdown` または `coreclr_shutdown_2` でシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="b2364-193">Finally, when the host is done running managed code, the .NET Core runtime is shut down with `coreclr_shutdown` or `coreclr_shutdown_2`.</span></span>

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

<span data-ttu-id="b2364-194">CoreCLR では、再初期化またはアンロードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b2364-194">CoreCLR does not support reinitialization or unloading.</span></span> <span data-ttu-id="b2364-195">`coreclr_initialize` を再度呼び出したり、CoreCLR ライブラリをアンロードしたりしないでください。</span><span class="sxs-lookup"><span data-stu-id="b2364-195">Do not call `coreclr_initialize` again or unload the CoreCLR library.</span></span>

## <a name="conclusion"></a><span data-ttu-id="b2364-196">まとめ</span><span class="sxs-lookup"><span data-stu-id="b2364-196">Conclusion</span></span>

<span data-ttu-id="b2364-197">ホストがビルドされたら、テストを行うことができます。コマンド ラインから実行し、ホストで想定される引数を渡します。</span><span class="sxs-lookup"><span data-stu-id="b2364-197">Once your host is built, it can be tested by running it from the command line and passing any arguments the host expects.</span></span> <span data-ttu-id="b2364-198">実行するホストの .NET Core アプリを指定するとき、`dotnet build` により生成された .dll を使用してください。</span><span class="sxs-lookup"><span data-stu-id="b2364-198">When specifying the .NET Core app for the host to run, be sure to use the .dll that is produced by `dotnet build`.</span></span> <span data-ttu-id="b2364-199">自己完結型アプリケーションのために `dotnet publish` で生成された実行可能ファイル (.exe ファイル) が実質的に既定の .NET Core ホストになります (メインライン シナリオでコマンド ラインから直接、アプリを起動できるように)。ユーザー コードがコンパイルされ、同じ名前の dll が作られます。</span><span class="sxs-lookup"><span data-stu-id="b2364-199">Executables (.exe files) produced by `dotnet publish` for self-contained applications are actually the default .NET Core host (so that the app can be launched directly from the command line in mainline scenarios); user code is compiled into a dll of the same name.</span></span>

<span data-ttu-id="b2364-200">最初の実行で動作しなかった場合、ホストが期待している場所に *coreclr.dll* があること、必要なすべての Framework ライブラリが TPA 一覧にあること、CoreCLR のビット数 (32 ビットまたは 64 ビット) がホストのビルド方法に一致することをもう一度確認してください。</span><span class="sxs-lookup"><span data-stu-id="b2364-200">If things don't work initially, double-check that *coreclr.dll* is available in the location expected by the host, that all necessary Framework libraries are in the TPA list, and that CoreCLR's bitness (32-bit or 64-bit) matches how the host was built.</span></span>

<span data-ttu-id="b2364-201">.NET Core ランタイムのホスティングは、多くの開発者が必要としない高度なシナリオですが、ネイティブ プロセスからマネージド コードを起動する場合や .NET Core ランタイムの動作をより細かくコントロールする場合、非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="b2364-201">Hosting the .NET Core runtime is an advanced scenario that many developers won't require, but for those who need to launch managed code from a native process, or who need more control over the .NET Core runtime's behavior, it can be very useful.</span></span>
