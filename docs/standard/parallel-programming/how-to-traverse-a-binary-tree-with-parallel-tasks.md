---
description: '詳細情報: 並列タスクでバイナリ ツリーを走査する方法'
title: 方法:並列タスクでバイナリ ツリーを走査する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
ms.openlocfilehash: f6b053bb9b480e85698dcd098a750d38d2ef403a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629540"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>方法:並列タスクでバイナリ ツリーを走査する

次の例では、ツリー データ構造を走査する並列タスクを使用する 2 つの方法を示します。 ツリー自体の作成は、演習として残しておきます。  
  
## <a name="example"></a>例  

 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 示した 2 つのメソッドは、機能的に同等です。 タスクを作成して実行するために、<xref:System.Threading.Tasks.TaskFactory.StartNew%2A> メソッドを使用すると、タスクで待機し、例外を処理するために使用するタスクからハンドルを戻すことができます。  
  
## <a name="see-also"></a>関連項目

- [タスク並列ライブラリ (TPL)](task-parallel-library-tpl.md)
