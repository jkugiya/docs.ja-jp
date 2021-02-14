---
description: '詳細情報: モデル定義関数'
title: モデル定義関数
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 146ef4a8ad8c38897b8e56b6bc1485e1e40754cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723739"
---
# <a name="model-defined-function"></a><span data-ttu-id="cccd3-103">モデル定義関数</span><span class="sxs-lookup"><span data-stu-id="cccd3-103">model-defined function</span></span>

<span data-ttu-id="cccd3-104">"*モデル定義関数*" は、概念モデルで定義される関数です。</span><span class="sxs-lookup"><span data-stu-id="cccd3-104">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="cccd3-105">モデル定義関数の本体は、[Entity SQL](./ef/language-reference/entity-sql-language.md) により表現されます。これにより、データ ソースでサポートされる規則または言語に関係なく関数を表現することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="cccd3-105">The body of a model-defined function is expressed in [Entity SQL](./ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="cccd3-106">モデル定義関数の定義には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cccd3-106">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="cccd3-107">関数名。</span><span class="sxs-lookup"><span data-stu-id="cccd3-107">A function name.</span></span> <span data-ttu-id="cccd3-108">(必須)</span><span class="sxs-lookup"><span data-stu-id="cccd3-108">(Required)</span></span>  
  
- <span data-ttu-id="cccd3-109">戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="cccd3-109">The type of the return value.</span></span> <span data-ttu-id="cccd3-110">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="cccd3-110">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cccd3-111">戻り値の型が指定されていない場合、戻り値は void になります。</span><span class="sxs-lookup"><span data-stu-id="cccd3-111">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="cccd3-112">パラメーター情報。</span><span class="sxs-lookup"><span data-stu-id="cccd3-112">Parameter information.</span></span> <span data-ttu-id="cccd3-113">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="cccd3-113">(Optional)</span></span>  
  
- <span data-ttu-id="cccd3-114">関数の本体を定義する [Entity SQL](./ef/language-reference/entity-sql-language.md) 表現。</span><span class="sxs-lookup"><span data-stu-id="cccd3-114">An [Entity SQL](./ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="cccd3-115">モデル定義関数では、出力パラメーターがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="cccd3-115">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="cccd3-116">この制約は、モデル定義関数を構成できるようにするためにあります。</span><span class="sxs-lookup"><span data-stu-id="cccd3-116">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cccd3-117">例</span><span class="sxs-lookup"><span data-stu-id="cccd3-117">Example</span></span>  

 <span data-ttu-id="cccd3-118">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="cccd3-118">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![発行日を含むモデルを示すスクリーンショット。](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="cccd3-120">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="cccd3-120">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="cccd3-121">次の CSDL は、`Book` (上のダイアグラムの) の出版以降の年数を返す概念モデルの関数を定義しています。</span><span class="sxs-lookup"><span data-stu-id="cccd3-121">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="cccd3-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="cccd3-122">See also</span></span>

- [<span data-ttu-id="cccd3-123">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="cccd3-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="cccd3-124">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="cccd3-124">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="cccd3-125">Entity Data Model: プリミティブ データ型</span><span class="sxs-lookup"><span data-stu-id="cccd3-125">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)
