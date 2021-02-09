---
description: '詳細情報: ナビゲーション プロパティ'
title: ナビゲーション プロパティ
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 4655c8ef1b18972697e41fa1c7c6185945335aa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786239"
---
# <a name="navigation-property"></a><span data-ttu-id="e023e-103">ナビゲーション プロパティ</span><span class="sxs-lookup"><span data-stu-id="e023e-103">Navigation property</span></span>

<span data-ttu-id="e023e-104">"*ナビゲーション プロパティ*" は、[アソシエーション](association-type.md)の 1 つの [End](association-end.md) から別の End へのナビゲーションを可能にする、[エンティティ型](entity-type.md)の省略可能なプロパティです。</span><span class="sxs-lookup"><span data-stu-id="e023e-104">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="e023e-105">他の[プロパティ](property.md)とは異なり、ナビゲーション プロパティではデータは伝達されません。</span><span class="sxs-lookup"><span data-stu-id="e023e-105">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="e023e-106">ナビゲーション プロパティの定義には、以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e023e-106">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="e023e-107">名前。</span><span class="sxs-lookup"><span data-stu-id="e023e-107">A name.</span></span> <span data-ttu-id="e023e-108">(必須)</span><span class="sxs-lookup"><span data-stu-id="e023e-108">(Required)</span></span>

- <span data-ttu-id="e023e-109">移動対象のアソシエーション。</span><span class="sxs-lookup"><span data-stu-id="e023e-109">The association that it navigates.</span></span> <span data-ttu-id="e023e-110">(必須)</span><span class="sxs-lookup"><span data-stu-id="e023e-110">(Required)</span></span>

- <span data-ttu-id="e023e-111">移動対象のアソシエーションの End。</span><span class="sxs-lookup"><span data-stu-id="e023e-111">The ends of the association that it navigates.</span></span> <span data-ttu-id="e023e-112">(必須)</span><span class="sxs-lookup"><span data-stu-id="e023e-112">(Required)</span></span>

<span data-ttu-id="e023e-113">ナビゲーション プロパティは、アソシエーション End の両方のエンティティ型で省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e023e-113">Navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="e023e-114">1 つのアソシエーション End のエンティティ型にナビゲーション プロパティを定義した場合に、そのアソシエーションの他方の End でもエンティティ型にナビゲーション プロパティを定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e023e-114">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="e023e-115">ナビゲーション プロパティのデータ型は、リモートの[アソシエーション End](association-end.md) の[多重度](association-end-multiplicity.md)により決まります。</span><span class="sxs-lookup"><span data-stu-id="e023e-115">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="e023e-116">たとえば、ナビゲーション プロパティ `OrdersNavProp` が `Customer` エンティティ型に存在し、`Customer` と `Order` の間の一対多のアソシエーションで移動するとします。</span><span class="sxs-lookup"><span data-stu-id="e023e-116">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="e023e-117">ナビゲーション プロパティのリモートのアソシエーション End の多重度が多数 (\*) であるため、そのデータ型は (`Order` の) コレクションになります。</span><span class="sxs-lookup"><span data-stu-id="e023e-117">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="e023e-118">同様に、`CustomerNavProp` エンティティ型にナビゲーション プロパティ、`Order` が存在する場合、リモート End の多重度が (1) であるため、データ型は `Customer` になります。</span><span class="sxs-lookup"><span data-stu-id="e023e-118">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="e023e-119">例</span><span class="sxs-lookup"><span data-stu-id="e023e-119">Example</span></span>

<span data-ttu-id="e023e-120">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="e023e-120">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="e023e-121">ナビゲーション プロパティ `Publisher` と `Authors` が、Book エンティティ型で定義されています。</span><span class="sxs-lookup"><span data-stu-id="e023e-121">The navigation properties `Publisher` and `Authors` are defined on the Book entity type.</span></span> <span data-ttu-id="e023e-122">Publisher エンティティ型と `Books` エンティティ型には、ナビゲーション プロパティ、`Author` が定義されています。</span><span class="sxs-lookup"><span data-stu-id="e023e-122">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

![3 つのエンティティ型を含む概念モデルを示す図。](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

<span data-ttu-id="e023e-124">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="e023e-124">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="e023e-125">次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="e023e-125">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="e023e-126">ナビゲーション プロパティの定義に必要な情報の伝達には、XML 属性が使用されます。属性 `Name` にはプロパティ名が含まれ、`Relationship` にはナビゲートするアソシエーション名が含まれ、`FromRole` と `ToRole` にはアソシエーションの End が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e023e-126">XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="e023e-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="e023e-127">See also</span></span>

- [<span data-ttu-id="e023e-128">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="e023e-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="e023e-129">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="e023e-129">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="e023e-130">リレーションシップ、ナビゲーション プロパティ、および外部キー</span><span class="sxs-lookup"><span data-stu-id="e023e-130">Relationships, navigation properties, and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
