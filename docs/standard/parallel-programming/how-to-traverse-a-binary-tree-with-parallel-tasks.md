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
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="a9abd-103">方法:並列タスクでバイナリ ツリーを走査する</span><span class="sxs-lookup"><span data-stu-id="a9abd-103">How to: Traverse a Binary Tree with Parallel Tasks</span></span>

<span data-ttu-id="a9abd-104">次の例では、ツリー データ構造を走査する並列タスクを使用する 2 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a9abd-104">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="a9abd-105">ツリー自体の作成は、演習として残しておきます。</span><span class="sxs-lookup"><span data-stu-id="a9abd-105">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9abd-106">例</span><span class="sxs-lookup"><span data-stu-id="a9abd-106">Example</span></span>  

 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="a9abd-107">示した 2 つのメソッドは、機能的に同等です。</span><span class="sxs-lookup"><span data-stu-id="a9abd-107">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="a9abd-108">タスクを作成して実行するために、<xref:System.Threading.Tasks.TaskFactory.StartNew%2A> メソッドを使用すると、タスクで待機し、例外を処理するために使用するタスクからハンドルを戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="a9abd-108">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9abd-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9abd-109">See also</span></span>

- [<span data-ttu-id="a9abd-110">タスク並列ライブラリ (TPL)</span><span class="sxs-lookup"><span data-stu-id="a9abd-110">Task Parallel Library (TPL)</span></span>](task-parallel-library-tpl.md)
