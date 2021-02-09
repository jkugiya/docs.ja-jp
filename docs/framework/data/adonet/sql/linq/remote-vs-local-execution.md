---
description: '詳細情報: クエリのリモート実行とローカル実行'
title: クエリのリモート実行とローカル実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: ea4d85faedd4a299da292029e64d77132e1a65a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695196"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="686b5-103">クエリのリモート実行とローカル実行</span><span class="sxs-lookup"><span data-stu-id="686b5-103">Remote vs. Local Execution</span></span>

<span data-ttu-id="686b5-104">クエリは、リモートで実行することも (データベース エンジンによるデータベースに対するクエリの実行)、ローカルに実行することも ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によるローカル キャッシュに対するクエリの実行) できます。</span><span class="sxs-lookup"><span data-stu-id="686b5-104">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="686b5-105">リモート実行</span><span class="sxs-lookup"><span data-stu-id="686b5-105">Remote Execution</span></span>  

 <span data-ttu-id="686b5-106">次のクエリがあるとします。</span><span class="sxs-lookup"><span data-stu-id="686b5-106">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="686b5-107">データベース内に大量の行がある場合は、小さなサブセットを処理するためにすべての行を取得するのは望ましくありません。</span><span class="sxs-lookup"><span data-stu-id="686b5-107">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="686b5-108">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Data.Linq.EntitySet%601> クラスに <xref:System.Linq.IQueryable> インターフェイスが実装されています。</span><span class="sxs-lookup"><span data-stu-id="686b5-108">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="686b5-109">これにより、このようなクエリをリモートで実行することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="686b5-109">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="686b5-110">この方法には、次の 2 つの大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="686b5-110">Two major benefits flow from this technique:</span></span>  
  
- <span data-ttu-id="686b5-111">不要なデータは取得されません。</span><span class="sxs-lookup"><span data-stu-id="686b5-111">Unnecessary data is not retrieved.</span></span>  
  
- <span data-ttu-id="686b5-112">多くの場合、データベース エンジンによって実行されるクエリは、データベース インデックスの効果でより効率的になります。</span><span class="sxs-lookup"><span data-stu-id="686b5-112">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="686b5-113">ローカル実行</span><span class="sxs-lookup"><span data-stu-id="686b5-113">Local Execution</span></span>  

 <span data-ttu-id="686b5-114">一方、関連するエンティティ全体をローカル キャッシュに取り込むことが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="686b5-114">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="686b5-115">この目的から、<xref:System.Data.Linq.EntitySet%601> には、<xref:System.Data.Linq.EntitySet%601.Load%2A> のすべてのメンバーを明示的に読み込む <xref:System.Data.Linq.EntitySet%601> メソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="686b5-115">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="686b5-116"><xref:System.Data.Linq.EntitySet%601> が既に読み込まれている場合、それ以降のクエリはローカルに実行されます。</span><span class="sxs-lookup"><span data-stu-id="686b5-116">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="686b5-117">この方法は、次の 2 つの点で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="686b5-117">This approach helps in two ways:</span></span>  
  
- <span data-ttu-id="686b5-118">データ全体をローカルで使用する必要がある場合、または複数回使用する必要がある場合に、リモート クエリおよびそれに伴う待機時間を回避できます。</span><span class="sxs-lookup"><span data-stu-id="686b5-118">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
- <span data-ttu-id="686b5-119">エンティティ全体をシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="686b5-119">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="686b5-120">次のコードは、ローカル実行を行う方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="686b5-120">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="686b5-121">比較</span><span class="sxs-lookup"><span data-stu-id="686b5-121">Comparison</span></span>  

 <span data-ttu-id="686b5-122">この 2 種類の実行方法は、強力なオプションの組み合わせになります。つまり、大規模なコレクションではリモート実行を、小規模なコレクションまたは完全なコレクションが必要な場合はローカル実行を選択できます。</span><span class="sxs-lookup"><span data-stu-id="686b5-122">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="686b5-123">リモート実行は <xref:System.Linq.IQueryable> を使用して実装し、ローカル実行はメモリ内の <xref:System.Collections.Generic.IEnumerable%601> コレクションに対して行います。</span><span class="sxs-lookup"><span data-stu-id="686b5-123">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="686b5-124">ローカル実行 (つまり <xref:System.Collections.Generic.IEnumerable%601>) を強制するには、「[汎用 IEnumerable への型の変換](convert-a-type-to-a-generic-ienumerable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="686b5-124">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="686b5-125">順序なしのセットに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="686b5-125">Queries Against Unordered Sets</span></span>  

 <span data-ttu-id="686b5-126"><xref:System.Collections.Generic.List%601> を実装するローカル コレクションと、リレーショナル データベース内の "*順序なしのセット*" に対してリモート クエリを実行するコレクションの間には、重要な違いがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="686b5-126">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="686b5-127">インデックス値を使用するメソッドなど、<xref:System.Collections.Generic.List%601> のメソッドにはリストのセマンティクスが必要ですが、これは通常、順序なしのセットに対するリモート クエリからは得られません。</span><span class="sxs-lookup"><span data-stu-id="686b5-127"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="686b5-128">このため、このようなメソッドでは、ローカル実行を可能にするために暗黙的に <xref:System.Data.Linq.EntitySet%601> が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="686b5-128">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686b5-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="686b5-129">See also</span></span>

- [<span data-ttu-id="686b5-130">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="686b5-130">Query Concepts</span></span>](query-concepts.md)
