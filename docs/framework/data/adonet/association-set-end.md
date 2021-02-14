---
description: '詳細情報: アソシエーション セット End'
title: アソシエーション セット End
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 12e01a3fb947f6fabd5e1a93ef475132418963df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697674"
---
# <a name="association-set-end"></a><span data-ttu-id="bbee8-103">アソシエーション セット End</span><span class="sxs-lookup"><span data-stu-id="bbee8-103">association set end</span></span>

<span data-ttu-id="bbee8-104">"*アソシエーション セット End*" は、[アソシエーション セット](association-set.md)の End にある [エンティティ型](entity-type.md)と [エンティティ セット](entity-set.md)を識別します。</span><span class="sxs-lookup"><span data-stu-id="bbee8-104">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="bbee8-105">アソシエーション セット End はアソシエーション セットの一部として定義されます。アソシエーション セットには、アソシエーション セット End が 2 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="bbee8-105">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="bbee8-106">アソシエーション セット End の定義には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bbee8-106">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="bbee8-107">アソシエーション セットに含まれるエンティティ型の 1 つ。</span><span class="sxs-lookup"><span data-stu-id="bbee8-107">One of the entity types involved in the association set.</span></span> <span data-ttu-id="bbee8-108">(必須)</span><span class="sxs-lookup"><span data-stu-id="bbee8-108">(Required)</span></span>  
  
- <span data-ttu-id="bbee8-109">アソシエーション セットに含まれるエンティティ型のエンティティ セット。</span><span class="sxs-lookup"><span data-stu-id="bbee8-109">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="bbee8-110">(必須)</span><span class="sxs-lookup"><span data-stu-id="bbee8-110">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbee8-111">例</span><span class="sxs-lookup"><span data-stu-id="bbee8-111">Example</span></span>  

 <span data-ttu-id="bbee8-112">下のダイアグラムは、`WrittenBy` および `PublishedBy` という 2 つのアソシエーションの概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="bbee8-112">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![3 種類のエンティティを持つモデルの例](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="bbee8-114">次のダイアグラムには、上の概念モデルに基づくアソシエーション セット (`PublishedBy`) と 2 つのエンティティ セット (`Books` および `Publishers`) を示しています。</span><span class="sxs-lookup"><span data-stu-id="bbee8-114">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="bbee8-115">アソシエーション セット End は `Books` および `Publishers` エンティティ セットです。</span><span class="sxs-lookup"><span data-stu-id="bbee8-115">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="bbee8-116">`Books` エンティティ セット内の Bi は、実行時の `Book` エンティティ型インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="bbee8-116">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="bbee8-117">同様に、Pj は、`Publishers` エンティティ セット内の `Publisher` インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="bbee8-117">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="bbee8-118">BiPj は、`PublishedBy` アソシエーション セット内にある `PublishedBy` アソシエーションのインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="bbee8-118">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![セットの例を示すスクリーンショット。](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="bbee8-120">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれる DSL を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="bbee8-120">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="bbee8-121">次の CSDL は、上のダイアグラムの各アソシエーションに対して 1 つのアソシエーション セットを持つエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="bbee8-121">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="bbee8-122">アソシエーション セット End はアソシエーション セット定義の一部として定義されています。</span><span class="sxs-lookup"><span data-stu-id="bbee8-122">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="bbee8-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbee8-123">See also</span></span>

- [<span data-ttu-id="bbee8-124">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="bbee8-124">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="bbee8-125">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="bbee8-125">Entity Data Model</span></span>](entity-data-model.md)
