---
description: 詳細については、「.NET Native によるアプリのコンパイル」を参照してください。
title: .NET ネイティブによるアプリのコンパイル
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
ms.openlocfilehash: 2626daf17fda751edd7915f15fd4b68ffb623dff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747661"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="afe66-103">.NET ネイティブによるアプリのコンパイル</span><span class="sxs-lookup"><span data-stu-id="afe66-103">Compiling Apps with .NET Native</span></span>

<span data-ttu-id="afe66-104">.NET Native は、Visual Studio 2015 以降のバージョンに付属している Windows アプリをビルドおよび配置するためのプリコンパイルテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="afe66-104">.NET Native is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="afe66-105">マネージド コード (C# または Visual Basic) で記述された、.NET Framework および Windows 10 を対象とするアプリのリリース バージョンを自動的にネイティブ コードにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="afe66-105">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>

<span data-ttu-id="afe66-106">通常、.NET Framework を対象とするアプリは中間言語 (IL) にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="afe66-106">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="afe66-107">実行時に、Just-In-Time (JIT) コンパイラによって IL がネイティブ コードに変換されます。</span><span class="sxs-lookup"><span data-stu-id="afe66-107">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="afe66-108">これに対し、.NET Native は、Windows アプリを直接ネイティブコードにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="afe66-108">In contrast, .NET Native compiles Windows apps directly to native code.</span></span> <span data-ttu-id="afe66-109">開発者にとって、これは次のことを意味します。</span><span class="sxs-lookup"><span data-stu-id="afe66-109">For developers, this means:</span></span>

- <span data-ttu-id="afe66-110">アプリは、ネイティブコードのパフォーマンスを特徴としています。</span><span class="sxs-lookup"><span data-stu-id="afe66-110">Your apps feature the performance of native code.</span></span> <span data-ttu-id="afe66-111">通常、パフォーマンスは、最初に IL にコンパイルされてから JIT コンパイラによってネイティブコードにコンパイルされるコードよりも優れています。</span><span class="sxs-lookup"><span data-stu-id="afe66-111">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span>

- <span data-ttu-id="afe66-112">引き続き C# または Visual Basic でプログラムを作成できます。</span><span class="sxs-lookup"><span data-stu-id="afe66-112">You can continue to program in C# or Visual Basic.</span></span>

- <span data-ttu-id="afe66-113">クラス ライブラリ、自動メモリ管理とガベージ コレクション、例外処理など、.NET Framework で提供されるリソースを引き続き利用できます。</span><span class="sxs-lookup"><span data-stu-id="afe66-113">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>

<span data-ttu-id="afe66-114">アプリのユーザーのために、.NET Native には次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="afe66-114">For users of your apps, .NET Native offers these advantages:</span></span>

- <span data-ttu-id="afe66-115">大部分のアプリとシナリオの実行時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="afe66-115">Faster execution times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="afe66-116">ほとんどのアプリとシナリオで、起動時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="afe66-116">Faster startup times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="afe66-117">デプロイコストと更新コストが低くなります。</span><span class="sxs-lookup"><span data-stu-id="afe66-117">Low deployment and update costs.</span></span>

- <span data-ttu-id="afe66-118">アプリのメモリ使用量が最適化されています。</span><span class="sxs-lookup"><span data-stu-id="afe66-118">Optimized app memory usage.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="afe66-119">アプリとシナリオの大部分では、IL または NGEN イメージにコンパイルされたアプリと比較した場合、起動時間が大幅に短縮され、パフォーマンスが向上します。 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="afe66-119">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="afe66-120">ただし、結果は異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="afe66-120">However, your results may vary.</span></span> <span data-ttu-id="afe66-121">.NET Native のパフォーマンスの向上によってアプリのパフォーマンスを向上させるには、アプリの non-.NET ネイティブバージョンとのパフォーマンスを比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afe66-121">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="afe66-122">詳細については、「 [パフォーマンスセッションの概要](/visualstudio/profiling/performance-session-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afe66-122">For more information, see [Performance Session Overview](/visualstudio/profiling/performance-session-overview).</span></span>

<span data-ttu-id="afe66-123">ただし .NET Native には、ネイティブコードへのコンパイル以外にも関係があります。</span><span class="sxs-lookup"><span data-stu-id="afe66-123">But .NET Native involves more than a compilation to native code.</span></span> <span data-ttu-id="afe66-124">.NET Framework アプリのビルド方法と実行方法が変更されます。</span><span class="sxs-lookup"><span data-stu-id="afe66-124">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="afe66-125">特に次の点に違いがあります。</span><span class="sxs-lookup"><span data-stu-id="afe66-125">In particular:</span></span>

- <span data-ttu-id="afe66-126">プリコンパイル時に、.NET Framework の必要な部分がアプリに静的にリンクされます。</span><span class="sxs-lookup"><span data-stu-id="afe66-126">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="afe66-127">これにより、アプリは .NET Framework のアプリ ローカルのライブラリを使用して実行でき、コンパイラはグローバル分析を実行してパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="afe66-127">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="afe66-128">その結果、.NET Framework の更新後であっても、アプリは常に高速に起動します。</span><span class="sxs-lookup"><span data-stu-id="afe66-128">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>

- <span data-ttu-id="afe66-129">.NET Native ランタイムは静的プリコンパイル用に最適化されており、ほとんどのケースでは優れたパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="afe66-129">The .NET Native runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="afe66-130">同時に、開発者に役立つ主要なリフレクション機能もあります。</span><span class="sxs-lookup"><span data-stu-id="afe66-130">At the same time, it retains the core reflection features that developers find so productive.</span></span>

- <span data-ttu-id="afe66-131">.NET Native は、静的なプリコンパイルのシナリオに最適化された、C++ コンパイラと同じバックエンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="afe66-131">.NET Native uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>

<span data-ttu-id="afe66-132">.NET Native は、次の表に示すように、内部で C++ と同じまたは類似のツールを使用しているため、C++ のパフォーマンス上の利点をマネージコードの開発者に持ち込むことができます。</span><span class="sxs-lookup"><span data-stu-id="afe66-132">.NET Native is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>

||<span data-ttu-id="afe66-133">.NET Native</span><span class="sxs-lookup"><span data-stu-id="afe66-133">.NET Native</span></span>|<span data-ttu-id="afe66-134">C++</span><span class="sxs-lookup"><span data-stu-id="afe66-134">C++</span></span>|
|-|----------------------------------------------------------------|-----------|
|<span data-ttu-id="afe66-135">ライブラリ</span><span class="sxs-lookup"><span data-stu-id="afe66-135">Libraries</span></span>|<span data-ttu-id="afe66-136">.NET Framework + Windows ランタイム</span><span class="sxs-lookup"><span data-stu-id="afe66-136">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="afe66-137">Win32 + Windows ランタイム</span><span class="sxs-lookup"><span data-stu-id="afe66-137">Win32 + Windows Runtime</span></span>|
|<span data-ttu-id="afe66-138">コンパイラ</span><span class="sxs-lookup"><span data-stu-id="afe66-138">Compiler</span></span>|<span data-ttu-id="afe66-139">UTC 最適化コンパイラ</span><span class="sxs-lookup"><span data-stu-id="afe66-139">UTC optimizing compiler</span></span>|<span data-ttu-id="afe66-140">UTC 最適化コンパイラ</span><span class="sxs-lookup"><span data-stu-id="afe66-140">UTC optimizing compiler</span></span>|
|<span data-ttu-id="afe66-141">配置</span><span class="sxs-lookup"><span data-stu-id="afe66-141">Deployed</span></span>|<span data-ttu-id="afe66-142">実行可能バイナリ</span><span class="sxs-lookup"><span data-stu-id="afe66-142">Ready-to-run binaries</span></span>|<span data-ttu-id="afe66-143">実行可能バイナリ (ASM)</span><span class="sxs-lookup"><span data-stu-id="afe66-143">Ready-to-run binaries (ASM)</span></span>|
|<span data-ttu-id="afe66-144">ランタイム</span><span class="sxs-lookup"><span data-stu-id="afe66-144">Runtime</span></span>|<span data-ttu-id="afe66-145">MRT.dll (最小 CLR ランタイム)</span><span class="sxs-lookup"><span data-stu-id="afe66-145">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="afe66-146">CRT.dll (C ランタイム)</span><span class="sxs-lookup"><span data-stu-id="afe66-146">CRT.dll (C Runtime)</span></span>|

<span data-ttu-id="afe66-147">Windows 10 用の Windows アプリの場合は、.NET ネイティブ コード コンパイル バイナリをアプリ パッケージ (.appx ファイル) に入れて Windows ストアにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="afe66-147">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="afe66-148">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="afe66-148">In This Section</span></span>

<span data-ttu-id="afe66-149">.NET ネイティブ コード コンパイルを使用したアプリ開発の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="afe66-149">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>

- [<span data-ttu-id="afe66-150">.NET ネイティブ コード コンパイルの概要: 開発者向けチュートリアル</span><span class="sxs-lookup"><span data-stu-id="afe66-150">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](getting-started-with-net-native.md)

- <span data-ttu-id="afe66-151">[.NET ネイティブとコンパイル:](net-native-and-compilation.md) .NET ネイティブがプロジェクトをネイティブ コードにコンパイルする方法を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="afe66-151">[.NET Native and Compilation:](net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>

- [<span data-ttu-id="afe66-152">リフレクションおよび .NET ネイティブ</span><span class="sxs-lookup"><span data-stu-id="afe66-152">Reflection and .NET Native</span></span>](reflection-and-net-native.md)

  - [<span data-ttu-id="afe66-153">リフレクションに依存する API</span><span class="sxs-lookup"><span data-stu-id="afe66-153">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)

  - [<span data-ttu-id="afe66-154">リフレクション API リファレンス</span><span class="sxs-lookup"><span data-stu-id="afe66-154">Reflection API Reference</span></span>](net-native-reflection-api-reference.md)

  - [<span data-ttu-id="afe66-155">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="afe66-155">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)

- [<span data-ttu-id="afe66-156">シリアル化とメタデータ</span><span class="sxs-lookup"><span data-stu-id="afe66-156">Serialization and Metadata</span></span>](serialization-and-metadata.md)

- [<span data-ttu-id="afe66-157">Windows ストア アプリの .NET ネイティブへの移行</span><span class="sxs-lookup"><span data-stu-id="afe66-157">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)

- [<span data-ttu-id="afe66-158">.NET ネイティブの一般的なトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="afe66-158">.NET Native General Troubleshooting</span></span>](net-native-general-troubleshooting.md)
