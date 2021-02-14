---
description: '詳細情報: 関連付けセット'
title: 関連付けセット
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: aeddf3e898aecc2b283a941e844a6dbe810357f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697583"
---
# <a name="association-set"></a><span data-ttu-id="4dfd2-103">関連付けセット</span><span class="sxs-lookup"><span data-stu-id="4dfd2-103">association set</span></span>

<span data-ttu-id="4dfd2-104">"*アソシエーション セット*" は、同じ型の [アソシエーション](association-type.md) インスタンスの論理コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-104">An *association set* is a logical container for [association](association-type.md) instances of the same type.</span></span> <span data-ttu-id="4dfd2-105">アソシエーション セットは、データ モデリング構造ではなく、データ構造やリレーションシップを表しません。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-105">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="4dfd2-106">アソシエーション セットは、アソシエーション インスタンスをグループ化してデータ ストアにマップするための、ホスト環境またはストレージ環境 (共通言語ランタイムや SQL Server データベースなど) の構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-106">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="4dfd2-107">アソシエーション セットは、[エンティティ セット](entity-set.md)とアソシエーション セットの論理グループである[エンティティ コンテナー](entity-container.md)内に定義されます。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-107">An association set is defined within an [entity container](entity-container.md), which is a logical grouping of [entity sets](entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="4dfd2-108">アソシエーション セットの定義には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-108">A definition for an association set contains the following information:</span></span>  
  
- <span data-ttu-id="4dfd2-109">アソシエーション セット名。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-109">The association set name.</span></span> <span data-ttu-id="4dfd2-110">(必須)</span><span class="sxs-lookup"><span data-stu-id="4dfd2-110">(Required)</span></span>  
  
- <span data-ttu-id="4dfd2-111">インスタンスを含むアソシエーション。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-111">The association of which it will contain instances.</span></span> <span data-ttu-id="4dfd2-112">(必須)</span><span class="sxs-lookup"><span data-stu-id="4dfd2-112">(Required)</span></span>  
  
- <span data-ttu-id="4dfd2-113">2 つの[アソシエーション セット End](association-set-end.md)。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-113">Two [association set ends](association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dfd2-114">例</span><span class="sxs-lookup"><span data-stu-id="4dfd2-114">Example</span></span>  

 <span data-ttu-id="4dfd2-115">下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-115">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="4dfd2-116">このダイアグラムにはアソシエーション セットに関する情報が示されていませんが、次のダイアグラムはこのモデルに基づくアソシエーション セットとエンティティ セットの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-116">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 ![3 種類のエンティティを持つモデルの例](./media/association-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="4dfd2-118">次の例は、上の概念モデルに基づくアソシエーション セット(`PublishedBy`) と 2 つのエンティティ セット (`Books` および `Publishers`) を示しています。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-118">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="4dfd2-119">`Books` エンティティ セット内の Bi は、実行時の `Book` エンティティ型インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-119">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="4dfd2-120">同様に、Pj は、`Publishers` エンティティ セット内の `Publisher` インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-120">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="4dfd2-121">BiPj は、`PublishedBy` アソシエーション セット内にある `PublishedBy` アソシエーションのインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-121">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![セットの例を示すスクリーンショット。](./media/association-set/sets-example-association.gif)  
  
 <span data-ttu-id="4dfd2-123">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="4dfd2-124">次の CSDL は、上のダイアグラムの各アソシエーションに対して 1 つのアソシエーション セットを持つエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-124">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="4dfd2-125">各アソシエーション セットの名前とアソシエーションは、XML 属性で定義しています。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-125">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="4dfd2-126">2 つのアソシエーション セットが同じ[アソシエーション セット End](association-set-end.md) を共有していない限り、アソシエーションごとに複数のアソシエーション セットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-126">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](association-set-end.md).</span></span> <span data-ttu-id="4dfd2-127">次の CSDL は、`WrittenBy` アソシエーションの 2 つのアソシエーション セットを含むエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-127">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="4dfd2-128">`Book` エンティティ型と `Author` エンティティ型には複数のエンティティ セットが定義され、同じアソシエーション セット End を共有するアソシエーション セットがないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4dfd2-128">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="4dfd2-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dfd2-129">See also</span></span>

- [<span data-ttu-id="4dfd2-130">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="4dfd2-130">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="4dfd2-131">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="4dfd2-131">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="4dfd2-132">外部キーのプロパティ</span><span class="sxs-lookup"><span data-stu-id="4dfd2-132">foreign key property</span></span>](foreign-key-property.md)
