---
title: .NET 5 の新機能
description: .Net Core の次世代のクロス プラットフォームおよびオープンソースの開発プラットフォームである .NET 5 について説明します。
ms.date: 11/30/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 7984f235044db5dfc7533343e7d43cd7745fba33
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "103412178"
---
# <a name="whats-new-in-net-5"></a><span data-ttu-id="d0583-103">.NET 5 の新機能</span><span class="sxs-lookup"><span data-stu-id="d0583-103">What's new in .NET 5</span></span>

<span data-ttu-id="d0583-104">.NET 5.0 は、.NET Core 3.1 の次のメジャー リリースです。</span><span class="sxs-lookup"><span data-stu-id="d0583-104">.NET 5.0 is the next major release of .NET Core following 3.1.</span></span> <span data-ttu-id="d0583-105">この新しいリリースは、次の 2 つの理由から .NET Core 4.0 ではなく、.NET 5.0 と名付けられています。</span><span class="sxs-lookup"><span data-stu-id="d0583-105">We named this new release .NET 5.0 instead of .NET Core 4.0 for two reasons:</span></span>

- <span data-ttu-id="d0583-106">バージョン番号 4.x は、NET Framework 4.x との混同を避けるために省略しました。</span><span class="sxs-lookup"><span data-stu-id="d0583-106">We skipped version numbers 4.x to avoid confusion with .NET Framework 4.x.</span></span>
- <span data-ttu-id="d0583-107">以降の .NET の主要な実装であることを強調するために、名前から "Core" を削除しました。</span><span class="sxs-lookup"><span data-stu-id="d0583-107">We dropped "Core" from the name to emphasize that this is the main implementation of .NET going forward.</span></span> <span data-ttu-id="d0583-108">.NET 5.0 では、.NET Core または .NET Framework よりも多くの種類のアプリと多くのプラットフォームをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d0583-108">.NET 5.0 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="d0583-109">ASP.NET Core 5.0 は .NET 5.0 に基づいていますが、ASP.NET MVC 5 との混同を避けるために、"Core" という名前を引き続き使用しています。</span><span class="sxs-lookup"><span data-stu-id="d0583-109">ASP.NET Core 5.0 is based on .NET 5.0 but retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="d0583-110">同様に、Entity Framework Core 5.0 も、Entity Framework 5 および 6 との混同を避けるために、"Core" という名前を引き続き使用しています。</span><span class="sxs-lookup"><span data-stu-id="d0583-110">Likewise, Entity Framework Core 5.0 retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span>

<span data-ttu-id="d0583-111">.NET 5.0 には、.NET Core 3.1 と比較し、次の機能強化と新機能があります。</span><span class="sxs-lookup"><span data-stu-id="d0583-111">.NET 5.0 includes the following improvements and new features compared to .NET Core 3.1:</span></span>

- [<span data-ttu-id="d0583-112">C# の更新</span><span class="sxs-lookup"><span data-stu-id="d0583-112">C# updates</span></span>](#c-updates)
- [<span data-ttu-id="d0583-113">F# の更新</span><span class="sxs-lookup"><span data-stu-id="d0583-113">F# updates</span></span>](#f-updates)
- [<span data-ttu-id="d0583-114">Visual Basic の更新</span><span class="sxs-lookup"><span data-stu-id="d0583-114">Visual Basic updates</span></span>](#visual-basic-updates)
- [<span data-ttu-id="d0583-115">System.Text.Json の新機能</span><span class="sxs-lookup"><span data-stu-id="d0583-115">System.Text.Json new features</span></span>](#systemtextjson-new-features)
- [<span data-ttu-id="d0583-116">単一ファイル アプリ</span><span class="sxs-lookup"><span data-stu-id="d0583-116">Single file apps</span></span>](deploying/single-file.md)
- [<span data-ttu-id="d0583-117">アプリのトリミング</span><span class="sxs-lookup"><span data-stu-id="d0583-117">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- <span data-ttu-id="d0583-118">Windows ARM64 および ARM64 組み込み</span><span class="sxs-lookup"><span data-stu-id="d0583-118">Windows ARM64 and ARM64 intrinsics</span></span>
- <span data-ttu-id="d0583-119">ダンプ デバッグでのツールのサポート</span><span class="sxs-lookup"><span data-stu-id="d0583-119">Tooling support for dump debugging</span></span>
- <span data-ttu-id="d0583-120">ランタイム ライブラリの 80% に、[null 許容参照型](../csharp/nullable-references.md)の注釈が付けられています</span><span class="sxs-lookup"><span data-stu-id="d0583-120">The runtime libraries are 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>
- <span data-ttu-id="d0583-121">パフォーマンスの向上:</span><span class="sxs-lookup"><span data-stu-id="d0583-121">Performance improvements:</span></span>
  - [<span data-ttu-id="d0583-122">ガベージ コレクション (GC)</span><span class="sxs-lookup"><span data-stu-id="d0583-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="d0583-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="d0583-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="d0583-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="d0583-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="d0583-125">Async ValueTask プール</span><span class="sxs-lookup"><span data-stu-id="d0583-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="d0583-126">コンテナー サイズの最適化</span><span class="sxs-lookup"><span data-stu-id="d0583-126">Container size optimizations</span></span>](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [<span data-ttu-id="d0583-127">その他の多数の領域</span><span class="sxs-lookup"><span data-stu-id="d0583-127">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a><span data-ttu-id="d0583-128">.NET 5.0 は .NET Framework の後継ではない</span><span class="sxs-lookup"><span data-stu-id="d0583-128">.NET 5.0 doesn't replace .NET Framework</span></span>

<span data-ttu-id="d0583-129">.Net 5.0 は今後の .NET の主要な実装であり、.NET Framework 4.x は引き続きサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d0583-129">.NET 5.0 is the main implementation of .NET going forward and .NET Framework 4.x is still supported.</span></span>

<span data-ttu-id="d0583-130">次のテクノロジを .NET Framework から .NET 5.0 に移植する予定はありませんが、.NET 5.0 には代替手段があります。</span><span class="sxs-lookup"><span data-stu-id="d0583-130">There are no plans to port the following technologies from .NET Framework to .NET 5.0, but there are alternatives in .NET 5.0:</span></span>

| <span data-ttu-id="d0583-131">テクノロジ</span><span class="sxs-lookup"><span data-stu-id="d0583-131">Technology</span></span>            | <span data-ttu-id="d0583-132">推奨される代替手段</span><span class="sxs-lookup"><span data-stu-id="d0583-132">Recommended alternative</span></span>                                                                         |
|-----------------------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d0583-133">Web フォーム</span><span class="sxs-lookup"><span data-stu-id="d0583-133">Web Forms</span></span>             | <span data-ttu-id="d0583-134">ASP.NET Core [Blazor](/aspnet/core/blazor) または [Razor Pages](/aspnet/core/tutorials/razor-pages)</span><span class="sxs-lookup"><span data-stu-id="d0583-134">ASP.NET Core [Blazor](/aspnet/core/blazor) or [Razor Pages](/aspnet/core/tutorials/razor-pages)</span></span> |
| <span data-ttu-id="d0583-135">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="d0583-135">Windows Workflow (WF)</span></span> | <span data-ttu-id="d0583-136">[オープンソース CoreWF](https://github.com/UiPath-Open/corewf) または [Elsa ワークフロー](https://github.com/elsa-workflows/elsa-core)</span><span class="sxs-lookup"><span data-stu-id="d0583-136">[Open-source CoreWF](https://github.com/UiPath-Open/corewf) or [Elsa-Workflow](https://github.com/elsa-workflows/elsa-core)</span></span> |

### <a name="windows-communication-foundation"></a><span data-ttu-id="d0583-137">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d0583-137">Windows Communication Foundation</span></span>

<span data-ttu-id="d0583-138">元の [Windows Communication Foundation (WCF)](../framework/wcf/index.md) の実装は、Windows でのみサポートされていました。</span><span class="sxs-lookup"><span data-stu-id="d0583-138">The original implementation of [Windows Communication Foundation (WCF)](../framework/wcf/index.md) was only supported on Windows.</span></span> <span data-ttu-id="d0583-139">ただし、クライアント ポートが .NET Foundation から提供されています。</span><span class="sxs-lookup"><span data-stu-id="d0583-139">However, there is a client port available from the .NET Foundation.</span></span> <span data-ttu-id="d0583-140">これは、完全に[オープンソース](https://github.com/dotnet/wcf)であり、クロス プラットフォームで、Microsoft でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d0583-140">It is entirely [open source](https://github.com/dotnet/wcf), cross platform, and supported by Microsoft.</span></span> <span data-ttu-id="d0583-141">コア NuGet パッケージの一覧は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d0583-141">The core NuGet packages are listed below:</span></span>

- [<span data-ttu-id="d0583-142">System.ServiceModel.Duplex</span><span class="sxs-lookup"><span data-stu-id="d0583-142">System.ServiceModel.Duplex</span></span>](https://www.nuget.org/packages/System.ServiceModel.Duplex)
- [<span data-ttu-id="d0583-143">System.ServiceModel.Federation</span><span class="sxs-lookup"><span data-stu-id="d0583-143">System.ServiceModel.Federation</span></span>](https://www.nuget.org/packages/System.ServiceModel.Federation)
- [<span data-ttu-id="d0583-144">System.ServiceModel.Http</span><span class="sxs-lookup"><span data-stu-id="d0583-144">System.ServiceModel.Http</span></span>](https://www.nuget.org/packages/System.ServiceModel.Http)
- [<span data-ttu-id="d0583-145">System.ServiceModel.NetTcp</span><span class="sxs-lookup"><span data-stu-id="d0583-145">System.ServiceModel.NetTcp</span></span>](https://www.nuget.org/packages/System.ServiceModel.NetTcp)
- [<span data-ttu-id="d0583-146">System.ServiceModel.Primitives</span><span class="sxs-lookup"><span data-stu-id="d0583-146">System.ServiceModel.Primitives</span></span>](https://www.nuget.org/packages/System.ServiceModel.Primitives)
- [<span data-ttu-id="d0583-147">System.ServiceModel.Security</span><span class="sxs-lookup"><span data-stu-id="d0583-147">System.ServiceModel.Security</span></span>](https://www.nuget.org/packages/System.ServiceModel.Security)

<span data-ttu-id="d0583-148">前述のクライアント ライブラリを補完するサーバー コンポーネントは、コミュニティで管理されています。</span><span class="sxs-lookup"><span data-stu-id="d0583-148">The community maintains the server components that complement the aforementioned client libraries.</span></span> <span data-ttu-id="d0583-149">この GitHub リポジトリは、[Corewcf](https://github.com/CoreWCF/CoreWCF) にあります。</span><span class="sxs-lookup"><span data-stu-id="d0583-149">The GitHub repository can be found at [CoreWCF](https://github.com/CoreWCF/CoreWCF).</span></span> <span data-ttu-id="d0583-150">このサーバー コンポーネントは、Microsoft では正式にサポートされて _いません_。</span><span class="sxs-lookup"><span data-stu-id="d0583-150">The server components are _not_ officially supported by Microsoft.</span></span> <span data-ttu-id="d0583-151">WCF の代わりに、[gRPC](/aspnet/core/grpc) を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="d0583-151">For an alternative to WCF, consider [gRPC](/aspnet/core/grpc).</span></span>

## <a name="net-50-doesnt-replace-net-standard"></a><span data-ttu-id="d0583-152">.NET 5.0 は .NET Standard の後継ではない</span><span class="sxs-lookup"><span data-stu-id="d0583-152">.NET 5.0 doesn't replace .NET Standard</span></span>

<span data-ttu-id="d0583-153">新しいアプリケーションを開発する場合、`net5.0` ターゲット フレームワーク モニカー (TFM) を、クラス ライブラリを含むすべての種類のプロジェクトに指定できます。</span><span class="sxs-lookup"><span data-stu-id="d0583-153">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="d0583-154">`net5.0` TFM を使用するだけで、簡単に .NET 5 とワークロードを共有できます。</span><span class="sxs-lookup"><span data-stu-id="d0583-154">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="d0583-155">.NET 5.0 アプリおよびライブラリでは、`netcoreapp` と `netstandard` の TFM の組みが `net5.0` ターゲット フレームワーク モニカー (TFM) に置き換わっています。</span><span class="sxs-lookup"><span data-stu-id="d0583-155">For .NET 5.0 apps and libraries, the `net5.0` Target Framework Moniker (TFM) combines and replaces the `netcoreapp` and `netstandard` TFMs.</span></span> <span data-ttu-id="d0583-156">ただし、.NET Framework、.NET Core、および .NET 5 の各ワークロードと同じコードを使用する予定の場合は、`netstandard2.0` をお使いの TFM として指定します。</span><span class="sxs-lookup"><span data-stu-id="d0583-156">However, if you plan to share code between .NET Framework, .NET Core, and .NET 5 workloads, you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="d0583-157">詳細については、「[.NET Standard](../standard/net-standard.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d0583-157">For more information, see [.NET Standard](../standard/net-standard.md).</span></span>

## <a name="c-updates"></a><span data-ttu-id="d0583-158">C# の更新</span><span class="sxs-lookup"><span data-stu-id="d0583-158">C# updates</span></span>

<span data-ttu-id="d0583-159">.NET 5 アプリを記述する開発者は、C# の最新バージョンと機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d0583-159">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="d0583-160">.NET 5 は、この言語に多数の新機能が取り入れられた C# 9 とペアになっています。</span><span class="sxs-lookup"><span data-stu-id="d0583-160">.NET 5 is paired with C# 9, which brings many new features to the language.</span></span> <span data-ttu-id="d0583-161">次にいくつか主要なものを紹介します。</span><span class="sxs-lookup"><span data-stu-id="d0583-161">Here are a few highlights:</span></span>

- <span data-ttu-id="d0583-162">レコード: 値ベースの等値セマンティクスを使用する参照型と、新しい `with` 式でサポートされる非破壊的な変化。</span><span class="sxs-lookup"><span data-stu-id="d0583-162">Records: reference types with value-based equality semantics and non-destructive mutation supported by a new `with` expression.</span></span>
- <span data-ttu-id="d0583-163">リレーショナル パターン マッチング: 論理パターン (`and`、`or`、`not` の新しいキーワード) を含む比較評価および式のための、パターン マッチング機能の関係演算子への拡張。</span><span class="sxs-lookup"><span data-stu-id="d0583-163">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="d0583-164">最上位レベルのステートメント: C# の採用と学習を加速するために、`Main` メソッドを省略でき、次のような単純なアプリケーションが許可されています。</span><span class="sxs-lookup"><span data-stu-id="d0583-164">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="d0583-165">関数ポインター: `ldftn` および `calli` の中間言語 (IL) オペコードを公開する言語構成要素。</span><span class="sxs-lookup"><span data-stu-id="d0583-165">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="d0583-166">利用可能な C# 9 の機能の詳細については、「[C# 9 の新機能](../csharp/whats-new/csharp-9.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0583-166">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

### <a name="source-generators"></a><span data-ttu-id="d0583-167">ソース ジェネレーター</span><span class="sxs-lookup"><span data-stu-id="d0583-167">Source generators</span></span>

<span data-ttu-id="d0583-168">開発者のプロジェクトでは、C# のいくつかの主要な新機能に加え、ソース ジェネレーターが使用されるようになっています。</span><span class="sxs-lookup"><span data-stu-id="d0583-168">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="d0583-169">ソース ジェネレーターを使用すると、コンパイル時に実行されるコードでお使いのプログラムを検査して、お使いのコードの残りの部分と共にコンパイルされる追加のファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="d0583-169">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="d0583-170">ソース ジェネレーターの詳細については、「[Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators)」 (C# のソース ジェネレーターの概要)、および [C# のソース ジェネレーターのサンプル](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0583-170">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

## <a name="f-updates"></a><span data-ttu-id="d0583-171">F# の更新</span><span class="sxs-lookup"><span data-stu-id="d0583-171">F# updates</span></span>

<span data-ttu-id="d0583-172">F# は .NET の関数型のプログラミング言語であり、.NET 5 で開発者は、F# 5 を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d0583-172">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="d0583-173">F# 5 の新機能をいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="d0583-173">Here are several new features of F# 5:</span></span>

### <a name="interpolated-strings"></a><span data-ttu-id="d0583-174">挿入文字列</span><span class="sxs-lookup"><span data-stu-id="d0583-174">Interpolated strings</span></span>

<span data-ttu-id="d0583-175">C# の補間文字列と同様に、また JavaScript でも、F# で基本の文字列補間がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d0583-175">Similar to interpolated string in C#, and even JavaScript, F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="d0583-176">基本の文字列補間に加え、型指定の補間があります。</span><span class="sxs-lookup"><span data-stu-id="d0583-176">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="d0583-177">型指定の補間では、指定した型が書式指定子と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0583-177">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="d0583-178">これは、タイプセーフな入力に基づいて文字列を書式設定する [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) 関数と似ています。</span><span class="sxs-lookup"><span data-stu-id="d0583-178">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

## <a name="visual-basic-updates"></a><span data-ttu-id="d0583-179">Visual Basic の更新</span><span class="sxs-lookup"><span data-stu-id="d0583-179">Visual Basic updates</span></span>

<span data-ttu-id="d0583-180">.NET 5 の Visual Basic には、新しい言語機能がありません。</span><span class="sxs-lookup"><span data-stu-id="d0583-180">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="d0583-181">しかし、.NET 5 の Visual Basic では、次もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d0583-181">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="d0583-182">説明</span><span class="sxs-lookup"><span data-stu-id="d0583-182">Description</span></span>                            | <span data-ttu-id="d0583-183">`dotnet new` パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0583-183">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="d0583-184">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="d0583-184">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="d0583-185">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d0583-185">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="d0583-186">WPF アプリケーション</span><span class="sxs-lookup"><span data-stu-id="d0583-186">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="d0583-187">WPF クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d0583-187">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="d0583-188">WPF カスタム コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d0583-188">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="d0583-189">WPF ユーザー コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d0583-189">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="d0583-190">Windows フォーム (WinForms) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="d0583-190">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="d0583-191">Windows フォーム (WinForms) クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d0583-191">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="d0583-192">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="d0583-192">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="d0583-193">NUnit 3 テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="d0583-193">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="d0583-194">NUnit 3 テスト項目</span><span class="sxs-lookup"><span data-stu-id="d0583-194">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="d0583-195">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="d0583-195">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="d0583-196">.NET CLI のプロジェクト テンプレートの詳細については、「[`dotnet new`](tools/dotnet-new.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0583-196">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="systemtextjson-new-features"></a><span data-ttu-id="d0583-197">System.Text.Json の新機能</span><span class="sxs-lookup"><span data-stu-id="d0583-197">System.Text.Json new features</span></span>

<span data-ttu-id="d0583-198">[System.Text.Js](../standard/serialization/system-text-json-overview.md) に、またこれを対象とした新機能があります。</span><span class="sxs-lookup"><span data-stu-id="d0583-198">There are new features in and for [System.Text.Json](../standard/serialization/system-text-json-overview.md):</span></span>

- [<span data-ttu-id="d0583-199">参照を保持し、循環参照を処理する</span><span class="sxs-lookup"><span data-stu-id="d0583-199">Preserve references and handle circular references</span></span>](../standard/serialization/system-text-json-preserve-references.md)
- [<span data-ttu-id="d0583-200">HttpClient と HttpContent の拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="d0583-200">HttpClient and HttpContent extension methods</span></span>](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [<span data-ttu-id="d0583-201">引用符で囲まれた数値を許可または記述する</span><span class="sxs-lookup"><span data-stu-id="d0583-201">Allow or write numbers in quotes</span></span>](../standard/serialization/system-text-json-invalid-json.md#allow-or-write-numbers-in-quotes)
- [<span data-ttu-id="d0583-202">不変の型と C# 9 レコードのサポート</span><span class="sxs-lookup"><span data-stu-id="d0583-202">Support immutable types and C# 9 Records</span></span>](../standard/serialization/system-text-json-immutability.md)
- [<span data-ttu-id="d0583-203">パブリックでないプロパティ アクセサーのサポート</span><span class="sxs-lookup"><span data-stu-id="d0583-203">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-immutability.md)
- [<span data-ttu-id="d0583-204">フィールドのサポート</span><span class="sxs-lookup"><span data-stu-id="d0583-204">Support fields</span></span>](../standard/serialization/system-text-json-how-to.md#include-fields)
- [<span data-ttu-id="d0583-205">プロパティの条件付きでの無視</span><span class="sxs-lookup"><span data-stu-id="d0583-205">Conditionally ignore properties</span></span>](../standard/serialization/system-text-json-ignore-properties.md)
- [<span data-ttu-id="d0583-206">ディクショナリでの文字列以外のキーのサポート</span><span class="sxs-lookup"><span data-stu-id="d0583-206">Support non-string-key dictionaries</span></span>](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [<span data-ttu-id="d0583-207">カスタム コンバーターによる null の処理の許可</span><span class="sxs-lookup"><span data-stu-id="d0583-207">Allow custom converters to handle null</span></span>](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [<span data-ttu-id="d0583-208">JsonSerializerOptions をコピーする</span><span class="sxs-lookup"><span data-stu-id="d0583-208">Copy JsonSerializerOptions</span></span>](../standard/serialization/system-text-json-configure-options.md#copy-jsonserializeroptions)
- [<span data-ttu-id="d0583-209">Web の既定値を使用した JsonSerializerOptions の作成</span><span class="sxs-lookup"><span data-stu-id="d0583-209">Create JsonSerializerOptions with web defaults</span></span>](../standard/serialization/system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)

## <a name="see-also"></a><span data-ttu-id="d0583-210">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0583-210">See also</span></span>

- [<span data-ttu-id="d0583-211">1 つの .NET への道のり</span><span class="sxs-lookup"><span data-stu-id="d0583-211">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="d0583-212">.NET 5 のパフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="d0583-212">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- [<span data-ttu-id="d0583-213">.NET SDK をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="d0583-213">Download the .NET SDK</span></span>](https://dotnet.microsoft.com/download)
