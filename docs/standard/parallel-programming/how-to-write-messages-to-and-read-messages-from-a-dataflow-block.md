---
description: '詳細情報: データフロー ブロックとの間でメッセージの読み取りと書き込みを行う方法'
title: '方法: データフロー ブロックとの間でメッセージの読み取りと書き込みを行う'
ms.date: 09/10/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
ms.openlocfilehash: 7571ac7acf3dad6dedb1e16546197c5f0e72a9a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798057"
---
# <a name="how-to-write-and-read-messages-from-a-dataflow-block"></a><span data-ttu-id="7af0c-103">方法: データフロー ブロックとの間でメッセージの読み取りと書き込みを行う</span><span class="sxs-lookup"><span data-stu-id="7af0c-103">How to: Write and read messages from a Dataflow block</span></span>

<span data-ttu-id="7af0c-104">この記事では、タスク並列ライブラリ (TPL) データフロー ライブラリを使用して、データフロー ブロックとの間でメッセージの読み取りと書き込みを行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="7af0c-104">This article describes how to use the Task Parallel Library (TPL) Dataflow Library to write messages to and read messages from a dataflow block.</span></span> <span data-ttu-id="7af0c-105">TPL データフロー ライブラリには、データフロー ブロックへのメッセージの書き込みとデータフロー ブロックからのメッセージの読み取りのための、同期と非同期の両方のメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7af0c-105">The TPL Dataflow Library provides both synchronous and asynchronous methods for writing messages to and reading messages from a dataflow block.</span></span> <span data-ttu-id="7af0c-106">この記事では、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> クラスを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7af0c-106">This article shows how to uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7af0c-107"><xref:System.Threading.Tasks.Dataflow.BufferBlock%601> クラスは、メッセージをバッファーし、メッセージ ソースとメッセージ ターゲットの両方として動作します。</span><span class="sxs-lookup"><span data-stu-id="7af0c-107">The <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class buffers messages and behaves as both a message source and a message target.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-and-reading-synchronously"></a><span data-ttu-id="7af0c-108">同期的な書き込みと読み取り</span><span class="sxs-lookup"><span data-stu-id="7af0c-108">Writing and reading synchronously</span></span>

<span data-ttu-id="7af0c-109">次の例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> メソッドを使用して <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> データフロー ブロックを書き込み、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> メソッドを使用して同じオブジェクトから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="7af0c-109">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method to write to a <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dataflow block and the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method to read from the same object.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="2":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="2":::

<span data-ttu-id="7af0c-110">また、次の例に示すように、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> メソッドを使用してデータフロー ブロックから読み取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="7af0c-110">You can also use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read from a dataflow block, as shown in the following example.</span></span> <span data-ttu-id="7af0c-111"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> メソッドは、現在のスレッドをブロックしないため、データを時々ポーリングする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7af0c-111">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method does not block the current thread and is useful when you occasionally poll for data.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="3":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="3":::

<span data-ttu-id="7af0c-112"><xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> メソッドは同期的に動作するため、前の例の <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> オブジェクトは、2 つ目のループがデータを読み取る前にすべてのデータを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7af0c-112">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method acts synchronously, the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object in the previous examples receives all data before the second loop reads data.</span></span> <span data-ttu-id="7af0c-113">次の例では、<xref:System.Threading.Tasks.Task.WhenAll(System.Threading.Tasks.Task[])?displayProperty=nameWithType> を使用して最初の例を拡張し、メッセージ ブロックからの読み取りとメッセージ ブロックへの書き込みを同時に行います。</span><span class="sxs-lookup"><span data-stu-id="7af0c-113">The following example extends the first example by using <xref:System.Threading.Tasks.Task.WhenAll(System.Threading.Tasks.Task[])?displayProperty=nameWithType> to read from and write to the message block concurrently.</span></span> <span data-ttu-id="7af0c-114"><xref:System.Threading.Tasks.Task.WhenAll%2A> は同時にアクションを実行するため、値が特定の順序で <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> オブジェクトに書き込まれることはありません。</span><span class="sxs-lookup"><span data-stu-id="7af0c-114">Because <xref:System.Threading.Tasks.Task.WhenAll%2A> performs actions concurrently, the values are not written to the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object in any specific order.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="4":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="4":::

## <a name="writing-and-reading-asynchronously"></a><span data-ttu-id="7af0c-115">非同期的な書き込みと読み取り</span><span class="sxs-lookup"><span data-stu-id="7af0c-115">Writing and reading asynchronously</span></span>

<span data-ttu-id="7af0c-116">次の例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> メソッドを使用して <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> オブジェクトに非同期的に書き込み、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> メソッドを使用して同じオブジェクトから非同期的に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="7af0c-116">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> method to asynchronously write to a <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object and the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> method to asynchronously read from the same object.</span></span> <span data-ttu-id="7af0c-117">この例では、[async](../../csharp/language-reference/keywords/async.md) 演算子と [await](../../csharp/language-reference/operators/await.md) 演算子 (Visual Basic では [Async](../../visual-basic/language-reference/modifiers/async.md) と [Await](../../visual-basic/language-reference/operators/await-operator.md)) を使用して、ターゲット ブロックへのデータの送信とターゲット ブロックからのデータの読み取りを非同期的に行います。</span><span class="sxs-lookup"><span data-stu-id="7af0c-117">This example uses the [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) operators ([Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic) to asynchronously send data to and read data from the target block.</span></span> <span data-ttu-id="7af0c-118"><xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> メソッドは、メッセージを延期するデータフロー ブロックを有効にする必要があるときに便利です。</span><span class="sxs-lookup"><span data-stu-id="7af0c-118">The <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> method is useful when you must enable a dataflow block to postpone messages.</span></span> <span data-ttu-id="7af0c-119"><xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> メソッドは、データが利用できるようになったときにデータを操作する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7af0c-119">The <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> method is useful when you want to act on data when that data becomes available.</span></span> <span data-ttu-id="7af0c-120">メッセージ ブロック間でメッセージが伝達されるしくみの詳細については、[データフロー](dataflow-task-parallel-library.md)に関するページの「Message Passing (メッセージ パッシング)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7af0c-120">For more information about how messages propagate among message blocks, see the section Message Passing in [Dataflow](dataflow-task-parallel-library.md).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="5":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="5":::

## <a name="a-complete-example"></a><span data-ttu-id="7af0c-121">コード例全体</span><span class="sxs-lookup"><span data-stu-id="7af0c-121">A complete example</span></span>

<span data-ttu-id="7af0c-122">次の例には、この記事のコードがすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="7af0c-122">The following example shows all of the code for this article.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="1":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="1":::

## <a name="next-steps"></a><span data-ttu-id="7af0c-123">次のステップ</span><span class="sxs-lookup"><span data-stu-id="7af0c-123">Next steps</span></span>

<span data-ttu-id="7af0c-124">この例は、メッセージ ブロックからの読み取りとメッセージ ブロックへの書き込みを直接行う方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7af0c-124">This example shows how to read from and write to a message block directly.</span></span> <span data-ttu-id="7af0c-125">データフロー ブロックを接続して、データフロー ブロックのリニア シーケンスである "*パイプライン*" を作成するか、またはデータフロー ブロックのグラフである "*ネットワーク*" を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="7af0c-125">You can also connect dataflow blocks to form *pipelines*, which are linear sequences of dataflow blocks, or *networks*, which are graphs of dataflow blocks.</span></span> <span data-ttu-id="7af0c-126">パイプラインまたはネットワークでは、データが使用可能になると、ソースはターゲットに非同期的にデータを伝達します。</span><span class="sxs-lookup"><span data-stu-id="7af0c-126">In a pipeline or network, sources asynchronously propagate data to targets as that data becomes available.</span></span> <span data-ttu-id="7af0c-127">基本的なデータフロー パイプラインを作成する例については、「[Walkthrough: Creating a Dataflow Pipeline (チュートリアル: データフロー パイプラインの作成)](walkthrough-creating-a-dataflow-pipeline.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7af0c-127">For an example that creates a basic dataflow pipeline, see [Walkthrough: Creating a Dataflow Pipeline](walkthrough-creating-a-dataflow-pipeline.md).</span></span> <span data-ttu-id="7af0c-128">さらに複雑なデータフロー ネットワークを作成する例については、「[Walkthrough: Using Dataflow in a Windows Forms Application (チュートリアル: Windows フォーム アプリケーションでのデータフローの使用)](walkthrough-using-dataflow-in-a-windows-forms-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7af0c-128">For an example that creates a more complex dataflow network, see [Walkthrough: Using Dataflow in a Windows Forms Application](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7af0c-129">参照</span><span class="sxs-lookup"><span data-stu-id="7af0c-129">See also</span></span>

- [<span data-ttu-id="7af0c-130">データフロー (タスク並列ライブラリ)</span><span class="sxs-lookup"><span data-stu-id="7af0c-130">Dataflow (Task Parallel Library)</span></span>](dataflow-task-parallel-library.md)
