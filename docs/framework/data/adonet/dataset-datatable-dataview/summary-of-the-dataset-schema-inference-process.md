---
description: '詳細情報: DataSet スキーマの推論プロセスの概要'
title: DataSet スキーマの推論プロセスの概要
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 637e4325558708c15d6d4eb17de9c0cf13b3b256
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651562"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="0c20a-103">DataSet スキーマの推論プロセスの概要</span><span class="sxs-lookup"><span data-stu-id="0c20a-103">Summary of the DataSet Schema Inference Process</span></span>

<span data-ttu-id="0c20a-104">推論プロセスでは、まず、テーブルとして推論する XML ドキュメントの要素を決定します。</span><span class="sxs-lookup"><span data-stu-id="0c20a-104">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="0c20a-105">XML ドキュメントの残りの要素から、それらのテーブルの列が推論によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-105">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="0c20a-106">入れ子状のテーブルの場合は、入れ子になった <xref:System.Data.DataRelation> オブジェクトと <xref:System.Data.ForeignKeyConstraint> オブジェクトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-106">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="0c20a-107">推論規則について、次に簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="0c20a-107">The following is a brief summary of inference rules:</span></span>  
  
- <span data-ttu-id="0c20a-108">属性を持つ要素は、テーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-108">Elements that have attributes are inferred as tables.</span></span>  
  
- <span data-ttu-id="0c20a-109">子要素を持つ要素は、テーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-109">Elements that have child elements are inferred as tables.</span></span>  
  
- <span data-ttu-id="0c20a-110">繰り返し出現する要素は、単一のテーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-110">Elements that repeat are inferred as a single table.</span></span>  
  
- <span data-ttu-id="0c20a-111">ドキュメント (ルート) 要素に属性がなく、列として推論される子要素もない場合、その要素は <xref:System.Data.DataSet> として推論されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-111">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="0c20a-112">それ以外の場合は、ドキュメント要素はテーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-112">Otherwise, the document element is inferred as a table.</span></span>  
  
- <span data-ttu-id="0c20a-113">属性は、列として推論されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-113">Attributes are inferred as columns.</span></span>  
  
- <span data-ttu-id="0c20a-114">属性または子要素を持たず、繰り返し出現することもない要素は、列として推論されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-114">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
- <span data-ttu-id="0c20a-115">テーブルとして推論される要素が、同じくテーブルとして推論される他の要素の内部に入れ子になっている場合は、その 2 つのテーブル間に入れ子になった **DataRelation** が作成されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-115">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="0c20a-116">その場合、**TableName_Id** という名前の新しい主キー列がその両方のテーブルに追加され、**DataRelation** によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-116">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="0c20a-117">この **TableName_Id** 列を使用して、この 2 つのテーブル間に **ForeignKeyConstraint** が作成されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-117">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
- <span data-ttu-id="0c20a-118">テーブルとして推論される要素に、テキストは含まれているが子要素は含まれていない場合は、**TableName_Text** という名前の新しい列が各要素のテキストに作成されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-118">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="0c20a-119">テーブルとして推論される要素にテキストだけでなく、子要素もある場合、テキストは無視されます。</span><span class="sxs-lookup"><span data-stu-id="0c20a-119">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c20a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c20a-120">See also</span></span>

- [<span data-ttu-id="0c20a-121">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="0c20a-121">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="0c20a-122">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="0c20a-122">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="0c20a-123">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="0c20a-123">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="0c20a-124">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="0c20a-124">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="0c20a-125">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="0c20a-125">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="0c20a-126">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="0c20a-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
