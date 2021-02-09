---
description: '詳細情報: 方法:複数の結果形状が割り当てられたストアド プロシージャを使用する'
title: '方法: 複数の結果形状が割り当てられたストアド プロシージャを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 9faf80e565656120a2601b30424df80ca10913e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785823"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="72c88-103">方法: 複数の結果形状が割り当てられたストアド プロシージャを使用する</span><span class="sxs-lookup"><span data-stu-id="72c88-103">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>

<span data-ttu-id="72c88-104">複数の結果形状を返すことができるストアド プロシージャの場合、戻り値の型を単一の射影形状として厳密に型指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="72c88-104">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="72c88-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では可能なすべてのプロジェクション型を生成できますが、返される順序を知ることはできません。</span><span class="sxs-lookup"><span data-stu-id="72c88-105">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="72c88-106">このシナリオと対照的なのが、複数の結果形状をシーケンシャルに生成するストアド プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="72c88-106">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="72c88-107">詳細については、[シーケンシャルな結果形状が割り当てられたストアド プロシージャを使用する](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72c88-107">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="72c88-108">複数の結果型を返すストアド プロシージャには、プロシージャが返す可能性のある一連の型を示す <xref:System.Data.Linq.Mapping.ResultTypeAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="72c88-108">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72c88-109">例</span><span class="sxs-lookup"><span data-stu-id="72c88-109">Example</span></span>  

 <span data-ttu-id="72c88-110">次の SQL コードの例では、結果形状は入力値 (`shape =1` または `shape = 2`) に応じて変わります。</span><span class="sxs-lookup"><span data-stu-id="72c88-110">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="72c88-111">どちらの射影が先に返されるかはわかりません。</span><span class="sxs-lookup"><span data-stu-id="72c88-111">You do not know which projection will be returned first.</span></span>  
  
``` sql
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="72c88-112">例</span><span class="sxs-lookup"><span data-stu-id="72c88-112">Example</span></span>  

 <span data-ttu-id="72c88-113">このストアド プロシージャを実行するには、次のようなコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="72c88-113">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72c88-114">ストアド プロシージャに対する知識に基づいて、<xref:System.Data.Linq.IMultipleResults.GetResult%2A> パターンを使用し、正しい型の列挙子を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72c88-114">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="72c88-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="72c88-115">See also</span></span>

- [<span data-ttu-id="72c88-116">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="72c88-116">Stored Procedures</span></span>](stored-procedures.md)
