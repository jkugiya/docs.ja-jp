---
title: Parallel.ForEach を使用して単純な並列プログラムを記述する
description: この記事では、.NET でデータの並列処理を有効にする方法について説明します。 任意の IEnumerable または IEnumerable<T> データ ソースに対して、Parallel.ForEach ループを記述します。
ms.date: 02/23/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 50c60d730fbf930ea369b014e2f8f971e9c1f239
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106684"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="b6080-104">方法: 単純な Parallel.ForEach ループを記述する</span><span class="sxs-lookup"><span data-stu-id="b6080-104">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="b6080-105">この例は、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ループを使用して、<xref:System.Collections.IEnumerable?displayProperty=nameWithType> または <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> データ ソースでのデータの並列処理を有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b6080-105">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="b6080-106">ここでは、ラムダ式を使用して PLINQ でデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="b6080-106">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="b6080-107">C# または Visual Basic のラムダ式についての情報が必要な場合は、「[PLINQ および TPL のラムダ式](lambda-expressions-in-plinq-and-tpl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6080-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="b6080-108">例</span><span class="sxs-lookup"><span data-stu-id="b6080-108">Example</span></span>

<span data-ttu-id="b6080-109">この例は、CPU を集中的に使用する操作に対する <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> を示します。</span><span class="sxs-lookup"><span data-stu-id="b6080-109">This example demonstrates <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> for CPU intensive operations.</span></span> <span data-ttu-id="b6080-110">この例を実行すると、200 万の数字がランダムに生成され、素数へのフィルター処理が試行されます。</span><span class="sxs-lookup"><span data-stu-id="b6080-110">When you run the example, it randomly generates 2 million numbers and tries to filter to prime numbers.</span></span> <span data-ttu-id="b6080-111">最初のケースでは、`for` ループを使用してコレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="b6080-111">The first case iterates over the collection via a `for` loop.</span></span> <span data-ttu-id="b6080-112">2 番目のケースでは、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> を使用してコレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="b6080-112">The second case iterates over the collection via <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b6080-113">アプリケーションが終了すると、各反復にかかった時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6080-113">The resulting time taken by each iteration is displayed when the application is finished.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="b6080-114"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ループは <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ループのように動作します。</span><span class="sxs-lookup"><span data-stu-id="b6080-114">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="b6080-115">ループによってソース コレクションがパーティション分割され、作業はシステム環境に基づいて複数のスレッドでスケジューリングされます。</span><span class="sxs-lookup"><span data-stu-id="b6080-115">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="b6080-116">システムのプロセッサの数が多いほど、並列メソッドの実行が速くなります。</span><span class="sxs-lookup"><span data-stu-id="b6080-116">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="b6080-117">一部のソース コレクションでは、ソースのサイズやループで実行される作業の種類に応じて、順次ループがより高速になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b6080-117">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="b6080-118">パフォーマンスの詳細については、「[データとタスクの並列化における注意点](potential-pitfalls-in-data-and-task-parallelism.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6080-118">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="b6080-119">並列ループの詳細については、「[方法: 単純な Parallel.For ループを記述する](how-to-write-a-simple-parallel-for-loop.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6080-119">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="b6080-120">非ジェネリック コレクションで <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> を使用する場合は、次の例に示すように、<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> 拡張メソッドを使用して、コレクションをジェネリック コレクションに変換することができます。</span><span class="sxs-lookup"><span data-stu-id="b6080-120">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="b6080-121">また、Parallel LINQ (PLINQ) を使用して、<xref:System.Collections.Generic.IEnumerable%601> データ ソースの処理を並列化することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6080-121">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="b6080-122">PLINQ では、宣言型のクエリ構文を使用して、ループの動作を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="b6080-122">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="b6080-123">詳細については、「[Parallel LINQ (PLINQ)](introduction-to-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6080-123">For more information, see [Parallel LINQ (PLINQ)](introduction-to-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="b6080-124">コードをコンパイルして実行する</span><span class="sxs-lookup"><span data-stu-id="b6080-124">Compile and run the code</span></span>

<span data-ttu-id="b6080-125">コードは .NET Framework のコンソール アプリケーションまたは .NET Core のコンソール アプリケーションとしてコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="b6080-125">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="b6080-126">Visual Studio には、Windows デスクトップと .NET Core 向けに、Visual Basic と C# のコンソール アプリケーション テンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="b6080-126">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="b6080-127">コマンド ラインから .NET Core CLI コマンド (`dotnet new console` や `dotnet new console -lang vb` など) を使用するか、またはファイルを作成して .NET Framework アプリケーション用のコマンド ライン コンパイラを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b6080-127">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="b6080-128">コマンド ラインから .NET Core コンソール アプリケーションを実行するには、アプリケーションが含まれるフォルダーから `dotnet run` を使用します。</span><span class="sxs-lookup"><span data-stu-id="b6080-128">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="b6080-129">Visual Studio からコンソール アプリケーションを実行するには、**F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b6080-129">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6080-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6080-130">See also</span></span>

- [<span data-ttu-id="b6080-131">データの並列化</span><span class="sxs-lookup"><span data-stu-id="b6080-131">Data parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="b6080-132">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="b6080-132">Parallel programming</span></span>](index.md)
- [<span data-ttu-id="b6080-133">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b6080-133">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
