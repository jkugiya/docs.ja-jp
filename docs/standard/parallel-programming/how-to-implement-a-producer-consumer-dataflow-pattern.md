---
title: 方法:プロデューサー/コンシューマーのデータフロー パターンを実装する
description: .NET の TPL データフロー ライブラリを使用して、プロデューサー/コンシューマー データフロー パターンを実装する方法について理解します。
ms.date: 09/24/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
ms.openlocfilehash: 94948d66ce2cb618c7501e55ba69745b44c7b793
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255263"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a><span data-ttu-id="2fc2b-103">方法:プロデューサー/コンシューマーのデータフロー パターンを実装する</span><span class="sxs-lookup"><span data-stu-id="2fc2b-103">How to: Implement a producer-consumer dataflow pattern</span></span>

<span data-ttu-id="2fc2b-104">この記事では、TPL データフロー ライブラリを使用して、プロデューサー/コンシューマー パターンを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-104">In this article, you'll learn how to use the TPL dataflow library to implement a producer-consumer pattern.</span></span> <span data-ttu-id="2fc2b-105">このパターンでは、"*プロデューサー*" がメッセージをメッセージ ブロックに送信し、"*コンシューマー*" がそのブロックからメッセージを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-105">In this pattern, the *producer* sends messages to a message block, and the *consumer* reads messages from that block.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="2fc2b-106">例</span><span class="sxs-lookup"><span data-stu-id="2fc2b-106">Example</span></span>

<span data-ttu-id="2fc2b-107">次の例では、データフローを使用する基本的なプロデューサー/コンシューマー モデルを示します。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-107">The following example demonstrates a basic producer-consumer model that uses dataflow.</span></span> <span data-ttu-id="2fc2b-108">`Produce` メソッドは、データのランダム バイトを含む配列を <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> オブジェクトに書き込み、`Consume` メソッドは <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> オブジェクトからバイトを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-108">The `Produce` method writes arrays that contain random bytes of data to a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> object and the `Consume` method reads bytes from a <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="2fc2b-109">派生型ではなく、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> と <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> のインターフェイス上で動作することで、さまざまなデータフロー ブロック型上で動作する再利用可能なコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-109">By acting on the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> and <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, instead of their derived types, you can write reusable code that can act on a variety of dataflow block types.</span></span> <span data-ttu-id="2fc2b-110">この例では、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-110">This example uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class.</span></span> <span data-ttu-id="2fc2b-111"><xref:System.Threading.Tasks.Dataflow.BufferBlock%601> クラスはソース ブロックとターゲット ブロックの両方として機能するため、プロデューサーおよびコンシューマーは共有されたオブジェクトを使用してデータを転送できます。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-111">Because the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class acts as both a source block and as a target block, the producer and the consumer can use a shared object to transfer data.</span></span>

 <span data-ttu-id="2fc2b-112">`Produce` メソッドはループ内で <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> メソッドを呼び出し、ターゲット ブロックにデータを同期的に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-112">The `Produce` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method in a loop to synchronously write data to the target block.</span></span> <span data-ttu-id="2fc2b-113">`Produce` メソッドはターゲット ブロックにすべてのデータを書き込んだ後、<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> メソッドを呼び出して、このブロックに使用可能なデータが追加されないように指示します。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-113">After the `Produce` method writes all data to the target block, it calls the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> method to indicate that the block will never have additional data available.</span></span> <span data-ttu-id="2fc2b-114">`Consume` メソッドでは、[async](../../csharp/language-reference/keywords/async.md) 演算子と [await](../../csharp/language-reference/operators/await.md) 演算子 (Visual Basic では [Async](../../visual-basic/language-reference/modifiers/async.md) と [Await](../../visual-basic/language-reference/operators/await-operator.md)) を使用して、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> オブジェクトから受信した合計バイト数を非同期的に計算します。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-114">The `Consume` method uses the [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) operators ([Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic) to asynchronously compute the total number of bytes that are received from the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object.</span></span> <span data-ttu-id="2fc2b-115">非同期的に動作するために、`Consume` メソッドは <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> メソッドを呼び出して、ソース ブロックに使用可能なデータがあるときとソース ブロックに使用可能なデータが追加されなくなったときに、通知を受信します。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-115">To act asynchronously, the `Consume` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> method to receive a notification when the source block has data available and when the source block will never have additional data available.</span></span>

 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="2fc2b-116">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="2fc2b-116">Robust programming</span></span>

 <span data-ttu-id="2fc2b-117">上記の例では、1 つのコンシューマーのみを使用してソース データを処理します。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-117">The preceding example uses just one consumer to process the source data.</span></span> <span data-ttu-id="2fc2b-118">アプリケーションに複数のコンシューマーがある場合は、次の例に示すように、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> メソッドを使用してソース ブロックからデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-118">If you have multiple consumers in your application, use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read data from the source block, as shown in the following example.</span></span>

 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]

 <span data-ttu-id="2fc2b-119"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> メソッドは、データを使用できないときに `False` を返します。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-119">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method returns `False` when no data is available.</span></span> <span data-ttu-id="2fc2b-120">複数のコンシューマーがソース ブロックに同時にアクセスする必要がある場合、この仕組みが、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> の呼び出し後もデータを使用可能なことを保証します。</span><span class="sxs-lookup"><span data-stu-id="2fc2b-120">When multiple consumers must access the source block concurrently, this mechanism guarantees that data is still available after the call to <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fc2b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="2fc2b-121">See also</span></span>

- [<span data-ttu-id="2fc2b-122">データフロー</span><span class="sxs-lookup"><span data-stu-id="2fc2b-122">Dataflow</span></span>](dataflow-task-parallel-library.md)
