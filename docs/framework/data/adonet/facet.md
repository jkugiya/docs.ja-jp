---
description: '詳細情報: ファセット'
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 195cb34b6de603859d592ee24140aec27a51418f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724311"
---
# <a name="facet"></a><span data-ttu-id="3edb2-103">facet</span><span class="sxs-lookup"><span data-stu-id="3edb2-103">facet</span></span>

<span data-ttu-id="3edb2-104">"*ファセット*" は、プリミティブ型のプロパティ定義の詳細を追加するために使用します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-104">A *facet* is used to add detail to a primitive type property definition.</span></span> <span data-ttu-id="3edb2-105">[プロパティ](property.md)定義には、プロパティの型の情報が含まれますが、多くの場合、より詳しい情報が必要になります。</span><span class="sxs-lookup"><span data-stu-id="3edb2-105">A [property](property.md) definition contains information about the property type, but often more detail is necessary.</span></span> <span data-ttu-id="3edb2-106">たとえば、概念モデルのエンティティ型に、値を null に設定できない `String` 型のプロパティが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3edb2-106">For example, an entity type in a conceptual model might have a property of type `String` whose value cannot be set to null.</span></span> <span data-ttu-id="3edb2-107">ファセットにより、このレベルの詳細を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="3edb2-107">Facets allow you to specify this level of detail.</span></span>  
  
 <span data-ttu-id="3edb2-108">下の表は、EDM でサポートされるファセットについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="3edb2-108">The table below describes the facets that are supported in the EDM.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3edb2-109">ファセットの正確な値と動作は、EDM の実装を使用するランタイム環境によって決まります。</span><span class="sxs-lookup"><span data-stu-id="3edb2-109">The exact values and behaviors of facets are determined by the run-time environment that uses an EDM implementation.</span></span>  
  
|<span data-ttu-id="3edb2-110">ファセット</span><span class="sxs-lookup"><span data-stu-id="3edb2-110">Facet</span></span>|<span data-ttu-id="3edb2-111">説明</span><span class="sxs-lookup"><span data-stu-id="3edb2-111">Description</span></span>|<span data-ttu-id="3edb2-112">対象</span><span class="sxs-lookup"><span data-stu-id="3edb2-112">Applies to</span></span>|  
|-----------|-----------------|----------------|  
|`Collation`|<span data-ttu-id="3edb2-113">プロパティの値に対して比較と順序付け操作を行うときに使用する照合シーケンス (または並べ替え順序) を指定します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-113">Specifies the collating sequence (or sorting sequence) to be used when performing comparison and ordering operations on values of the property.</span></span>|`String`|  
|`ConcurrencyMode`|<span data-ttu-id="3edb2-114">プロパティの値をオプティミスティック コンカレンシー チェックに使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-114">Indicates that the value of the property should be used for optimistic concurrency checks.</span></span>|<span data-ttu-id="3edb2-115">すべてのプリミティブ型のプロパティ</span><span class="sxs-lookup"><span data-stu-id="3edb2-115">All primitive type properties</span></span>|  
|`Default`|<span data-ttu-id="3edb2-116">インスタンス化で値が指定されない場合のプロパティの既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-116">Specifies the default value of the property if no value is supplied upon instantiation.</span></span>|<span data-ttu-id="3edb2-117">すべてのプリミティブ型のプロパティ</span><span class="sxs-lookup"><span data-stu-id="3edb2-117">All primitive type properties</span></span>|  
|`FixedLength`|<span data-ttu-id="3edb2-118">プロパティ値の長さを可変とすることができるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-118">Specifies whether the length of the property value can vary.</span></span>|<span data-ttu-id="3edb2-119">`Binary`, `String`</span><span class="sxs-lookup"><span data-stu-id="3edb2-119">`Binary`, `String`</span></span>|  
|`MaxLength`|<span data-ttu-id="3edb2-120">プロパティ値の最大長を指定します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-120">Specifies the maximum length of the property value.</span></span>|<span data-ttu-id="3edb2-121">`Binary`, `String`</span><span class="sxs-lookup"><span data-stu-id="3edb2-121">`Binary`, `String`</span></span>|  
|`Nullable`|<span data-ttu-id="3edb2-122">プロパティに null 値を指定できるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-122">Specifies whether the property can have a null value.</span></span>|<span data-ttu-id="3edb2-123">すべてのプリミティブ型のプロパティ</span><span class="sxs-lookup"><span data-stu-id="3edb2-123">All primitive type properties</span></span>|  
|`Precision`|<span data-ttu-id="3edb2-124">`Decimal` 型のプロパティには、プロパティ値の桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-124">For properties of type `Decimal`, specifies the number of digits a property value can have.</span></span> <span data-ttu-id="3edb2-125">`Time` 型、`DateTime` 型、および `DateTimeOffset` 型のプロパティには、プロパティ値の秒の小数点以下の有効桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-125">For properties of type `Time`, `DateTime`, and `DateTimeOffset`, specifies the number of digits for the fractional part of seconds of the property value.</span></span>|<span data-ttu-id="3edb2-126">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span><span class="sxs-lookup"><span data-stu-id="3edb2-126">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span></span>|  
|`Scale`|<span data-ttu-id="3edb2-127">プロパティ値の小数点の右側の桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-127">Specifies the number of digits to the right of the decimal point for the property value.</span></span>|<span data-ttu-id="3edb2-128">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="3edb2-128">Decimal</span></span>|  
|`Unicode`|<span data-ttu-id="3edb2-129">プロパティ値を Unicode として保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-129">Indicates whether the property value is stored as Unicode.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="3edb2-130">例</span><span class="sxs-lookup"><span data-stu-id="3edb2-130">Example</span></span>  

 <span data-ttu-id="3edb2-131">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-131">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="3edb2-132">次の CSDL は `Book` エンティティ型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="3edb2-132">The following CSDL defines a `Book` entity type.</span></span> <span data-ttu-id="3edb2-133">ファセットは XML 属性として実装されています。</span><span class="sxs-lookup"><span data-stu-id="3edb2-133">Note that facets are implemented as XML attributes.</span></span> <span data-ttu-id="3edb2-134">ファセット値は、プロパティ値を null に設定できないことと、`Scale` プロパティの `Precision` と `Revision` がそれぞれ 29 に設定されることを示します。</span><span class="sxs-lookup"><span data-stu-id="3edb2-134">The facet values indicate that no property can be set to null, and that the `Scale` and `Precision` of the `Revision` property are each set to 29.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="3edb2-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="3edb2-135">See also</span></span>

- [<span data-ttu-id="3edb2-136">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="3edb2-136">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="3edb2-137">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="3edb2-137">Entity Data Model</span></span>](entity-data-model.md)
