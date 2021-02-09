---
description: '詳細情報: 方法:クエリで複合キーを処理する'
title: '方法: クエリで複合キーを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 9d7c68495810bee6a383d98a75694e7cd24f1015
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738872"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="a6572-103">方法: クエリで複合キーを処理する</span><span class="sxs-lookup"><span data-stu-id="a6572-103">How to: Handle Composite Keys in Queries</span></span>

<span data-ttu-id="a6572-104">演算子によっては、引数を 1 つしか受け取らないものがあります。</span><span class="sxs-lookup"><span data-stu-id="a6572-104">Some operators can take only one argument.</span></span> <span data-ttu-id="a6572-105">1 つの演算子にデータベースの複数の列を含めるには、その組み合わせを表す匿名型を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6572-105">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6572-106">例</span><span class="sxs-lookup"><span data-stu-id="a6572-106">Example</span></span>  

 <span data-ttu-id="a6572-107">`GroupBy` 演算子を使用するクエリを次の例に示します。この演算子は、1 つの `key` 引数だけを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a6572-107">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="a6572-108">例</span><span class="sxs-lookup"><span data-stu-id="a6572-108">Example</span></span>  

 <span data-ttu-id="a6572-109">次の例に示すように、結合の場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="a6572-109">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a6572-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6572-110">See also</span></span>

- [<span data-ttu-id="a6572-111">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="a6572-111">Query Concepts</span></span>](query-concepts.md)
