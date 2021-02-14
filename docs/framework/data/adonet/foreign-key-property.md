---
description: '詳細情報: 外部キーのプロパティ'
title: 外部キーのプロパティ
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 1666e4477c09dd5d0ed3d2c35a93ca21824e8a0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724129"
---
# <a name="foreign-key-property"></a><span data-ttu-id="b1eef-103">外部キーのプロパティ</span><span class="sxs-lookup"><span data-stu-id="b1eef-103">foreign key property</span></span>

<span data-ttu-id="b1eef-104">Entity Data Model (EDM) における "*外部キーのプロパティ*" は、別の [エンティティ型](entity-type.md)の [エンティティ キー](entity-key.md)を含むエンティティ型のプリミティブ型の [プロパティ](property.md) (または一連のプリミティブ型のプロパティ) です。</span><span class="sxs-lookup"><span data-stu-id="b1eef-104">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](property.md) (or a set of primitive type properties) on an [entity type](entity-type.md) that contains the [entity key](entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="b1eef-105">外部キーのプロパティは、リレーショナル データベースの外部キー列に似ています。</span><span class="sxs-lookup"><span data-stu-id="b1eef-105">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="b1eef-106">リレーショナル データベースで外部キー列を使用してテーブル内の行の間のリレーションシップを作成するのと同様に、概念モデルでは外部キーのプロパティを使用してエンティティ型の間の[アソシエーション](association-type.md)を設定します。</span><span class="sxs-lookup"><span data-stu-id="b1eef-106">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](association-type.md) between entity types.</span></span> <span data-ttu-id="b1eef-107">エンティティ型の 1 つに外部キーのプロパティがある場合に、2 つのエンティティ型の間のアソシエーションを定義するには、[参照整合性制約](referential-integrity-constraint.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="b1eef-107">A [referential integrity constraint](referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1eef-108">例</span><span class="sxs-lookup"><span data-stu-id="b1eef-108">Example</span></span>  

 <span data-ttu-id="b1eef-109">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="b1eef-109">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="b1eef-110">`Book` エンティティ型には、`PublisherId` というプロパティがあります。`Publisher` アソシエーションに参照整合性制約を定義するときに、このプロパティは `PublishedBy` エンティティ型のエンティティ キーを参照します。</span><span class="sxs-lookup"><span data-stu-id="b1eef-110">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="b1eef-111">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "参照制約モデルの例")</span><span class="sxs-lookup"><span data-stu-id="b1eef-111">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="b1eef-112">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="b1eef-112">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="b1eef-113">次の CSDL は、外部キーのプロパティ `PublisherId` を使用して、上の概念モデルに示された `PublishedBy` アソシエーションに参照整合性制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="b1eef-113">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="b1eef-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1eef-114">See also</span></span>

- [<span data-ttu-id="b1eef-115">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="b1eef-115">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="b1eef-116">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="b1eef-116">Entity Data Model</span></span>](entity-data-model.md)
