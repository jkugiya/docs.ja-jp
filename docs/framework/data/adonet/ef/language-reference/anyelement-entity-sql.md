---
description: '詳細情報: ANYELEMENT (Entity SQL)'
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 3330c1b0bed69084bc83c5a689762ff529539d54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697154"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="f61cd-103">ANYELEMENT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f61cd-103">ANYELEMENT (Entity SQL)</span></span>

<span data-ttu-id="f61cd-104">複数値のコレクションから要素を抽出します。</span><span class="sxs-lookup"><span data-stu-id="f61cd-104">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f61cd-105">構文</span><span class="sxs-lookup"><span data-stu-id="f61cd-105">Syntax</span></span>  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="f61cd-106">引数</span><span class="sxs-lookup"><span data-stu-id="f61cd-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="f61cd-107">要素の抽出元のコレクションを返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="f61cd-107">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f61cd-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f61cd-108">Return Value</span></span>  

 <span data-ttu-id="f61cd-109">コレクションに複数の要素が存在する場合はコレクション内の単一の要素 (任意の要素) が、コレクションが空の場合は `null`が返されます。</span><span class="sxs-lookup"><span data-stu-id="f61cd-109">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="f61cd-110">`collection` が `Collection<T>` 型のコレクションである場合、`ANYELEMENT(collection)` は `T` 型のインスタンスを生成する有効な式です。</span><span class="sxs-lookup"><span data-stu-id="f61cd-110">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f61cd-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f61cd-111">Remarks</span></span>  

 <span data-ttu-id="f61cd-112">ANYELEMENT では、複数値のコレクションから任意の要素が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="f61cd-112">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="f61cd-113">たとえば、次の例では、 `Customers`という集合から単一の要素が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="f61cd-113">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="f61cd-114">例</span><span class="sxs-lookup"><span data-stu-id="f61cd-114">Example</span></span>  

 <span data-ttu-id="f61cd-115">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、ANYELEMENT 演算子を使用して、複数値のコレクションから要素を抽出します。</span><span class="sxs-lookup"><span data-stu-id="f61cd-115">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="f61cd-116">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f61cd-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f61cd-117">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f61cd-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f61cd-118">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f61cd-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f61cd-119">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="f61cd-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="f61cd-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f61cd-120">See also</span></span>

- [<span data-ttu-id="f61cd-121">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="f61cd-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f61cd-122">NULL 値が許容される構造化型</span><span class="sxs-lookup"><span data-stu-id="f61cd-122">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
