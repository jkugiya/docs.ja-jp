---
description: '詳細情報: アソシエーション型'
title: アソシエーション型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 4df84d97c798e9f2d06e0f5dce442e05cb4c67b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697557"
---
# <a name="association-type"></a><span data-ttu-id="b57cd-103">アソシエーション型</span><span class="sxs-lookup"><span data-stu-id="b57cd-103">association type</span></span>

<span data-ttu-id="b57cd-104">"*アソシエーション型*" (アソシエーションとも呼ばれます) は、Entity Data Model (EDM) でリレーションシップを記述するために不可欠な構成要素です。</span><span class="sxs-lookup"><span data-stu-id="b57cd-104">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="b57cd-105">概念モデルでは、アソシエーションによって 2 つの[エンティティ型](entity-type.md) (`Customer` や `Order` など) の間のリレーションシップが表されます。</span><span class="sxs-lookup"><span data-stu-id="b57cd-105">In a conceptual model, an association represents a relationship between two [entity types](entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="b57cd-106">アプリケーションでは、アソシエーションのインスタンスが特定のアソシエーション (`Customer` のインスタンスと `Order` のインスタンスの間のアソシエーションなど) を表します。</span><span class="sxs-lookup"><span data-stu-id="b57cd-106">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="b57cd-107">アソシエーション インスタンスは、[アソシエーション セット](association-set.md)に論理的にグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="b57cd-107">Association instances are logically grouped in an [association set](association-set.md).</span></span>  
  
 <span data-ttu-id="b57cd-108">アソシエーションの定義には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b57cd-108">An association definition contains the following information:</span></span>  
  
- <span data-ttu-id="b57cd-109">一意の名前 </span><span class="sxs-lookup"><span data-stu-id="b57cd-109">A unique name.</span></span> <span data-ttu-id="b57cd-110">(必須)</span><span class="sxs-lookup"><span data-stu-id="b57cd-110">(Required)</span></span>  
  
- <span data-ttu-id="b57cd-111">2 つの[アソシエーション End](association-end.md) (リレーションシップを構成する各エンティティ型に 1 つずつ)。</span><span class="sxs-lookup"><span data-stu-id="b57cd-111">Two [association ends](association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="b57cd-112">(必須)</span><span class="sxs-lookup"><span data-stu-id="b57cd-112">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b57cd-113">アソシエーションは、2 つ以上のエンティティ型のリレーションシップを表すことができません。</span><span class="sxs-lookup"><span data-stu-id="b57cd-113">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="b57cd-114">しかし、各アソシエーション End に同じエンティティ型を指定することによって、アソシエーションで自己リレーションシップを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b57cd-114">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
- <span data-ttu-id="b57cd-115">[参照整合性制約](referential-integrity-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="b57cd-115">A [referential integrity constraint](referential-integrity-constraint.md).</span></span> <span data-ttu-id="b57cd-116">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="b57cd-116">(Optional)</span></span>  
  
 <span data-ttu-id="b57cd-117">各アソシエーション End には、アソシエーションの 1 つの End に存在できるエンティティ型のインスタンス数を示す[アソシエーション End の多重度](association-end-multiplicity.md)を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b57cd-117">Each association end must specify an [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="b57cd-118">アソシエーション End の多重度には、1 、ゼロか 1 (0..1)、または多数 (\*) の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="b57cd-118">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="b57cd-119">アソシエーションの一方の End にあるエンティティ型のインスタンスには、それらがエンティティ型で公開されている場合、[ナビゲーション プロパティ](navigation-property.md)または外部キーからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b57cd-119">Entity type instances at one end of an association can be accessed through [navigation properties](navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="b57cd-120">詳しくは、「[Entity Data Model: 外部キー](foreign-key-property.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b57cd-120">For more information, see [Entity Data Model: Foreign Keys](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b57cd-121">例</span><span class="sxs-lookup"><span data-stu-id="b57cd-121">Example</span></span>  

 <span data-ttu-id="b57cd-122">下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="b57cd-122">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="b57cd-123">`PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。</span><span class="sxs-lookup"><span data-stu-id="b57cd-123">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="b57cd-124">`Publisher` End の多重度は 1 で、`Book` End の多重度は多数 (\*) です。これは、出版社が多くの書籍を出版し、書籍は 1 社の出版社により出版されることを示します。</span><span class="sxs-lookup"><span data-stu-id="b57cd-124">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![3 種類のエンティティを持つモデルの例](./media/association-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="b57cd-126">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="b57cd-126">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="b57cd-127">次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義しています。</span><span class="sxs-lookup"><span data-stu-id="b57cd-127">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="b57cd-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="b57cd-128">See also</span></span>

- [<span data-ttu-id="b57cd-129">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="b57cd-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="b57cd-130">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="b57cd-130">Entity Data Model</span></span>](entity-data-model.md)
