---
description: '詳細情報: 定数式'
title: 定数式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 3c040918df4af6a0302d2435e3564e395044108e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724831"
---
# <a name="constant-expressions"></a><span data-ttu-id="443ee-103">定数式</span><span class="sxs-lookup"><span data-stu-id="443ee-103">Constant Expressions</span></span>

<span data-ttu-id="443ee-104">定数式は、定数値で構成されています。</span><span class="sxs-lookup"><span data-stu-id="443ee-104">A constant expression consists of a constant value.</span></span> <span data-ttu-id="443ee-105">定数値は、クライアント側で変換されることなく、コマンド ツリーの定数式に直接変換されます。</span><span class="sxs-lookup"><span data-stu-id="443ee-105">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="443ee-106">これには、定数値になる式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="443ee-106">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="443ee-107">したがって、定数にかかわるすべての式でデータ ソースの動作が、予期したとおりになります。</span><span class="sxs-lookup"><span data-stu-id="443ee-107">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="443ee-108">これは CLR の動作とは異なる結果となります。</span><span class="sxs-lookup"><span data-stu-id="443ee-108">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="443ee-109">次の例では、サーバーで評価される定数式を示します。</span><span class="sxs-lookup"><span data-stu-id="443ee-109">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="443ee-110">LINQ to Entities では、ユーザー クラスを定数として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="443ee-110">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="443ee-111">ただし、ユーザー クラスのプロパティ参照は定数と見なされます。そのため、コマンド ツリーの定数式に変換され、データ ソースで実行されます。</span><span class="sxs-lookup"><span data-stu-id="443ee-111">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443ee-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="443ee-112">See also</span></span>

- [<span data-ttu-id="443ee-113">LINQ to Entities クエリ内の式</span><span class="sxs-lookup"><span data-stu-id="443ee-113">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
