---
description: '詳細情報: 方法:ユーザー定義関数をインラインで呼び出す'
title: '方法: ユーザー定義関数をインラインで呼び出す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 2a7cf185af05a1ed58a2dd3b365a5bbcaa2a4fd5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786057"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="80872-103">方法: ユーザー定義関数をインラインで呼び出す</span><span class="sxs-lookup"><span data-stu-id="80872-103">How to: Call User-Defined Functions Inline</span></span>

<span data-ttu-id="80872-104">ユーザー定義関数はインラインで呼び出すことができますが、遅延実行のクエリに含まれる関数は、そのクエリが実行されるまで実行されません。</span><span class="sxs-lookup"><span data-stu-id="80872-104">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="80872-105">詳細については、「[LINQ クエリの概要 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80872-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="80872-106">同じ関数をクエリの外部で呼び出すと、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって、メソッド呼び出し式から単純なクエリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="80872-106">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="80872-107">この SQL 構文を次に示します (`@p0` パラメーターは渡される定数にバインドされます)。</span><span class="sxs-lookup"><span data-stu-id="80872-107">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```sql  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="80872-108">によって、次の結果が作成されます。</span><span class="sxs-lookup"><span data-stu-id="80872-108">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="80872-109">例</span><span class="sxs-lookup"><span data-stu-id="80872-109">Example</span></span>  

 <span data-ttu-id="80872-110">次の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のクエリでは、生成されたユーザー定義関数メソッド `ReverseCustName` のインライン呼び出しを確認できます。</span><span class="sxs-lookup"><span data-stu-id="80872-110">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="80872-111">クエリは遅延実行されるので、この関数は即座には実行されません。</span><span class="sxs-lookup"><span data-stu-id="80872-111">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="80872-112">このクエリ用に作成される SQL は、データベース内のユーザー定義関数の呼び出しに変換されます (クエリの後の SQL コードを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="80872-112">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```sql  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="80872-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="80872-113">See also</span></span>

- [<span data-ttu-id="80872-114">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="80872-114">User-Defined Functions</span></span>](user-defined-functions.md)
