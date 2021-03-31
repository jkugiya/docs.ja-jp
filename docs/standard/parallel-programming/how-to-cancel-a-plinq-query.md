---
description: '詳細情報: PLINQ クエリを取り消す方法'
title: '方法: PLINQ クエリを取り消す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
ms.openlocfilehash: c81ea565beb7287389ea043fee5854eb592e5271
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702185"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="30f9f-103">方法: PLINQ クエリを取り消す</span><span class="sxs-lookup"><span data-stu-id="30f9f-103">How to: Cancel a PLINQ Query</span></span>

<span data-ttu-id="30f9f-104">次の例は、PLINQ クエリを取り消す 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="30f9f-104">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="30f9f-105">最初の例は、主にデータ トラバーサルで構成されるクエリを取り消す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="30f9f-105">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="30f9f-106">2 つ目の例は、負荷の大きいユーザー関数を含むクエリを取り消す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="30f9f-106">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>

> [!NOTE]
> <span data-ttu-id="30f9f-107">[マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30f9f-107">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="30f9f-108">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="30f9f-108">This error is benign.</span></span> <span data-ttu-id="30f9f-109">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="30f9f-109">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="30f9f-110">Visual Studio による処理が最初のエラーで中断しないようにするには、 **[ツール] メニューの [オプション]、[デバッグ] 、[全般]** の順にクリックし、[マイ コードのみ] チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="30f9f-110">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="30f9f-111">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="30f9f-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="30f9f-112">高速化の詳細については、「[PLINQ での高速化について](understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30f9f-112">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="30f9f-113">例</span><span class="sxs-lookup"><span data-stu-id="30f9f-113">Example</span></span>

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

<span data-ttu-id="30f9f-114">PLINQ フレームワークでは単一の <xref:System.OperationCanceledException> が <xref:System.AggregateException?displayProperty=nameWithType> にローリングされません。<xref:System.OperationCanceledException> は別個のキャッチ ブロックで処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30f9f-114">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="30f9f-115">1 つ以上のユーザー デリゲートが (外部の <xref:System.Threading.CancellationToken?displayProperty=nameWithType> を使用して) OperationCanceledException(externalCT) をスローし、他の例外はスローしない場合で、クエリが `AsParallel().WithCancellation(externalCT)` として定義されている場合は、PLINQ は <xref:System.AggregateException?displayProperty=nameWithType> ではなく、単一の <xref:System.OperationCanceledException> (externalCT) を発行します。</span><span class="sxs-lookup"><span data-stu-id="30f9f-115">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="30f9f-116">ただし、1 つのユーザー デリゲートが <xref:System.OperationCanceledException> をスローし、別のデリゲートが別の種類の例外をスローした場合、両方の例外が <xref:System.AggregateException> にローリングされます。</span><span class="sxs-lookup"><span data-stu-id="30f9f-116">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>

<span data-ttu-id="30f9f-117">取り消しに関する一般的なガイダンスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="30f9f-117">The general guidance on cancellation is as follows:</span></span>

1. <span data-ttu-id="30f9f-118">ユーザー デリゲートを取り消す場合、外部の <xref:System.Threading.CancellationToken> について PLINQ に通知し、<xref:System.OperationCanceledException>(externalCT) をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="30f9f-118">If you perform user-delegate cancellation, you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>

2. <span data-ttu-id="30f9f-119">取り消しが発生し、その他の例外がスローされない場合は、<xref:System.AggregateException> ではなく <xref:System.OperationCanceledException> を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30f9f-119">If cancellation occurs and no other exceptions are thrown, then handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>

## <a name="example"></a><span data-ttu-id="30f9f-120">例</span><span class="sxs-lookup"><span data-stu-id="30f9f-120">Example</span></span>

<span data-ttu-id="30f9f-121">次の例は、ユーザー コードで負荷が大きい関数を使用する場合の取り消しの処理方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="30f9f-121">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

<span data-ttu-id="30f9f-122">ユーザー コードで取り消しを処理する場合、クエリ定義で <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="30f9f-122">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="30f9f-123">ただし、<xref:System.Linq.ParallelEnumerable.WithCancellation%2A> がクエリのパフォーマンスに影響を与えることはなく、クエリ演算子とお使いのユーザー コードで取り消しを処理できるため、<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="30f9f-123">However, we recommended that you do use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>, because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>

<span data-ttu-id="30f9f-124">システムの応答性を確保できるように、ミリ秒単位で取り消しを確認することをお勧めします。ただし、許容可能と見なされるのは 10 ミリ秒までです。</span><span class="sxs-lookup"><span data-stu-id="30f9f-124">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="30f9f-125">この頻度であれば、コードのパフォーマンスに悪影響を与えることはありません。</span><span class="sxs-lookup"><span data-stu-id="30f9f-125">This frequency should not have a negative impact on your code's performance.</span></span>

<span data-ttu-id="30f9f-126">列挙子が破棄された場合、たとえば、クエリ結果を反復処理している foreach (Visual Basic では For Each) ループからコードが抜け出た場合、クエリは取り消されますが、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="30f9f-126">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is canceled, but no exception is thrown.</span></span>

## <a name="see-also"></a><span data-ttu-id="30f9f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="30f9f-127">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="30f9f-128">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="30f9f-128">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
- [<span data-ttu-id="30f9f-129">マネージド スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="30f9f-129">Cancellation in Managed Threads</span></span>](../threading/cancellation-in-managed-threads.md)
