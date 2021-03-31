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
# <a name="how-to-write-and-read-messages-from-a-dataflow-block"></a>方法: データフロー ブロックとの間でメッセージの読み取りと書き込みを行う

この記事では、タスク並列ライブラリ (TPL) データフロー ライブラリを使用して、データフロー ブロックとの間でメッセージの読み取りと書き込みを行う方法を説明します。 TPL データフロー ライブラリには、データフロー ブロックへのメッセージの書き込みとデータフロー ブロックからのメッセージの読み取りのための、同期と非同期の両方のメソッドが用意されています。 この記事では、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> クラスを使用する方法について説明します。 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> クラスは、メッセージをバッファーし、メッセージ ソースとメッセージ ターゲットの両方として動作します。

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-and-reading-synchronously"></a>同期的な書き込みと読み取り

次の例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> メソッドを使用して <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> データフロー ブロックを書き込み、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> メソッドを使用して同じオブジェクトから読み取ります。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="2":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="2":::

また、次の例に示すように、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> メソッドを使用してデータフロー ブロックから読み取ることもできます。 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> メソッドは、現在のスレッドをブロックしないため、データを時々ポーリングする場合に便利です。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="3":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="3":::

<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> メソッドは同期的に動作するため、前の例の <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> オブジェクトは、2 つ目のループがデータを読み取る前にすべてのデータを受け取ります。 次の例では、<xref:System.Threading.Tasks.Task.WhenAll(System.Threading.Tasks.Task[])?displayProperty=nameWithType> を使用して最初の例を拡張し、メッセージ ブロックからの読み取りとメッセージ ブロックへの書き込みを同時に行います。 <xref:System.Threading.Tasks.Task.WhenAll%2A> は同時にアクションを実行するため、値が特定の順序で <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> オブジェクトに書き込まれることはありません。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="4":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="4":::

## <a name="writing-and-reading-asynchronously"></a>非同期的な書き込みと読み取り

次の例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> メソッドを使用して <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> オブジェクトに非同期的に書き込み、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> メソッドを使用して同じオブジェクトから非同期的に読み取ります。 この例では、[async](../../csharp/language-reference/keywords/async.md) 演算子と [await](../../csharp/language-reference/operators/await.md) 演算子 (Visual Basic では [Async](../../visual-basic/language-reference/modifiers/async.md) と [Await](../../visual-basic/language-reference/operators/await-operator.md)) を使用して、ターゲット ブロックへのデータの送信とターゲット ブロックからのデータの読み取りを非同期的に行います。 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> メソッドは、メッセージを延期するデータフロー ブロックを有効にする必要があるときに便利です。 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> メソッドは、データが利用できるようになったときにデータを操作する必要がある場合に便利です。 メッセージ ブロック間でメッセージが伝達されるしくみの詳細については、[データフロー](dataflow-task-parallel-library.md)に関するページの「Message Passing (メッセージ パッシング)」のセクションを参照してください。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="5":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="5":::

## <a name="a-complete-example"></a>コード例全体

次の例には、この記事のコードがすべて含まれています。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="1":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="1":::

## <a name="next-steps"></a>次のステップ

この例は、メッセージ ブロックからの読み取りとメッセージ ブロックへの書き込みを直接行う方法を示しています。 データフロー ブロックを接続して、データフロー ブロックのリニア シーケンスである "*パイプライン*" を作成するか、またはデータフロー ブロックのグラフである "*ネットワーク*" を作成することもできます。 パイプラインまたはネットワークでは、データが使用可能になると、ソースはターゲットに非同期的にデータを伝達します。 基本的なデータフロー パイプラインを作成する例については、「[Walkthrough: Creating a Dataflow Pipeline (チュートリアル: データフロー パイプラインの作成)](walkthrough-creating-a-dataflow-pipeline.md)」を参照してください。 さらに複雑なデータフロー ネットワークを作成する例については、「[Walkthrough: Using Dataflow in a Windows Forms Application (チュートリアル: Windows フォーム アプリケーションでのデータフローの使用)](walkthrough-using-dataflow-in-a-windows-forms-application.md)」を参照してください。

## <a name="see-also"></a>参照

- [データフロー (タスク並列ライブラリ)](dataflow-task-parallel-library.md)
