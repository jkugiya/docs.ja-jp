---
description: '詳細情報: MULTISET (Entity SQL)'
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: f963638d018299e1cae7435f6dd3b7eaf855b4eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696595"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="556cf-103">MULTISET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="556cf-103">MULTISET (Entity SQL)</span></span>

<span data-ttu-id="556cf-104">値のリストからマルチセットのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="556cf-104">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="556cf-105">MULTISET コンストラクターの値はすべて、互換性のある型 `T`である必要があります。</span><span class="sxs-lookup"><span data-stu-id="556cf-105">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="556cf-106">空のマルチセット コンストラクターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="556cf-106">Empty multiset constructors are not allowed.</span></span>

## <a name="syntax"></a><span data-ttu-id="556cf-107">構文</span><span class="sxs-lookup"><span data-stu-id="556cf-107">Syntax</span></span>

```sql
MULTISET ( expression [{, expression }] )
-- or
{ expression [{, expression }] }
```

## <a name="arguments"></a><span data-ttu-id="556cf-108">引数</span><span class="sxs-lookup"><span data-stu-id="556cf-108">Arguments</span></span>

`expression`  
 <span data-ttu-id="556cf-109">任意の有効な値のリスト。</span><span class="sxs-lookup"><span data-stu-id="556cf-109">Any valid list of values.</span></span>

## <a name="return-value"></a><span data-ttu-id="556cf-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="556cf-110">Return Value</span></span>

<span data-ttu-id="556cf-111">型 MULTISET\<T> のコレクション。</span><span class="sxs-lookup"><span data-stu-id="556cf-111">A collection of type MULTISET\<T>.</span></span>

## <a name="remarks"></a><span data-ttu-id="556cf-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="556cf-112">Remarks</span></span>

<!-- markdownlint-disable DOCSMD001 -->

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="556cf-113">には、行コンストラクター、オブジェクト コンストラクター、およびマルチセット (またはコレクション) コンストラクターの 3 種類のコンストラクターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="556cf-113">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="556cf-114">詳しくは、「[コンストラクター](constructing-types-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="556cf-114">For more information, see [Constructing Types](constructing-types-entity-sql.md).</span></span>

<span data-ttu-id="556cf-115">マルチセット コンストラクターは、値のリストからマルチセットのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="556cf-115">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="556cf-116">このコンストラクターの値はすべて、互換性のある型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="556cf-116">All the values in the constructor must be of a compatible type.</span></span>

<span data-ttu-id="556cf-117">たとえば、次の式は整数のマルチセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="556cf-117">For example, the following expression creates a multiset of integers.</span></span>

`MULTISET(1, 2, 3)`

`{1, 2, 3}`

> [!NOTE]
> <span data-ttu-id="556cf-118">入れ子になったマルチセット リテラルは、`{{1, 2, 3}}` のように、外側のマルチセットに含まれているマルチセット要素が 1 つである場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="556cf-118">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="556cf-119">複数のマルチセット要素が外側のマルチセットに含まれている場合 ( `{{1, 2}, {3, 4}}`など)、入れ子になったマルチセット リテラルはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="556cf-119">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>

## <a name="example"></a><span data-ttu-id="556cf-120">例</span><span class="sxs-lookup"><span data-stu-id="556cf-120">Example</span></span>

<span data-ttu-id="556cf-121">次の Entity SQL クエリでは、MULTISET 演算子を使用して、値のリストからマルチセットのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="556cf-121">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="556cf-122">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="556cf-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="556cf-123">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="556cf-123">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="556cf-124">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="556cf-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="556cf-125">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="556cf-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

[!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]

## <a name="see-also"></a><span data-ttu-id="556cf-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="556cf-126">See also</span></span>

- [<span data-ttu-id="556cf-127">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="556cf-127">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="556cf-128">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="556cf-128">Entity SQL Reference</span></span>](entity-sql-reference.md)
