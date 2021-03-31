---
description: '詳細情報: PLINQ クエリの例外を処理する方法'
title: 方法:PLINQ クエリの例外を処理する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
ms.openlocfilehash: 3699a913f227ac931dd40a29bfc28e7161b0db0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702016"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="fd909-103">方法:PLINQ クエリの例外を処理する</span><span class="sxs-lookup"><span data-stu-id="fd909-103">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="fd909-104">このトピックの最初の例では、PLINQ クエリの実行時にスローされる <xref:System.AggregateException?displayProperty=nameWithType> の処理方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fd909-104">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="fd909-105">2 番目の例では、デリゲート内で例外がスローされる場所のできるだけ近くに try-catch ブロックを配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fd909-105">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="fd909-106">こうすると、発生の直後に例外をキャッチしてクエリの実行を続行できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fd909-106">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="fd909-107">連結しているスレッドへ例外が上方向へ通知されると、例外が発生した後も、クエリによって一部の項目の処理が続行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fd909-107">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="fd909-108">場合によっては、PLINQ が順次実行に戻り、例外が発生すると、例外が直接反映され、<xref:System.AggregateException> にラップされないことがあります。</span><span class="sxs-lookup"><span data-stu-id="fd909-108">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="fd909-109">また、<xref:System.Threading.ThreadAbortException> は常に直接反映されます。</span><span class="sxs-lookup"><span data-stu-id="fd909-109">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="fd909-110">[マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd909-110">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="fd909-111">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="fd909-111">This error is benign.</span></span> <span data-ttu-id="fd909-112">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="fd909-112">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="fd909-113">Visual Studio による処理が最初のエラーで中断しないようにするには、 **[ツール] メニューの [オプション]、[デバッグ] 、[全般]** の順にクリックし、[マイ コードのみ] チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="fd909-113">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="fd909-114">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fd909-114">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="fd909-115">高速化の詳細については、「[PLINQ での高速化について](understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd909-115">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="fd909-116">例</span><span class="sxs-lookup"><span data-stu-id="fd909-116">Example</span></span>

<span data-ttu-id="fd909-117">次の例は、スローされる <xref:System.AggregateException?displayProperty=nameWithType> をキャッチするクエリを実行するコードの近くに try-catch ブロックを配置する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="fd909-117">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="fd909-118">この例では、例外がスローされた後にクエリを続行することはできません。</span><span class="sxs-lookup"><span data-stu-id="fd909-118">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="fd909-119">アプリケーション コードが例外をキャッチするまでに、PLINQ はすべてのスレッド上でクエリを停止しています。</span><span class="sxs-lookup"><span data-stu-id="fd909-119">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="fd909-120">例</span><span class="sxs-lookup"><span data-stu-id="fd909-120">Example</span></span>

<span data-ttu-id="fd909-121">次の例は、例外をキャッチしてクエリの実行を続行できるようにするため、try-catch ブロックをデリゲートに配置する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="fd909-121">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="fd909-122">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="fd909-122">Compiling the Code</span></span>

- <span data-ttu-id="fd909-123">これらの例をコンパイルして実行するには、これらのコードを PLINQ データのサンプルにコピーして、Main からメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fd909-123">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="fd909-124">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="fd909-124">Robust Programming</span></span>

<span data-ttu-id="fd909-125">プログラムの状態を破損しないようにするため、処理方法がわからない場合は、例外をキャッチしないでください。</span><span class="sxs-lookup"><span data-stu-id="fd909-125">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd909-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd909-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="fd909-127">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="fd909-127">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
