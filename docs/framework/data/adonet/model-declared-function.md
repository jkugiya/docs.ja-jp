---
description: '詳細情報: モデル宣言関数'
title: モデル宣言関数
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: c9a5cedb8c9706aa0d299635f60f762b92ca6d78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786265"
---
# <a name="model-declared-function"></a><span data-ttu-id="8be2d-103">モデル宣言関数</span><span class="sxs-lookup"><span data-stu-id="8be2d-103">model-declared function</span></span>

<span data-ttu-id="8be2d-104">"*モデル宣言関数*" は、概念モデルで宣言されていても、その概念モデルには定義されていない関数です。</span><span class="sxs-lookup"><span data-stu-id="8be2d-104">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="8be2d-105">この関数は、ホスト環境またはストレージ環境で定義します。</span><span class="sxs-lookup"><span data-stu-id="8be2d-105">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="8be2d-106">たとえば、モデル宣言関数は、データベースに定義された関数にマップされ、これによって概念モデルにおけるサーバー側の機能が公開される場合があります。</span><span class="sxs-lookup"><span data-stu-id="8be2d-106">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="8be2d-107">モデル宣言関数の宣言には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8be2d-107">The declaration of a model-declared function contains the following information:</span></span>  
  
- <span data-ttu-id="8be2d-108">関数の名前。</span><span class="sxs-lookup"><span data-stu-id="8be2d-108">The name of the function.</span></span> <span data-ttu-id="8be2d-109">(必須)</span><span class="sxs-lookup"><span data-stu-id="8be2d-109">(Required)</span></span>  
  
- <span data-ttu-id="8be2d-110">戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="8be2d-110">The type of the return value.</span></span> <span data-ttu-id="8be2d-111">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="8be2d-111">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8be2d-112">戻り値が指定されていない場合、戻り値の型は void になります。</span><span class="sxs-lookup"><span data-stu-id="8be2d-112">If no return value is specified, the return type is void.</span></span>  
  
- <span data-ttu-id="8be2d-113">パラメーター名と型を含むパラメーター情報。</span><span class="sxs-lookup"><span data-stu-id="8be2d-113">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="8be2d-114">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="8be2d-114">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="8be2d-115">例</span><span class="sxs-lookup"><span data-stu-id="8be2d-115">Example</span></span>  

 <span data-ttu-id="8be2d-116">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="8be2d-116">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="8be2d-117">CSDL には、モデル宣言関数の 1 つの実装手段として、関数インポートがあります ([FunctionImport 要素](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)を使用します)。</span><span class="sxs-lookup"><span data-stu-id="8be2d-117">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="8be2d-118">次の CSDL は、関数インポート定義を含むエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="8be2d-118">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="8be2d-119">戻り値の型が指定されていないため、関数の戻り値の型は void になります。</span><span class="sxs-lookup"><span data-stu-id="8be2d-119">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="8be2d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8be2d-120">See also</span></span>

- [<span data-ttu-id="8be2d-121">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="8be2d-121">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="8be2d-122">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="8be2d-122">Entity Data Model</span></span>](entity-data-model.md)
