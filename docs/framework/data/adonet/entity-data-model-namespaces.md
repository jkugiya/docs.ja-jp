---
description: '詳細情報: Entity Data Model:名前空間'
title: Entity Data Model:名前空間
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: c18178672ebab0e323c9712af2668c3cb92e0300
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672765"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="fdfc2-103">Entity Data Model:名前空間</span><span class="sxs-lookup"><span data-stu-id="fdfc2-103">Entity Data Model: Namespaces</span></span>

<span data-ttu-id="fdfc2-104">Entity Data Model (EDM) の名前空間は、[エンティティ型](entity-type.md)、[複合型](complex-type.md)、[アソシエーション](association-type.md)のための抽象コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="fdfc2-104">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="fdfc2-105">EDM の名前空間はプログラミング言語の名前空間と似ており、その中に含まれるオブジェクトのコンテキストを指定し、同じ名前を持つ (しかし、別の名前空間に含まれる) オブジェクトを明確に区別する手段になります。</span><span class="sxs-lookup"><span data-stu-id="fdfc2-105">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdfc2-106">例</span><span class="sxs-lookup"><span data-stu-id="fdfc2-106">Example</span></span>  

 <span data-ttu-id="fdfc2-107">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="fdfc2-107">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="fdfc2-108">次の CSDL コードは、名前空間を使用して異なる概念モデルに定義された型を識別します。</span><span class="sxs-lookup"><span data-stu-id="fdfc2-108">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="fdfc2-109">この例は、`Publisher` 名前空間からインポートされた複合型のプロパティ (`Address`) を持つエンティティ型 (`ExtendedBooksModel`) を定義します。</span><span class="sxs-lookup"><span data-stu-id="fdfc2-109">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="fdfc2-110">`Using` 要素は、名前空間がインポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="fdfc2-110">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="fdfc2-111">さらに、`Address` プロパティの型は、完全修飾名 (`ExtendedBooksModel.Address`) で定義されており、この型が `ExtendedBooksModel` 名前空間で定義されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="fdfc2-111">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="fdfc2-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdfc2-112">See also</span></span>

- [<span data-ttu-id="fdfc2-113">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="fdfc2-113">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="fdfc2-114">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="fdfc2-114">Entity Data Model</span></span>](entity-data-model.md)
