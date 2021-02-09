---
description: '詳細情報: LIMIT (Entity SQL)'
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 873f3fd5ed83d04313aff92bf1f97e07001c3f08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748207"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="ffa5b-103">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ffa5b-103">LIMIT (Entity SQL)</span></span>

<span data-ttu-id="ffa5b-104">物理的なページングは、ORDER BY 句の LIMIT サブ句を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-104">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="ffa5b-105">LIMIT は ORDER BY 句と切り離して使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-105">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa5b-106">構文</span><span class="sxs-lookup"><span data-stu-id="ffa5b-106">Syntax</span></span>  
  
```sql  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ffa5b-107">引数</span><span class="sxs-lookup"><span data-stu-id="ffa5b-107">Arguments</span></span>  

 `n`  
 <span data-ttu-id="ffa5b-108">選択する項目の数。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-108">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="ffa5b-109">LIMIT 式のサブ句が ORDER BY 句に存在する場合、クエリは並べ替え順序に従って並べ替えられ、結果の行数は LIMIT 式によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-109">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="ffa5b-110">たとえば、LIMIT 5 は、結果セットを 5 つのインスタンスまたは行に制限します。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-110">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="ffa5b-111">LIMIT は機能的に TOP と等価ですが、LIMIT では ORDER BY 句が存在する必要がある点が異なります。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-111">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="ffa5b-112">SKIP および LIMIT は ORDER BY 句と共に別々に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-112">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffa5b-113">TOP 修飾子と SKIP サブ句が同じクエリ式内に存在する場合には、Entity Sql クエリは無効と見なされます。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-113">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="ffa5b-114">TOP 式を LIMIT 式に変更してクエリを記述し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-114">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffa5b-115">例</span><span class="sxs-lookup"><span data-stu-id="ffa5b-115">Example</span></span>  

 <span data-ttu-id="ffa5b-116">次の Entity SQL クエリでは、SELECT ステートメントで返されたオブジェクトの並べ替え順序の指定に ORDER BY 演算子を LIMIT と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-116">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="ffa5b-117">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ffa5b-118">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ffa5b-119">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ffa5b-120">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="ffa5b-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LIMIT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="ffa5b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffa5b-121">See also</span></span>

- [<span data-ttu-id="ffa5b-122">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="ffa5b-122">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="ffa5b-123">[方法: クエリの結果をページングする](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ffa5b-123">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="ffa5b-124">ページング</span><span class="sxs-lookup"><span data-stu-id="ffa5b-124">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="ffa5b-125">TOP</span><span class="sxs-lookup"><span data-stu-id="ffa5b-125">TOP</span></span>](top-entity-sql.md)
