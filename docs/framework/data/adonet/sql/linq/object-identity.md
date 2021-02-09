---
description: '詳細情報: オブジェクト ID'
title: オブジェクト ID
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
ms.openlocfilehash: 1e525250e37e697e33ee53ea59b973882633ec15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695516"
---
# <a name="object-identity"></a><span data-ttu-id="7ad69-103">オブジェクト ID</span><span class="sxs-lookup"><span data-stu-id="7ad69-103">Object Identity</span></span>

<span data-ttu-id="7ad69-104">実行時のオブジェクトは、一意の ID を持ちます。</span><span class="sxs-lookup"><span data-stu-id="7ad69-104">Objects in the runtime have unique identities.</span></span> <span data-ttu-id="7ad69-105">2 つの変数が同じオブジェクトを参照している場合、実際それらの変数は、そのオブジェクトの同じインスタンスを参照しています。</span><span class="sxs-lookup"><span data-stu-id="7ad69-105">Two variables that refer to the same object actually refer to the same instance of the object.</span></span> <span data-ttu-id="7ad69-106">したがって、一方の変数から加えた変更は、もう一方の変数から直ちに参照できます。</span><span class="sxs-lookup"><span data-stu-id="7ad69-106">Because of this fact, changes that you make by way of a path through one variable are immediately visible through the other.</span></span>  
  
 <span data-ttu-id="7ad69-107">リレーショナル データベースのテーブルの行は、一意の ID を持ちません。</span><span class="sxs-lookup"><span data-stu-id="7ad69-107">Rows in a relational database table do not have unique identities.</span></span> <span data-ttu-id="7ad69-108">それぞれの行は一意の主キーを持つので、同じキー値を持つ行が存在することはありません。</span><span class="sxs-lookup"><span data-stu-id="7ad69-108">Because each row has a unique primary key, no two rows share the same key value.</span></span> <span data-ttu-id="7ad69-109">しかしこれは、データベース テーブルの中だけでの制限です。</span><span class="sxs-lookup"><span data-stu-id="7ad69-109">However, this fact constrains only the contents of the database table.</span></span>  
  
 <span data-ttu-id="7ad69-110">実際には、データベースの外にデータを取り出して、別の層に移し、そこでアプリケーションが処理を行うのが普通です。</span><span class="sxs-lookup"><span data-stu-id="7ad69-110">In reality, data is most often brought out of the database and into a different tier, where an application works with it.</span></span> <span data-ttu-id="7ad69-111">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] がサポートするのはこのモデルです。</span><span class="sxs-lookup"><span data-stu-id="7ad69-111">This is the model that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports.</span></span> <span data-ttu-id="7ad69-112">データベースからデータを行として取り出す場合、同じデータを表す 2 つの行が、実際に同じ行インスタンスに対応付けられることは求めません。</span><span class="sxs-lookup"><span data-stu-id="7ad69-112">When data is brought out of the database as rows, you have no expectation that two rows that represent the same data actually correspond to the same row instances.</span></span> <span data-ttu-id="7ad69-113">ある特定の顧客についてのクエリを 2 回行うと、2 行のデータが取得されます。</span><span class="sxs-lookup"><span data-stu-id="7ad69-113">If you query for a specific customer two times, you get two rows of data.</span></span> <span data-ttu-id="7ad69-114">どちらの行も、中身は同じ情報です。</span><span class="sxs-lookup"><span data-stu-id="7ad69-114">Each row contains the same information.</span></span>  
  
 <span data-ttu-id="7ad69-115">オブジェクトの場合、求める動作は大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="7ad69-115">With objects you expect something very different.</span></span> <span data-ttu-id="7ad69-116"><xref:System.Data.Linq.DataContext> に対して同じ情報を繰り返し要求した場合、同じオブジェクト インスタンスが返されることを期待します。</span><span class="sxs-lookup"><span data-stu-id="7ad69-116">You expect that if you ask the <xref:System.Data.Linq.DataContext> for the same information repeatedly, it will in fact give you the same object instance.</span></span> <span data-ttu-id="7ad69-117">そのような動作を期待するのは、オブジェクトはアプリケーションにとって特別な意味を持つものであり、オブジェクトらしい動作が求められるためです。</span><span class="sxs-lookup"><span data-stu-id="7ad69-117">You expect this behavior because objects have special meaning for your application and you expect them to behave like objects.</span></span> <span data-ttu-id="7ad69-118">オブジェクトは階層やグラフとして設計されています。</span><span class="sxs-lookup"><span data-stu-id="7ad69-118">You designed them as hierarchies or graphs.</span></span> <span data-ttu-id="7ad69-119">そして、そのように取得されることを期待します。同じデータを何回か要求したからといって、レプリケートされたインスタンスをいくつも返されることは期待しません。</span><span class="sxs-lookup"><span data-stu-id="7ad69-119">You expect to retrieve them as such and not to receive multitudes of replicated instances just because you asked for the same thing more than one time.</span></span>  
  
 <span data-ttu-id="7ad69-120">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、オブジェクト ID は <xref:System.Data.Linq.DataContext> によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="7ad69-120">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.DataContext> manages object identity.</span></span> <span data-ttu-id="7ad69-121">データベースから新しい行を取得すると、主キーに基づいてその行が ID テーブルに記録され、新しいオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7ad69-121">Whenever you retrieve a new row from the database, the row is logged in an identity table by its primary key, and a new object is created.</span></span> <span data-ttu-id="7ad69-122">それと同じ行を取得した場合、最初のオブジェクト インスタンスがアプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="7ad69-122">Whenever you retrieve that same row, the original object instance is handed back to the application.</span></span> <span data-ttu-id="7ad69-123"><xref:System.Data.Linq.DataContext> は、このような方法で、データベースにおける ID の概念 (つまり主キー) を、言語における ID の概念 (つまりインスタンス) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7ad69-123">In this manner the <xref:System.Data.Linq.DataContext> translates the concept of identity as seen by the database (that is, primary keys) into the concept of identity seen by the language (that is, instances).</span></span> <span data-ttu-id="7ad69-124">アプリケーションが参照するオブジェクトは、常に最初に取得した状態です。</span><span class="sxs-lookup"><span data-stu-id="7ad69-124">The application only sees the object in the state that it was first retrieved.</span></span> <span data-ttu-id="7ad69-125">新しいデータが異なる場合、破棄されます。</span><span class="sxs-lookup"><span data-stu-id="7ad69-125">The new data, if different, is discarded.</span></span> <span data-ttu-id="7ad69-126">詳しくは、「[ID キャッシュからのオブジェクトの取得](retrieving-objects-from-the-identity-cache.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7ad69-126">For more information, see [Retrieving Objects from the Identity Cache](retrieving-objects-from-the-identity-cache.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7ad69-127">では、オプティミスティック更新をサポートするために、この方法を使用してローカル オブジェクトの整合性が管理されます。</span><span class="sxs-lookup"><span data-stu-id="7ad69-127">uses this approach to manage the integrity of local objects in order to support optimistic updates.</span></span> <span data-ttu-id="7ad69-128">オブジェクトが最初に作成された後で生じた変更は、アプリケーションが加えた変更だけなので、アプリケーションの意図は明確です。</span><span class="sxs-lookup"><span data-stu-id="7ad69-128">Because the only changes that occur after the object is at first created are those made by the application, the intent of the application is clear.</span></span> <span data-ttu-id="7ad69-129">その間に外部の者によって変更が加えられた場合、`SubmitChanges()` を呼び出した時点で把握されます。</span><span class="sxs-lookup"><span data-stu-id="7ad69-129">If changes by an outside party have occurred in the interim, they are identified at the time `SubmitChanges()` is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ad69-130">クエリで要求されたオブジェクトが、既に取得済みであることが簡単に判別できる場合、クエリは実行されません。</span><span class="sxs-lookup"><span data-stu-id="7ad69-130">If the object requested by the query is easily identifiable as one already retrieved, no query is executed.</span></span> <span data-ttu-id="7ad69-131">ID テーブルは、それまでに取得した全オブジェクトのキャッシュの役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="7ad69-131">The identity table acts as a cache of all previously retrieved objects.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7ad69-132">使用例</span><span class="sxs-lookup"><span data-stu-id="7ad69-132">Examples</span></span>  
  
### <a name="object-caching-example-1"></a><span data-ttu-id="7ad69-133">オブジェクトのキャッシュの例 1</span><span class="sxs-lookup"><span data-stu-id="7ad69-133">Object Caching Example 1</span></span>  

 <span data-ttu-id="7ad69-134">この例では、同じクエリを 2 回実行した場合、メモリ内にある同じオブジェクトへの参照をそのつど受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7ad69-134">In this example, if you execute the same query two times, you receive a reference to the same object in memory every time.</span></span>  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a><span data-ttu-id="7ad69-135">オブジェクトのキャッシュの例 2</span><span class="sxs-lookup"><span data-stu-id="7ad69-135">Object Caching Example 2</span></span>  

 <span data-ttu-id="7ad69-136">この例では、データベースの同じ行を返す、異なるクエリを実行した場合、メモリ内にある同じオブジェクトへの参照をそのつど受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7ad69-136">In this example, if you execute different queries that return the same row from the database, you receive a reference to the same object in memory every time.</span></span>  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7ad69-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ad69-137">See also</span></span>

- [<span data-ttu-id="7ad69-138">背景情報</span><span class="sxs-lookup"><span data-stu-id="7ad69-138">Background Information</span></span>](background-information.md)
