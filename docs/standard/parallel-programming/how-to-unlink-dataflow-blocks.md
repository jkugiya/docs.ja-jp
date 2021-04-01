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
# <a name="how-to-unlink-dataflow-blocks"></a>方法:データ フロー ブロックのリンクを解除する

このドキュメントでは、ソースからターゲット データフロー ブロックのリンクを解除する方法について説明します。

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>例  

 次の例では、3 つの <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> オブジェクトを作成し、それぞれのオブジェクトが値を計算する `TrySolution` メソッドを呼び出します。 この例は、完了させるために、`TrySolution` に対する最初の呼び出しからの結果のみが必要です。  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 完了した最初の <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> オブジェクトの結果を受信するために、この例では `ReceiveFromAny(T)` メソッドを定義します。 `ReceiveFromAny(T)` メソッドは、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> オブジェクトの配列を受け取り、これらの各オブジェクトと <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトをリンクさせます。 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> メソッドを使用してソース データフロー ブロックをターゲット ブロックにリンクさせると、データが使用可能になったときにソースがターゲットにメッセージを反映させます。 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> クラスは提供される最初のメッセージのみを受け取るため、`ReceiveFromAny(T)` メソッドは <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> メソッドを呼び出して、その結果を生成します。 これにより、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトに提供される最初のメッセージが生成されます。 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> メソッドには、<xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> オブジェクトと <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> プロパティを取得するオーバーロードされたバージョンがあります。そのプロパティを `1` に設定すると、ソースからターゲットに 1 つのメッセージが届いた後に、ターゲットとのリンクを解除するようにソース ブロックに指示が出されます。 ソースの配列と <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトの関係は、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトがメッセージを受信した後は必要なくなるため、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトにはそのソースからリンクを解除することが重要です。  
  
 いずれかで値を計算した後に、`TrySolution` への残りの呼び出しを終了できるようにするには、`TrySolution` メソッドは `ReceiveFromAny(T)` への呼び出しが返された後にキャンセルされる、<xref:System.Threading.CancellationToken> オブジェクトを取得します。 <xref:System.Threading.SpinWait.SpinUntil%2A> メソッドは、この <xref:System.Threading.CancellationToken> オブジェクトがキャンセルされたときに返されます。  
  
## <a name="see-also"></a>関連項目

- [データフロー](dataflow-task-parallel-library.md)
