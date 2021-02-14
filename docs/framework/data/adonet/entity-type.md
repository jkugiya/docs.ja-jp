---
description: '詳細情報: エンティティ型'
title: エンティティ型
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: fb801ca8565fce01466f30bddc8c14c39af568c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724363"
---
# <a name="entity-type"></a><span data-ttu-id="ddae1-103">エンティティ型</span><span class="sxs-lookup"><span data-stu-id="ddae1-103">entity type</span></span>

<span data-ttu-id="ddae1-104">"*エンティティ型*" は、Entity Data Model (EDM) でデータ構造を記述するために不可欠な構成要素です。</span><span class="sxs-lookup"><span data-stu-id="ddae1-104">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="ddae1-105">概念モデルでのエンティティ型は、顧客や注文のように、トップレベル概念の構造を表します。</span><span class="sxs-lookup"><span data-stu-id="ddae1-105">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="ddae1-106">エンティティ型は、エンティティ型のインスタンスのテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="ddae1-106">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="ddae1-107">各テンプレートには、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ddae1-107">Each template contains the following information:</span></span>  
  
- <span data-ttu-id="ddae1-108">一意の名前 </span><span class="sxs-lookup"><span data-stu-id="ddae1-108">A unique name.</span></span> <span data-ttu-id="ddae1-109">(必須) </span><span class="sxs-lookup"><span data-stu-id="ddae1-109">(Required.)</span></span>  
  
- <span data-ttu-id="ddae1-110">1 つ以上のプロパティにより定義される[エンティティ キー](entity-key.md)。</span><span class="sxs-lookup"><span data-stu-id="ddae1-110">An [entity key](entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="ddae1-111">(必須) </span><span class="sxs-lookup"><span data-stu-id="ddae1-111">(Required.)</span></span>  
  
- <span data-ttu-id="ddae1-112">[プロパティ](property.md)の形式のデータ。</span><span class="sxs-lookup"><span data-stu-id="ddae1-112">Data in the form of [properties](property.md).</span></span> <span data-ttu-id="ddae1-113">(省略可能) </span><span class="sxs-lookup"><span data-stu-id="ddae1-113">(Optional.)</span></span>  
  
- <span data-ttu-id="ddae1-114">[アソシエーション](association-type.md)の 1 つの [End](association-end.md) から別の End へのナビゲーションを可能にする[ナビゲーション プロパティ](navigation-property.md)。</span><span class="sxs-lookup"><span data-stu-id="ddae1-114">[Navigation properties](navigation-property.md) that allow for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="ddae1-115">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="ddae1-115">(Optional)</span></span>  
  
 <span data-ttu-id="ddae1-116">アプリケーションでは、エンティティ型のインスタンスが特定のオブジェクト (特定の顧客や注文など) を表します。</span><span class="sxs-lookup"><span data-stu-id="ddae1-116">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="ddae1-117">エンティティ型の各インスタンスに対して、[エンティティ セット](entity-set.md)内の[エンティティ キー](entity-key.md)を一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddae1-117">Each instance of an entity type must have a unique [entity key](entity-key.md) within an [entity set](entity-set.md).</span></span>  
  
 <span data-ttu-id="ddae1-118">2 つのエンティティ型のインスタンスは、型が同じであり、エンティティ キーの値が等しい場合にのみ、等価のインスタンスと見なされます。</span><span class="sxs-lookup"><span data-stu-id="ddae1-118">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddae1-119">例</span><span class="sxs-lookup"><span data-stu-id="ddae1-119">Example</span></span>  

 <span data-ttu-id="ddae1-120">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="ddae1-120">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![3 種類のエンティティを持つモデルの例](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="ddae1-122">各エンティティ型のエンティティ キーを構成するプロパティには、"(キー)" と示されています。</span><span class="sxs-lookup"><span data-stu-id="ddae1-122">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="ddae1-123">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="ddae1-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="ddae1-124">次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="ddae1-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ddae1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddae1-125">See also</span></span>

- [<span data-ttu-id="ddae1-126">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="ddae1-126">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="ddae1-127">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ddae1-127">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="ddae1-128">facet</span><span class="sxs-lookup"><span data-stu-id="ddae1-128">facet</span></span>](facet.md)
