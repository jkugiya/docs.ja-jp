---
description: '詳細情報: CAST (Entity SQL)'
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: f6a90c0ec2557391c2da6e46511a020f90d32ab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739483"
---
# <a name="cast-entity-sql"></a><span data-ttu-id="acbba-103">CAST (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="acbba-103">CAST (Entity SQL)</span></span>

<span data-ttu-id="acbba-104">あるデータ型の式を別のデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="acbba-104">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acbba-105">構文</span><span class="sxs-lookup"><span data-stu-id="acbba-105">Syntax</span></span>  
  
```csharp
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="acbba-106">引数</span><span class="sxs-lookup"><span data-stu-id="acbba-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="acbba-107">`data_type`に変換できる任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="acbba-107">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="acbba-108">対象システムで提供されるデータ型。</span><span class="sxs-lookup"><span data-stu-id="acbba-108">The target system-supplied data type.</span></span> <span data-ttu-id="acbba-109">プリミティブ (スカラー) 型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="acbba-109">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="acbba-110">使用される `data_type` は、クエリのスペースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="acbba-110">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="acbba-111">クエリが <xref:System.Data.EntityClient.EntityCommand>で実行される場合、データ型は概念モデルで定義された型です。</span><span class="sxs-lookup"><span data-stu-id="acbba-111">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="acbba-112">詳細については、「 [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acbba-112">For more information, see [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span> <span data-ttu-id="acbba-113">クエリが <xref:System.Data.Objects.ObjectQuery%601>で実行される場合、データ型は共通言語ランタイム (CLR) 型です。</span><span class="sxs-lookup"><span data-stu-id="acbba-113">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acbba-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="acbba-114">Return Value</span></span>  

 <span data-ttu-id="acbba-115">`data_type`と同じ値を返します。</span><span class="sxs-lookup"><span data-stu-id="acbba-115">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acbba-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="acbba-116">Remarks</span></span>  

 <span data-ttu-id="acbba-117">キャスト式のセマンティクスは、Transact-SQL の CONVERT 式と似ています。</span><span class="sxs-lookup"><span data-stu-id="acbba-117">The cast expression has similar semantics to the Transact-SQL CONVERT expression.</span></span> <span data-ttu-id="acbba-118">キャスト式は、ある型の値を別の型の値に変換する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="acbba-118">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```csharp
CAST( e as T )  
```  
  
 <span data-ttu-id="acbba-119">e が S 型で、S を T に変換できる場合、上記の式は有効なキャスト式です。</span><span class="sxs-lookup"><span data-stu-id="acbba-119">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="acbba-120">T はプリミティブ (スカラー) 型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="acbba-120">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="acbba-121">`Edm.Decimal`にキャストする場合は、オプションで精度と小数点以下桁数のファセットの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="acbba-121">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="acbba-122">明示的に指定しない場合、精度と小数点以下桁数の既定値はそれぞれ 18 と 0 です。</span><span class="sxs-lookup"><span data-stu-id="acbba-122">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="acbba-123">具体的には、 `Decimal`で次のオーバーロードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="acbba-123">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="acbba-124">キャスト式の使用は明示的な変換と見なされます。</span><span class="sxs-lookup"><span data-stu-id="acbba-124">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="acbba-125">明示的な変換では、データが切り捨てられたり、精度が失われたりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="acbba-125">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acbba-126">CAST はプリミティブ型と列挙メンバー型のみでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="acbba-126">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acbba-127">例</span><span class="sxs-lookup"><span data-stu-id="acbba-127">Example</span></span>  

 <span data-ttu-id="acbba-128">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリは CAST 演算子を使用して、あるデータ型の式を別のデータ型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="acbba-128">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="acbba-129">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="acbba-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="acbba-130">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="acbba-130">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="acbba-131">「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="acbba-131">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="acbba-132">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="acbba-132">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="acbba-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="acbba-133">See also</span></span>

- [<span data-ttu-id="acbba-134">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="acbba-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
