---
description: '詳細情報: エンティティ キー'
title: エンティティ キー
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: 588f18a2f76ca11c797b9b2aaab00b090c99e345
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724441"
---
# <a name="entity-key"></a><span data-ttu-id="6e8ed-103">エンティティ キー</span><span class="sxs-lookup"><span data-stu-id="6e8ed-103">entity key</span></span>

<span data-ttu-id="6e8ed-104">"*エンティティ キー*" とは、ID を決定するために使用される [エンティティ型](entity-type.md)の [プロパティ](property.md)または一連のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-104">An *entity key* is a [property](property.md) or a set of properties of an [entity type](entity-type.md) that are used to determine identity.</span></span> <span data-ttu-id="6e8ed-105">エンティティ キーを構成するプロパティは、デザイン時に選択されます。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-105">The properties that make up an entity key are chosen at design time.</span></span> <span data-ttu-id="6e8ed-106">エンティティ キー プロパティの値では、実行時の[エンティティ セット](entity-set.md)内のエンティティ型のインスタンスが一意に識別される必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-106">The values of entity key properties must uniquely identify an entity type instance within an [entity set](entity-set.md) at run time.</span></span> <span data-ttu-id="6e8ed-107">エンティティ キーを構成するプロパティには、エンティティ セット内のインスタンスの一意性を保証するものを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-107">The properties that make up an entity key should be chosen to guarantee uniqueness of instances in an entity set.</span></span>  
  
 <span data-ttu-id="6e8ed-108">エンティティ キーを構成する一連のプロパティには、次の要件があります。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-108">The following are the requirements for a set of properties to be an entity key:</span></span>  
  
- <span data-ttu-id="6e8ed-109">エンティティ セット内では、2 つ以上のエンティティ キーを同じにすることができません。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-109">No two entity keys within an entity set can be identical.</span></span> <span data-ttu-id="6e8ed-110">つまり、エンティティ セット内の 2 つのエンティティに対して、キーを構成するすべてのプロパティの値を同じにすることができません。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-110">That is, for any two entities within an entity set, the values for all of the properties that constitute a key cannot be the same.</span></span> <span data-ttu-id="6e8ed-111">ただし、エンティティ キーを構成する一部 (すべてではなく) の値は同じにすることができます。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-111">However, some (but not all) of the values that make up an entity key can be the same.</span></span>  
  
- <span data-ttu-id="6e8ed-112">エンティティ キーは、null 値が許可されない不変の[プリミティブ型プロパティ](entity-data-model-primitive-data-types.md)で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-112">An entity key must consist of a set of non-nullable, immutable, [primitive type properties](entity-data-model-primitive-data-types.md).</span></span>  
  
- <span data-ttu-id="6e8ed-113">エンティティ型のエンティティ キーを構成するプロパティは、変更できません。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-113">The properties that make up an entity key for a given entity type cannot change.</span></span> <span data-ttu-id="6e8ed-114">エンティティ型に対して複数のエンティティ キーを許可することはできません。代理キーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-114">You cannot allow more than one possible entity key for a given entity type; surrogate keys are not supported.</span></span>  
  
- <span data-ttu-id="6e8ed-115">エンティティが継承階層に含まれる場合、ルート エンティティには、エンティティ キーを構成するすべてのプロパティを含める必要があり、そのエンティティ キーをルート エンティティ型に定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-115">When an entity is involved in an inheritance hierarchy, the root entity must contain all the properties that make up the entity key, and the entity key must be defined on the root entity type.</span></span> <span data-ttu-id="6e8ed-116">詳しくは、「[Entity Data Model: 継承](entity-data-model-inheritance.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-116">For more information, see [Entity Data Model: Inheritance](entity-data-model-inheritance.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e8ed-117">例</span><span class="sxs-lookup"><span data-stu-id="6e8ed-117">Example</span></span>  

 <span data-ttu-id="6e8ed-118">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-118">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="6e8ed-119">各エンティティ型のエンティティ キーを構成するプロパティには、"(キー)" と示されています。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-119">The properties of each entity type that make up its entity key are denoted with "(Key)".</span></span> <span data-ttu-id="6e8ed-120">`Author` エンティティ型には、`Name` と `Address` の 2 つのプロパティで構成されるエンティティ キーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-120">Note that the `Author` entity type has an entity key that consists of two properties, `Name` and `Address`.</span></span>  
  
 ![3 種類のエンティティを持つモデルの例](./media/entity-key/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="6e8ed-122">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="6e8ed-123">次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義します。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-123">The CSDL below defines the `Book` entity type shown in the diagram above.</span></span> <span data-ttu-id="6e8ed-124">エンティティ キーは、エンティティ型の `ISBN` プロパティを参照して定義されています。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-124">Note that the entity key is defined by referencing the `ISBN` property of the entity type.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="6e8ed-125">国際標準図書番号 (ISBN) は書籍を一意に識別するものであるため、`ISBN` プロパティは、エンティティ キーに適しています。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-125">The `ISBN` property is a good choice for the entity key because an International Standard Book Number (ISBN) uniquely identifies a book.</span></span>  
  
 <span data-ttu-id="6e8ed-126">次の CSDL は、上のダイアグラムに示された `Author` エンティティ型を定義します。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-126">The CSDL below defines the `Author` entity type shown in the diagram above.</span></span> <span data-ttu-id="6e8ed-127">エンティティ キーは、`Name` と `Address` の 2 つのプロパティで構成されています。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-127">Note that the entity key consists of two properties, `Name` and `Address`.</span></span>  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 <span data-ttu-id="6e8ed-128">同じ名前の 2 人の著者が同じ住所に住む可能性は低いため、エンティティ キーに `Name` および `Address` を使用するのは妥当な選択になります。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-128">Using `Name` and `Address` for the entity key is a reasonable choice, because two authors of the same name are unlikely to live at the same address.</span></span> <span data-ttu-id="6e8ed-129">ただし、エンティティ キーのこの選択では、エンティティ セット内のエンティティ キーの一意性を絶対的に保証することはできません。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-129">However, this choice for an entity key does not absolutely guarantee unique entity keys in an entity set.</span></span> <span data-ttu-id="6e8ed-130">この場合には、`AuthorId` などのプロパティを追加して、著者を一意に識別することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="6e8ed-130">Adding a property, such as `AuthorId`, that could be used to uniquely identify an author would be recommended in this case.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e8ed-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e8ed-131">See also</span></span>

- [<span data-ttu-id="6e8ed-132">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="6e8ed-132">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="6e8ed-133">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="6e8ed-133">Entity Data Model</span></span>](entity-data-model.md)
