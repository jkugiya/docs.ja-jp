---
description: '詳細情報: 方法:シーケンシャルな結果形状が割り当てられたストアド プロシージャを使用する'
title: '方法: シーケンシャルな結果形状が割り当てられたストアド プロシージャを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 3b5791875a7beb5a0c702e787e775cd528ab2517
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738768"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="387fe-103">方法: シーケンシャルな結果形状が割り当てられたストアド プロシージャを使用する</span><span class="sxs-lookup"><span data-stu-id="387fe-103">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>

<span data-ttu-id="387fe-104">この種類のストアド プロシージャでは、複数の結果形状が生成されますが、どの順序で結果が返されるかがわかります。</span><span class="sxs-lookup"><span data-stu-id="387fe-104">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="387fe-105">このシナリオは、返される結果のシーケンスがわからないシナリオと対照的です。</span><span class="sxs-lookup"><span data-stu-id="387fe-105">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="387fe-106">詳細については、[複数の結果形状が割り当てられたストアド プロシージャを使用する](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="387fe-106">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="387fe-107">例</span><span class="sxs-lookup"><span data-stu-id="387fe-107">Example</span></span>  

 <span data-ttu-id="387fe-108">次は、複数の結果形状をシーケンシャルに返すストアド プロシージャの T-SQL です。</span><span class="sxs-lookup"><span data-stu-id="387fe-108">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```sql
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="387fe-109">例</span><span class="sxs-lookup"><span data-stu-id="387fe-109">Example</span></span>  

 <span data-ttu-id="387fe-110">このストアド プロシージャを実行するには、次のようなコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="387fe-110">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="387fe-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="387fe-111">See also</span></span>

- [<span data-ttu-id="387fe-112">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="387fe-112">Stored Procedures</span></span>](stored-procedures.md)
