---
description: '詳細情報: エンティティ セット'
title: エンティティ セット
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 4881be280e1da2d53db6fc9f526289cdcd82ee07
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724428"
---
# <a name="entity-set"></a><span data-ttu-id="7019e-103">エンティティ セット</span><span class="sxs-lookup"><span data-stu-id="7019e-103">entity set</span></span>

<span data-ttu-id="7019e-104">"*エンティティ セット*" は、[エンティティ型](entity-type.md)のインスタンスと、そのエンティティ型から派生するあらゆる型のインスタンスの論理コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="7019e-104">An *entity set* is a logical container for instances of an [entity type](entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="7019e-105">(派生型について詳しくは、「[Entity Data Model: 継承](entity-data-model-inheritance.md)」をご覧ください。)エンティティ型とエンティティ セットの間のリレーションシップは、リレーショナル データベースの行とテーブルの間のリレーションシップと似ています。エンティティ型では、行のようにデータの構造が記述され、エンティティ セットには、テーブルのように特定の構造のインスタンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7019e-105">(For information about derived types, see [Entity Data Model: Inheritance](entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="7019e-106">エンティティ セットは、データ モデリング構造ではなく、データ構造を表しません。</span><span class="sxs-lookup"><span data-stu-id="7019e-106">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="7019e-107">エンティティ セットは、エンティティ型のインスタンスをグループ化してデータ ストアにマップするための、ホスト環境またはストレージ環境 (共通言語ランタイムや SQL Server データベースなど) の構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="7019e-107">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="7019e-108">エンティティ セットは、エンティティ セットと[アソシエーション セット](association-set.md)の論理グループである[エンティティ コンテナー](entity-container.md)内で定義されます。</span><span class="sxs-lookup"><span data-stu-id="7019e-108">An entity set is defined within an [entity container](entity-container.md), which is a logical grouping of entity sets and [association sets](association-set.md).</span></span>  
  
 <span data-ttu-id="7019e-109">エンティティ型のインスタンスがエンティティ セット内に存在できるようにするには、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7019e-109">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
- <span data-ttu-id="7019e-110">インスタンスの型がエンティティ セットの基本になるエンティティ型と同じであるか、インスタンスの型がエンティティ型のサブタイプであること。</span><span class="sxs-lookup"><span data-stu-id="7019e-110">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
- <span data-ttu-id="7019e-111">インスタンスの[エンティティ キー](entity-key.md)がエンティティ セット内で一意であること。</span><span class="sxs-lookup"><span data-stu-id="7019e-111">The [entity key](entity-key.md) for the instance is unique within the entity set.</span></span>  
  
- <span data-ttu-id="7019e-112">インスタンスが他のエンティティ セットに存在しないこと。</span><span class="sxs-lookup"><span data-stu-id="7019e-112">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7019e-113">同じエンティティ型を使用して複数のエンティティ セットを定義できますが、特定のエンティティ型のインスタンスは、1 つのエンティティ セット内のみに存在できます。</span><span class="sxs-lookup"><span data-stu-id="7019e-113">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="7019e-114">概念モデルの各エンティティ型にはエンティティ セットを定義する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="7019e-114">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7019e-115">例</span><span class="sxs-lookup"><span data-stu-id="7019e-115">Example</span></span>  

 <span data-ttu-id="7019e-116">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="7019e-116">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![3 種類のエンティティを持つモデルの例](./media/entity-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="7019e-118">次のダイアグラムには、上の概念モデルに基づく 2 つのエンティティ セット (`Books` および `Publishers`) と、アソシエーション セット(`PublishedBy`) を示しています。</span><span class="sxs-lookup"><span data-stu-id="7019e-118">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="7019e-119">`Books` エンティティ セット内の Bi は、実行時の `Book` エンティティ型インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="7019e-119">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="7019e-120">同様に、Pj は、`Publishers` エンティティ セットの `Publisher` インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="7019e-120">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="7019e-121">BiPj は、`PublishedBy` アソシエーション セット内にある `PublishedBy` アソシエーションのインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="7019e-121">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![セットの例を示すスクリーンショット。](./media/entity-set/sets-example-association.gif)  
  
 <span data-ttu-id="7019e-123">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="7019e-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="7019e-124">次の CSDL は、上の概念モデルに示された各エンティティ型に対して 1 つのエンティティ セットを持つエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="7019e-124">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="7019e-125">各エンティティ セットの名前とエンティティ型は、XML 属性で定義されています。</span><span class="sxs-lookup"><span data-stu-id="7019e-125">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="7019e-126">型ごとに複数のエンティティ セット (Multiple-Entity-Sets-per-Type: MEST) を定義できます。</span><span class="sxs-lookup"><span data-stu-id="7019e-126">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="7019e-127">次の CSDL は、`Book` エンティティ型のエンティティ セットを 2 つ持つエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="7019e-127">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="7019e-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="7019e-128">See also</span></span>

- [<span data-ttu-id="7019e-129">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="7019e-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="7019e-130">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="7019e-130">Entity Data Model</span></span>](entity-data-model.md)
