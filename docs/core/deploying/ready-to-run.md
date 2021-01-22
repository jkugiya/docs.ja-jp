---
title: ReadyToRun 展開の概要
description: ReadyToRun 展開の概要と、.NET 5 および .NET Core 3.0 以降でのアプリの発行の一部としてその使用を検討する必要がある理由について説明します。
author: davidwrighton
ms.author: davidwr
ms.date: 09/21/2020
ms.openlocfilehash: 2d4aaac2534bbb1279eb88d8e24e1f5f022afe7d
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536100"
---
# <a name="readytorun-compilation"></a><span data-ttu-id="3f05d-103">ReadyToRun コンパイル</span><span class="sxs-lookup"><span data-stu-id="3f05d-103">ReadyToRun Compilation</span></span>

<span data-ttu-id="3f05d-104">アプリケーション アセンブリを ReadyToRun (R2R) 形式としてコンパイルすることにより、.NET アプリケーションの起動時間と待機時間を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="3f05d-104">.NET application startup time and latency can be improved by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="3f05d-105">R2R とは、Ahead-Of-Time (AOT) コンパイルの一種です。</span><span class="sxs-lookup"><span data-stu-id="3f05d-105">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="3f05d-106">R2R バイナリでは、アプリケーションの読み込み時に Just-In-Time (JIT) コンパイラで行う必要がある作業量を減らすことにより、起動時のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="3f05d-106">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="3f05d-107">バイナリには、JIT で生成されるものと似たネイティブ コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3f05d-107">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="3f05d-108">ただし、R2R バイナリは、中間言語 (IL) コード (一部のシナリオでまだ必要です) と同じコードのネイティブ バージョンの両方が含まれるため、大きくなります。</span><span class="sxs-lookup"><span data-stu-id="3f05d-108">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="3f05d-109">R2R は、Linux x64 や Windows x64 などの特定のランタイム環境 (RID) を対象とするアプリを発行するときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3f05d-109">R2R is only available when you publish an app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="3f05d-110">プロジェクトを ReadyToRun としてコンパイルするには、PublishReadyToRun プロパティを `true` に設定してアプリケーションを発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f05d-110">To compile your project as ReadyToRun, the application must be published with the PublishReadyToRun property set to `true`.</span></span>

<span data-ttu-id="3f05d-111">アプリを ReadyToRun として発行するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="3f05d-111">There are two ways to publish your app as ReadyToRun:</span></span>

01. <span data-ttu-id="3f05d-112">PublishReadyToRun フラグを dotnet publish コマンドに対して直接指定します。</span><span class="sxs-lookup"><span data-stu-id="3f05d-112">Specify the PublishReadyToRun flag directly to the dotnet publish command.</span></span> <span data-ttu-id="3f05d-113">詳細については、「[dotnet publish](../tools/dotnet-publish.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f05d-113">See [dotnet publish](../tools/dotnet-publish.md) for details.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
    ```

02. <span data-ttu-id="3f05d-114">プロジェクトでプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f05d-114">Specify the property in the project.</span></span>

    - <span data-ttu-id="3f05d-115">`<PublishReadyToRun>` の設定をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="3f05d-115">Add the `<PublishReadyToRun>` setting to your project.</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

    - <span data-ttu-id="3f05d-116">特別なパラメーターを指定せずにアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="3f05d-116">Publish the application without any special parameters.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64
    ```

## <a name="impact-of-using-the-readytorun-feature"></a><span data-ttu-id="3f05d-117">ReadyToRun 機能を使用した場合の影響</span><span class="sxs-lookup"><span data-stu-id="3f05d-117">Impact of using the ReadyToRun feature</span></span>

<span data-ttu-id="3f05d-118">Ahead Of Time コンパイルには、アプリケーションのパフォーマンスに対して複雑な影響があり、その予測は困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f05d-118">Ahead-of-time compilation has complex performance impact on application performance, which can be difficult to predict.</span></span> <span data-ttu-id="3f05d-119">一般に、アセンブリのサイズは 2 から 3 倍の大きさになります。</span><span class="sxs-lookup"><span data-stu-id="3f05d-119">In general, the size of an assembly will grow to between two to three times larger.</span></span> <span data-ttu-id="3f05d-120">このようにファイルの物理サイズが大きくなると、ディスクからのアセンブリの読み込みのパフォーマンスが低下し、プロセスの作業セットが大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3f05d-120">This increase in the physical size of the file may reduce the performance of loading the assembly from disk, and increase working set of the process.</span></span> <span data-ttu-id="3f05d-121">ただし、代わりに、実行時にコンパイルされるメソッドの数は一般に大幅に減少します。</span><span class="sxs-lookup"><span data-stu-id="3f05d-121">However, in return the number of methods compiled at runtime is typically reduced substantially.</span></span> <span data-ttu-id="3f05d-122">その結果、大量のコードを使用するほとんどのアプリケーションでは、ReadyToRun を有効にすることにより、パフォーマンスに関して大きなメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="3f05d-122">The result is that most applications that have large amounts of code receive large performance benefits from enabling ReadyToRun.</span></span> <span data-ttu-id="3f05d-123">ReadyToRun によって .NET ランタイム ライブラリが既にプリコンパイルされているため、コードの量が少ないアプリケーションでは、ReadyToRun を有効にしてもそれほど向上しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f05d-123">Applications that have small amounts of code will likely not experience a significant improvement from enabling ReadyToRun, as the .NET runtime libraries have already been precompiled with ReadyToRun.</span></span>

<span data-ttu-id="3f05d-124">ここで説明する起動に関する向上は、アプリケーションの起動時だけでなく、アプリケーションで何かのコードを初めて使用するときにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="3f05d-124">The startup improvement discussed here applies not only to application startup, but also to the first use of any code in the application.</span></span> <span data-ttu-id="3f05d-125">たとえば、ReadyToRun を使用すると、ASP.NET アプリケーションで Web API を初めて使用するときの応答待機時間を短縮できます。</span><span class="sxs-lookup"><span data-stu-id="3f05d-125">For instance, ReadyToRun can be used to reduce the response latency of the first use of Web API in an ASP.NET application.</span></span>

### <a name="interaction-with-tiered-compilation"></a><span data-ttu-id="3f05d-126">階層型コンパイルとの相互作用</span><span class="sxs-lookup"><span data-stu-id="3f05d-126">Interaction with tiered compilation</span></span>

<span data-ttu-id="3f05d-127">Ahead Of Time で生成されるコードは、JIT によって生成されるコードほど高度に最適化されていません。</span><span class="sxs-lookup"><span data-stu-id="3f05d-127">Ahead-of-time generated code is not as highly optimized as code produced by the JIT.</span></span> <span data-ttu-id="3f05d-128">この問題に対処するため、階層型コンパイルでは、一般的に使用される ReadyToRun メソッドが、JIT で生成されるメソッドに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="3f05d-128">To address this issue, tiered compilation will replace commonly used ReadyToRun methods with JIT-generated methods.</span></span>

## <a name="how-is-the-set-of-precompiled-assemblies-chosen"></a><span data-ttu-id="3f05d-129">プリコンパイルされるアセンブリのセットが選択される方法</span><span class="sxs-lookup"><span data-stu-id="3f05d-129">How is the set of precompiled assemblies chosen?</span></span>

<span data-ttu-id="3f05d-130">SDK により、アプリケーションと共に配布されるアセンブリがプリコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="3f05d-130">The SDK will precompile the assemblies that are distributed with the application.</span></span> <span data-ttu-id="3f05d-131">自己完結型アプリケーションの場合、このアセンブリのセットにはフレームワークが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3f05d-131">For self-contained applications, this set of assemblies will include the framework.</span></span> <span data-ttu-id="3f05d-132">C++/CLI バイナリは、ReadyToRun コンパイルの対象にはなりません。</span><span class="sxs-lookup"><span data-stu-id="3f05d-132">C++/CLI binaries are not eligible for ReadyToRun compilation.</span></span>

## <a name="how-is-the-set-of-methods-to-precompile-chosen"></a><span data-ttu-id="3f05d-133">プリコンパイルされるメソッドのセットが選択される方法</span><span class="sxs-lookup"><span data-stu-id="3f05d-133">How is the set of methods to precompile chosen?</span></span>

<span data-ttu-id="3f05d-134">コンパイラでは、可能な限り多くのメソッドのプリコンパイルが試みられます。</span><span class="sxs-lookup"><span data-stu-id="3f05d-134">The compiler will attempt to pre-compile as many methods as it can.</span></span> <span data-ttu-id="3f05d-135">ただし、さまざまな理由で、ReadyToRun 機能を使用しても JIT が実行されなくなることは期待できません。</span><span class="sxs-lookup"><span data-stu-id="3f05d-135">However, for various reasons, it's not expected that using the ReadyToRun feature will prevent the JIT from executing.</span></span> <span data-ttu-id="3f05d-136">その理由には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="3f05d-136">Such reasons may include, but are not limited to:</span></span>

- <span data-ttu-id="3f05d-137">別のアセンブリで定義されているジェネリック型の使用。</span><span class="sxs-lookup"><span data-stu-id="3f05d-137">Use of generic types defined in separate assemblies.</span></span>
- <span data-ttu-id="3f05d-138">ネイティブ コードとの相互運用。</span><span class="sxs-lookup"><span data-stu-id="3f05d-138">Interop with native code.</span></span>
- <span data-ttu-id="3f05d-139">ターゲット コンピューターで使用しても安全であることをコンパイラで証明できないハードウェア組み込みの使用。</span><span class="sxs-lookup"><span data-stu-id="3f05d-139">Use of hardware intrinsics that the compiler cannot prove are safe to use on a target machine.</span></span>
- <span data-ttu-id="3f05d-140">特定の異常な IL パターン。</span><span class="sxs-lookup"><span data-stu-id="3f05d-140">Certain unusual IL patterns.</span></span>
- <span data-ttu-id="3f05d-141">リフレクションまたは LINQ による動的メソッド作成。</span><span class="sxs-lookup"><span data-stu-id="3f05d-141">Dynamic method creation via reflection or LINQ.</span></span>

## <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="3f05d-142">クロス プラットフォーム/アーキテクチャの制限</span><span class="sxs-lookup"><span data-stu-id="3f05d-142">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="3f05d-143">一部の SDK プラットフォームでは、ReadyToRun コンパイラにより他のターゲットプラットフォームに対するクロスコンパイルを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3f05d-143">For some SDK platforms, the ReadyToRun compiler is capable of cross-compiling for other target platforms.</span></span> <span data-ttu-id="3f05d-144">サポートされているコンパイル ターゲットについて次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="3f05d-144">Supported compilation targets are described in the following table.</span></span>

| <span data-ttu-id="3f05d-145">SDK プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="3f05d-145">SDK platform</span></span> | <span data-ttu-id="3f05d-146">サポート対象のターゲット プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="3f05d-146">Supported target platforms</span></span> |
| ------------ | --------------------------- |
| <span data-ttu-id="3f05d-147">Windows X64</span><span class="sxs-lookup"><span data-stu-id="3f05d-147">Windows X64</span></span>  | <span data-ttu-id="3f05d-148">Windows X86、Windows X64、Windows ARM32、Windows ARM64</span><span class="sxs-lookup"><span data-stu-id="3f05d-148">Windows X86, Windows X64, Windows ARM32, Windows ARM64</span></span> |
| <span data-ttu-id="3f05d-149">Windows X86</span><span class="sxs-lookup"><span data-stu-id="3f05d-149">Windows X86</span></span>  | <span data-ttu-id="3f05d-150">Windows X86、Windows ARM32</span><span class="sxs-lookup"><span data-stu-id="3f05d-150">Windows X86, Windows ARM32</span></span> |
| <span data-ttu-id="3f05d-151">Linux X64</span><span class="sxs-lookup"><span data-stu-id="3f05d-151">Linux X64</span></span>    | <span data-ttu-id="3f05d-152">Linux X86、Linux X64、Linux ARM32、Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="3f05d-152">Linux X86, Linux X64, Linux ARM32, Linux ARM64</span></span> |
| <span data-ttu-id="3f05d-153">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="3f05d-153">Linux ARM32</span></span>  | <span data-ttu-id="3f05d-154">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="3f05d-154">Linux ARM32</span></span> |
| <span data-ttu-id="3f05d-155">Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="3f05d-155">Linux ARM64</span></span>  | <span data-ttu-id="3f05d-156">Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="3f05d-156">Linux ARM64</span></span> |
| <span data-ttu-id="3f05d-157">macOS X64</span><span class="sxs-lookup"><span data-stu-id="3f05d-157">macOS X64</span></span>    | <span data-ttu-id="3f05d-158">macOS X64</span><span class="sxs-lookup"><span data-stu-id="3f05d-158">macOS X64</span></span> |
