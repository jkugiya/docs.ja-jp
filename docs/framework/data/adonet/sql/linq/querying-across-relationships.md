---
description: '詳細情報: リレーションシップを介したクエリの実行'
title: リレーションシップを介したクエリの実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: a29a24b21cc486f59ae7535db0e5f97831249ee0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695256"
---
# <a name="querying-across-relationships"></a><span data-ttu-id="461fe-103">リレーションシップを介したクエリの実行</span><span class="sxs-lookup"><span data-stu-id="461fe-103">Querying Across Relationships</span></span>

<span data-ttu-id="461fe-104">他のオブジェクトまたは他のオブジェクトのコレクションをクラス定義内で参照することは、データベース内の外部キー リレーションシップに直接対応します。</span><span class="sxs-lookup"><span data-stu-id="461fe-104">References to other objects or collections of other objects in your class definitions directly correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="461fe-105">クエリを実行するときにこのリレーションシップを使用するには、ドット表記を使ってリレーションシップ プロパティにアクセスし、オブジェクト間を移動します。</span><span class="sxs-lookup"><span data-stu-id="461fe-105">You can use these relationships when you query by using dot notation to access the relationship properties and navigate from one object to another.</span></span> <span data-ttu-id="461fe-106">これらのアクセス操作は、SQL で同等の複雑な結合または相関サブクエリとして変換されます。</span><span class="sxs-lookup"><span data-stu-id="461fe-106">These access operations translate to more complex joins or correlated subqueries in the equivalent SQL.</span></span>  
  
 <span data-ttu-id="461fe-107">たとえば、次のクエリでは、ロンドン在住の顧客からの注文のみが結果として得られるように注文から顧客へと移動します。</span><span class="sxs-lookup"><span data-stu-id="461fe-107">For example, the following query navigates from orders to customers as a way to restrict the results to only those orders for customers located in London.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 <span data-ttu-id="461fe-108">リレーションシップのプロパティが存在しない場合は、SQL クエリの場合と同じように "*結合*" として、手動で記述する必要があります。次にコードの例を示します。</span><span class="sxs-lookup"><span data-stu-id="461fe-108">If relationship properties did not exist you would have to write them manually as *joins*, just as you would do in a SQL query, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 <span data-ttu-id="461fe-109">"*リレーションシップ*" のプロパティを使用すると、このようなリレーションシップを一度で定義できます。</span><span class="sxs-lookup"><span data-stu-id="461fe-109">You can use the *relationship* property to define this particular relationship one time.</span></span> <span data-ttu-id="461fe-110">こうすると、使いやすいドット構文を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="461fe-110">You can then use the more convenient dot syntax.</span></span> <span data-ttu-id="461fe-111">しかし、それだけがリレーションシップ プロパティの利点ではありません。なぜなら、通常はドメイン固有のオブジェクト モデルは階層構造またはグラフとして定義されるからです。</span><span class="sxs-lookup"><span data-stu-id="461fe-111">But relationship properties exist more importantly because domain-specific object models are typically defined as hierarchies or graphs.</span></span> <span data-ttu-id="461fe-112">プログラムで使用するオブジェクトには他のオブジェクトへの参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="461fe-112">The objects that you program against have references to other objects.</span></span> <span data-ttu-id="461fe-113">このオブジェクト間リレーションシップがデータベースの外部キー型リレーションシップに相当するのは、単なる幸運な偶然です。</span><span class="sxs-lookup"><span data-stu-id="461fe-113">It is only a happy coincidence that object-to-object relationships correspond to foreign-key-styled relationships in databases.</span></span> <span data-ttu-id="461fe-114">プロパティへのアクセスは、結合を記述するための便利な方法となります。</span><span class="sxs-lookup"><span data-stu-id="461fe-114">Property access then provides a convenient way to write joins.</span></span>  
  
 <span data-ttu-id="461fe-115">この点では、リレーションシップ プロパティは、クエリそのものよりもクエリの結果でより重要です。</span><span class="sxs-lookup"><span data-stu-id="461fe-115">With regard to this, relationship properties are more important on the results side of a query than as part of the query itself.</span></span> <span data-ttu-id="461fe-116">クエリによって特定の顧客に関するデータが取得された後で、クラス定義ではその顧客の注文が存在することが示されます。</span><span class="sxs-lookup"><span data-stu-id="461fe-116">After the query has retrieved data about a particular customer, the class definition indicates that customers have orders.</span></span> <span data-ttu-id="461fe-117">つまり、特定の顧客の `Orders` プロパティにその顧客のすべての注文が含まれると見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="461fe-117">In other words, you expect the `Orders` property of a particular customer to be a collection that is populated with all the orders from that customer.</span></span> <span data-ttu-id="461fe-118">実際には、これはクラスをこのように定義することにより宣言したコントラクトです。</span><span class="sxs-lookup"><span data-stu-id="461fe-118">That is in fact the contract you declared by defining the classes in this manner.</span></span> <span data-ttu-id="461fe-119">クエリによって注文が要求されなかった場合でも、ここに注文が含まれていると見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="461fe-119">You expect to see the orders there even if the query did not request orders.</span></span> <span data-ttu-id="461fe-120">オブジェクト モデルに対して期待されるのは、それがデータベースがメモリ内に拡張されたものであり、関連オブジェクトがすぐに使用できる状態にある、という錯覚を維持することです。</span><span class="sxs-lookup"><span data-stu-id="461fe-120">You expect your object model to maintain an illusion that it is an in-memory extension of the database with related objects immediately available.</span></span>  
  
 <span data-ttu-id="461fe-121">リレーションシップが得られたので、クラスに定義されたリレーションシップ プロパティを参照してクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="461fe-121">Now that you have relationships, you can write queries by referring to the relationship properties defined in your classes.</span></span> <span data-ttu-id="461fe-122">これらのリレーションシップ参照は、データベース内の外部キー リレーションシップに対応します。</span><span class="sxs-lookup"><span data-stu-id="461fe-122">These relationship references correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="461fe-123">これらのリレーションシップを使用する操作は、SQL で同等の複雑な結合として変換されます。</span><span class="sxs-lookup"><span data-stu-id="461fe-123">Operations that use these relationships translate to more complex joins in the equivalent SQL.</span></span> <span data-ttu-id="461fe-124"><xref:System.Data.Linq.Mapping.AssociationAttribute> 属性を使用してリレーションシップを定義している限りは、明示的な結合を [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="461fe-124">As long as you have defined a relationship (using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute), you do not have to code an explicit join in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="461fe-125">この錯覚を維持するために、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] には "*遅延読み込み*" と呼ばれる機能が実装されています。</span><span class="sxs-lookup"><span data-stu-id="461fe-125">To help maintain this illusion, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implements a technique called *deferred loading*.</span></span> <span data-ttu-id="461fe-126">詳細については、「[遅延読み込みと即時読み込み](deferred-versus-immediate-loading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="461fe-126">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
 <span data-ttu-id="461fe-127">`CustomerID`-`OrderID` ペアのリストを投影する次のような SQL クエリがあるとします。</span><span class="sxs-lookup"><span data-stu-id="461fe-127">Consider the following SQL query to project a list of `CustomerID`-`OrderID` pairs:</span></span>  
  
```sql
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 <span data-ttu-id="461fe-128">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して同じ結果を得るには、`Orders` クラスに既に存在する `Customer` プロパティ参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="461fe-128">To obtain the same results by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the `Orders` property reference already existing in the `Customer` class.</span></span> <span data-ttu-id="461fe-129">次のコードに示すとおり、`Orders` の参照からは、クエリを実行し、`CustomerID`-`OrderID` ペアを投影するために必要な情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="461fe-129">The `Orders` reference provides the necessary information to execute the query and project the `CustomerID`-`OrderID` pairs, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 <span data-ttu-id="461fe-130">逆の操作も可能です。</span><span class="sxs-lookup"><span data-stu-id="461fe-130">You can also do the reverse.</span></span> <span data-ttu-id="461fe-131">つまり、`Orders` にクエリを実行し、その `Customer` リレーションシップ参照を使用して、関連付けられた `Customer` オブジェクトに関する情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="461fe-131">That is, you can query `Orders` and use its `Customer` relationship reference to access information about the associated `Customer` object.</span></span> <span data-ttu-id="461fe-132">次のコードでは、前の例と同じ `CustomerID`-`OrderID` ペアが投影されますが、ここでは `Customers` ではなく `Orders` のクエリを実行しています。</span><span class="sxs-lookup"><span data-stu-id="461fe-132">The following code projects the same `CustomerID`-`OrderID` pairs as before, but this time by querying `Orders` instead of `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="461fe-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="461fe-133">See also</span></span>

- [<span data-ttu-id="461fe-134">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="461fe-134">Query Concepts</span></span>](query-concepts.md)
