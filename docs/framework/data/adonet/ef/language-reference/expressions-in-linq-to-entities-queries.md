---
description: '詳細情報: LINQ to Entities クエリ内の式'
title: LINQ to Entities クエリ内の式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 3ab9e04adb7e823538638ae262f0e481b6948a24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786369"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="f5d43-103">LINQ to Entities クエリ内の式</span><span class="sxs-lookup"><span data-stu-id="f5d43-103">Expressions in LINQ to Entities Queries</span></span>

<span data-ttu-id="f5d43-104">式は、単一の値、オブジェクト、メソッド、または名前空間として評価されるコード フラグメントです。</span><span class="sxs-lookup"><span data-stu-id="f5d43-104">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="f5d43-105">式には、リテラル値、メソッド呼び出し、演算子とそのオペランド、または単純な名前を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f5d43-105">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="f5d43-106">単純な名前には、変数、型メンバー、メソッド パラメーター、名前空間、または型の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f5d43-106">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="f5d43-107">式では、他の式をパラメーターとして使用する演算子、またはパラメーターが他のメソッド呼び出しであるメソッド呼び出しを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5d43-107">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="f5d43-108">したがって、単純な式だけでなく、非常に複雑な式も作成できます。</span><span class="sxs-lookup"><span data-stu-id="f5d43-108">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="f5d43-109">LINQ to Entities のクエリの式では、ラムダ式など、<xref:System.Linq.Expressions> 名前空間内の型で許容されている要素であれば何でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5d43-109">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="f5d43-110">LINQ to Entities のクエリで使用可能な式は、Entity Framework のクエリに使用可能な式のスーパーセットです。Entity Framework に対するクエリの一部である式は、`ObjectQuery<T>` および基になるデータ ソースでサポートされている演算に制限されます。</span><span class="sxs-lookup"><span data-stu-id="f5d43-110">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the Entity Framework.Expressions that are part of queries against the Entity Framework are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="f5d43-111">次の例では、`Where` 句で使用される比較の式を示します。</span><span class="sxs-lookup"><span data-stu-id="f5d43-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="f5d43-112">C# の `unchecked` などの特殊な言語構造は、LINQ to Entities では意味がありません。</span><span class="sxs-lookup"><span data-stu-id="f5d43-112">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5d43-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f5d43-113">In This Section</span></span>  

 [<span data-ttu-id="f5d43-114">定数式</span><span class="sxs-lookup"><span data-stu-id="f5d43-114">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="f5d43-115">比較式</span><span class="sxs-lookup"><span data-stu-id="f5d43-115">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="f5d43-116">NULL 比較</span><span class="sxs-lookup"><span data-stu-id="f5d43-116">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="f5d43-117">初期化式</span><span class="sxs-lookup"><span data-stu-id="f5d43-117">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="f5d43-118">リレーションシップ、ナビゲーション プロパティ、および外部キー</span><span class="sxs-lookup"><span data-stu-id="f5d43-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="f5d43-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5d43-119">See also</span></span>

- [<span data-ttu-id="f5d43-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="f5d43-120">ADO.NET Entity Framework</span></span>](../index.md)
