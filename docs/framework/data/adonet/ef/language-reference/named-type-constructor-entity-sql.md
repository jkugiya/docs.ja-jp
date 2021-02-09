---
description: '詳細情報: 名前付きの型コンストラクター (Entity SQL)'
title: 名前付きの型コンストラクター (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: e5ec811f814898661cf8de28de1fb8406647332d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696543"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="c712b-103">名前付きの型コンストラクター (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c712b-103">Named Type Constructor (Entity SQL)</span></span>

<span data-ttu-id="c712b-104">エンティティ型や複合型など、概念モデル標準型のインスタンスの作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="c712b-104">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c712b-105">構文</span><span class="sxs-lookup"><span data-stu-id="c712b-105">Syntax</span></span>  
  
```sql  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="c712b-106">引数</span><span class="sxs-lookup"><span data-stu-id="c712b-106">Arguments</span></span>  

 `identifier`  
 <span data-ttu-id="c712b-107">単純な識別子および引用符で囲まれた識別子の値。</span><span class="sxs-lookup"><span data-stu-id="c712b-107">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="c712b-108">詳しくは、「[識別子](identifiers-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c712b-108">For more information see, [Identifiers](identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="c712b-109">型の宣言に表示される順序と同じ順序であると見なされる型の属性。</span><span class="sxs-lookup"><span data-stu-id="c712b-109">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c712b-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="c712b-110">Return Value</span></span>  

 <span data-ttu-id="c712b-111">名前付きの複合型とエンティティ型のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="c712b-111">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c712b-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="c712b-112">Remarks</span></span>  

 <span data-ttu-id="c712b-113">次の例は、標準型と複合型を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c712b-113">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="c712b-114">次の式は、 `Person` 型のインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="c712b-114">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="c712b-115">次の式は、複合型のインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="c712b-115">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="c712b-116">次の式は、入れ子になった複合型のインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="c712b-116">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="c712b-117">次の式は、入れ子になった複合型を持つエンティティのインスタンスを作成する式です。</span><span class="sxs-lookup"><span data-stu-id="c712b-117">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="c712b-118">次の例は、複合型のプロパティを null に初期化する方法を示しています。`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="c712b-118">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="c712b-119">例</span><span class="sxs-lookup"><span data-stu-id="c712b-119">Example</span></span>  

 <span data-ttu-id="c712b-120">次の Entity SQL クエリでは、名前付きの型コンストラクターを使用して、概念モデル型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c712b-120">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="c712b-121">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="c712b-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c712b-122">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c712b-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c712b-123">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c712b-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c712b-124">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="c712b-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NAMED_TYPE_CONSTRUCTOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="c712b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="c712b-125">See also</span></span>

- [<span data-ttu-id="c712b-126">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="c712b-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="c712b-127">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="c712b-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
