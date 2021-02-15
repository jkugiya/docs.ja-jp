---
description: '詳細情報: アソシエーション End の多重度'
title: アソシエーション End の多重度
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 4b708406192e8a6e34119b47261d8986829f2a43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697700"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="5a44d-103">アソシエーション End の多重度</span><span class="sxs-lookup"><span data-stu-id="5a44d-103">association end multiplicity</span></span>

<span data-ttu-id="5a44d-104">"*アソシエーション End の多重度*" は、[アソシエーション](association-type.md)の 1 つの End に存在できる [エンティティ型](entity-type.md)のインスタンス数を定義します。</span><span class="sxs-lookup"><span data-stu-id="5a44d-104">*Association end multiplicity* defines the number of [entity type](entity-type.md) instances that can be at one end of an [association](association-type.md).</span></span>  
  
 <span data-ttu-id="5a44d-105">アソシエーション End の多重度には、次のいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5a44d-105">An association end multiplicity can have one of the following values:</span></span>  
  
- <span data-ttu-id="5a44d-106">1 つ (1): アソシエーション End に 1 個のエンティティ型インスタンスが存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="5a44d-106">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
- <span data-ttu-id="5a44d-107">0 または 1 (0..1): アソシエーション End に 0 個か 1 個のエンティティ型インスタンスが存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="5a44d-107">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
- <span data-ttu-id="5a44d-108">多数 (\*): アソシエーション End に 0 個、1 個、または複数個のエンティティ型インスタンスが存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="5a44d-108">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="5a44d-109">アソシエーションは、多くの場合、そのアソシエーション End の多重度により特徴付けられます。</span><span class="sxs-lookup"><span data-stu-id="5a44d-109">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="5a44d-110">たとえば、アソシエーション End の多重度が 1 と多数 (\*) の場合、アソシエーションは一対多のアソシエーションと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="5a44d-110">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="5a44d-111">次の例で、`PublishedBy` アソシエーションは一対多のアソシエーションです (出版社が多くの書籍を出版し、書籍は 1 社の出版社により出版されます)。</span><span class="sxs-lookup"><span data-stu-id="5a44d-111">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="5a44d-112">`WrittenBy` アソシエーションは多対多のアソシエーションです (書籍の著者が複数の場合があり、著者は複数の書籍を執筆することができます)。</span><span class="sxs-lookup"><span data-stu-id="5a44d-112">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a44d-113">例</span><span class="sxs-lookup"><span data-stu-id="5a44d-113">Example</span></span>  

 <span data-ttu-id="5a44d-114">下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="5a44d-114">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="5a44d-115">`PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。</span><span class="sxs-lookup"><span data-stu-id="5a44d-115">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="5a44d-116">`Publisher` End の多重度は 1 で、`Book` End の多重度は多数 (\*) です。</span><span class="sxs-lookup"><span data-stu-id="5a44d-116">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![3 種類のエンティティを持つモデルの例](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="5a44d-118">ADO.NET Entity Framework では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して、概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="5a44d-118">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="5a44d-119">次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義しています。</span><span class="sxs-lookup"><span data-stu-id="5a44d-119">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="5a44d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a44d-120">See also</span></span>

- [<span data-ttu-id="5a44d-121">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="5a44d-121">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="5a44d-122">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="5a44d-122">Entity Data Model</span></span>](entity-data-model.md)
