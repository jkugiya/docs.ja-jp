---
description: '詳細情報: REF (Entity SQL)'
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 05f87ce8027e8e095722eb13d39f3f13d56f6faa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802061"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="ef085-103">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ef085-103">REF (Entity SQL)</span></span>

<span data-ttu-id="ef085-104">エンティティ インスタンスへの参照を返します。</span><span class="sxs-lookup"><span data-stu-id="ef085-104">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef085-105">構文</span><span class="sxs-lookup"><span data-stu-id="ef085-105">Syntax</span></span>  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a><span data-ttu-id="ef085-106">引数</span><span class="sxs-lookup"><span data-stu-id="ef085-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="ef085-107">エンティティ型のインスタンスを生成する任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="ef085-107">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef085-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ef085-108">Return Value</span></span>  

 <span data-ttu-id="ef085-109">指定されたエンティティ インスタンスへの参照。</span><span class="sxs-lookup"><span data-stu-id="ef085-109">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef085-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="ef085-110">Remarks</span></span>  

 <span data-ttu-id="ef085-111">エンティティ参照は、エンティティ キーとエンティティ セット名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ef085-111">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="ef085-112">異なるエンティティ セットが同じエンティティ型に基づくことができるので、特定のエンティティ キーが複数のエンティティ セットで使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ef085-112">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="ef085-113">ただし、エンティティ参照は常に一意です。</span><span class="sxs-lookup"><span data-stu-id="ef085-113">However, an entity reference is always unique.</span></span> <span data-ttu-id="ef085-114">入力式が永続エンティティを表す場合、このエンティティへの参照が返されます。</span><span class="sxs-lookup"><span data-stu-id="ef085-114">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="ef085-115">入力式が永続エンティティではない場合は、NULL 参照が返されます。</span><span class="sxs-lookup"><span data-stu-id="ef085-115">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="ef085-116">プロパティ抽出演算子 (.) を使用してエンティティのプロパティにアクセスすると、参照は自動的に逆参照されます。</span><span class="sxs-lookup"><span data-stu-id="ef085-116">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef085-117">例</span><span class="sxs-lookup"><span data-stu-id="ef085-117">Example</span></span>  

 <span data-ttu-id="ef085-118">次の Entity SQL クエリは、REF 演算子を使用して入力エンティティ引数の参照を返します。</span><span class="sxs-lookup"><span data-stu-id="ef085-118">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="ef085-119">プロパティ抽出演算子 (.) を使用して Product エンティティのプロパティにアクセスすることにより、同じクエリでこの参照が逆参照されます。</span><span class="sxs-lookup"><span data-stu-id="ef085-119">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="ef085-120">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ef085-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ef085-121">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ef085-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ef085-122">「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ef085-122">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="ef085-123">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="ef085-123">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="ef085-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef085-124">See also</span></span>

- [<span data-ttu-id="ef085-125">DEREF</span><span class="sxs-lookup"><span data-stu-id="ef085-125">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="ef085-126">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="ef085-126">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="ef085-127">KEY</span><span class="sxs-lookup"><span data-stu-id="ef085-127">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="ef085-128">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="ef085-128">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ef085-129">型定義</span><span class="sxs-lookup"><span data-stu-id="ef085-129">Type Definitions</span></span>](type-definitions-entity-sql.md)
