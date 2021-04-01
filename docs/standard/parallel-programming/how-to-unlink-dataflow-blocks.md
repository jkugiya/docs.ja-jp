---
description: '詳細情報: データ フロー ブロックのリンクを解除する方法'
title: 方法:データ フロー ブロックのリンクを解除する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
ms.openlocfilehash: d3bea3887553397c902345e9dcc39ca0cdfe68d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629501"
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="1a717-103">方法:データ フロー ブロックのリンクを解除する</span><span class="sxs-lookup"><span data-stu-id="1a717-103">How to: Unlink Dataflow Blocks</span></span>

<span data-ttu-id="1a717-104">このドキュメントでは、ソースからターゲット データフロー ブロックのリンクを解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a717-104">This document describes how to unlink a target dataflow block from its source.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="1a717-105">例</span><span class="sxs-lookup"><span data-stu-id="1a717-105">Example</span></span>  

 <span data-ttu-id="1a717-106">次の例では、3 つの <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> オブジェクトを作成し、それぞれのオブジェクトが値を計算する `TrySolution` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1a717-106">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="1a717-107">この例は、完了させるために、`TrySolution` に対する最初の呼び出しからの結果のみが必要です。</span><span class="sxs-lookup"><span data-stu-id="1a717-107">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="1a717-108">完了した最初の <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> オブジェクトの結果を受信するために、この例では `ReceiveFromAny(T)` メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="1a717-108">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="1a717-109">`ReceiveFromAny(T)` メソッドは、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> オブジェクトの配列を受け取り、これらの各オブジェクトと <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトをリンクさせます。</span><span class="sxs-lookup"><span data-stu-id="1a717-109">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="1a717-110"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> メソッドを使用してソース データフロー ブロックをターゲット ブロックにリンクさせると、データが使用可能になったときにソースがターゲットにメッセージを反映させます。</span><span class="sxs-lookup"><span data-stu-id="1a717-110">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="1a717-111"><xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> クラスは提供される最初のメッセージのみを受け取るため、`ReceiveFromAny(T)` メソッドは <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> メソッドを呼び出して、その結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="1a717-111">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="1a717-112">これにより、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトに提供される最初のメッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1a717-112">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="1a717-113"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> メソッドには、<xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> オブジェクトと <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> プロパティを取得するオーバーロードされたバージョンがあります。そのプロパティを `1` に設定すると、ソースからターゲットに 1 つのメッセージが届いた後に、ターゲットとのリンクを解除するようにソース ブロックに指示が出されます。</span><span class="sxs-lookup"><span data-stu-id="1a717-113">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes an <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> object with a <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> property that, when it is set to `1`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="1a717-114">ソースの配列と <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトの関係は、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトがメッセージを受信した後は必要なくなるため、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトにはそのソースからリンクを解除することが重要です。</span><span class="sxs-lookup"><span data-stu-id="1a717-114">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="1a717-115">いずれかで値を計算した後に、`TrySolution` への残りの呼び出しを終了できるようにするには、`TrySolution` メソッドは `ReceiveFromAny(T)` への呼び出しが返された後にキャンセルされる、<xref:System.Threading.CancellationToken> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="1a717-115">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="1a717-116"><xref:System.Threading.SpinWait.SpinUntil%2A> メソッドは、この <xref:System.Threading.CancellationToken> オブジェクトがキャンセルされたときに返されます。</span><span class="sxs-lookup"><span data-stu-id="1a717-116">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a717-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a717-117">See also</span></span>

- [<span data-ttu-id="1a717-118">データフロー</span><span class="sxs-lookup"><span data-stu-id="1a717-118">Dataflow</span></span>](dataflow-task-parallel-library.md)
