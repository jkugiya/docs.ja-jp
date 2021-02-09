---
description: '詳細情報: 要素のテキストの推論'
title: 要素のテキストの推論
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 5d0d9b1b3bb6164cd3cf26b429a4c7d658ee4128
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652212"
---
# <a name="inferring-element-text"></a><span data-ttu-id="85b4a-103">要素のテキストの推論</span><span class="sxs-lookup"><span data-stu-id="85b4a-103">Inferring Element Text</span></span>

<span data-ttu-id="85b4a-104">要素にテキストは含まれているが、テーブルとして推論される (属性を持つ要素または繰り返し出現する要素などの) 子の要素がない場合は、**TableName_Text** という名前の新しい列が、要素に対して推論されるテーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-104">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="85b4a-105">要素に含まれているテキストはテーブルの行に追加され、新しい列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-105">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="85b4a-106">新しい列の **ColumnMapping** プロパティは、**MappingType.SimpleContent** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-106">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="85b4a-107">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="85b4a-107">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="85b4a-108">推論プロセスにより、**attr1** および **Element1_Text** という 2 つの列を持つ **Element1** という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-108">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="85b4a-109">**attr1** 列の **ColumnMapping** プロパティは、**MappingType.Attribute** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-109">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="85b4a-110">**Element1_Text** 列の **ColumnMapping** プロパティは、**MappingType.SimpleContent** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-110">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="85b4a-111">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="85b4a-111">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="85b4a-112">**テーブル:** Element1</span><span class="sxs-lookup"><span data-stu-id="85b4a-112">**Table:** Element1</span></span>  
  
|<span data-ttu-id="85b4a-113">attr1</span><span class="sxs-lookup"><span data-stu-id="85b4a-113">attr1</span></span>|<span data-ttu-id="85b4a-114">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="85b4a-114">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="85b4a-115">value1</span><span class="sxs-lookup"><span data-stu-id="85b4a-115">value1</span></span>|<span data-ttu-id="85b4a-116">Text1</span><span class="sxs-lookup"><span data-stu-id="85b4a-116">Text1</span></span>|  
  
 <span data-ttu-id="85b4a-117">要素にテキストだけでなく、テキストを含む子の要素も含まれている場合は、その要素に含まれているテキストを格納するための列はテーブルに追加されません。</span><span class="sxs-lookup"><span data-stu-id="85b4a-117">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="85b4a-118">要素に含まれるテキストは無視されますが、子の要素のテキストはテーブルの行に追加されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-118">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="85b4a-119">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="85b4a-119">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="85b4a-120">推論プロセスにより、**ChildElement1** という 1 つの列を持つ **Element1** という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-120">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="85b4a-121">**ChildElement1** 要素のテキストは、テーブルの行に追加されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-121">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="85b4a-122">その他のテキストは無視されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-122">The other text will be ignored.</span></span> <span data-ttu-id="85b4a-123">**ChildElement1** 列の **ColumnMapping** プロパティは、**MappingType.Element** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="85b4a-123">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="85b4a-124">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="85b4a-124">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="85b4a-125">**テーブル:** Element1</span><span class="sxs-lookup"><span data-stu-id="85b4a-125">**Table:** Element1</span></span>  
  
|<span data-ttu-id="85b4a-126">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="85b4a-126">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="85b4a-127">Text2</span><span class="sxs-lookup"><span data-stu-id="85b4a-127">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85b4a-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="85b4a-128">See also</span></span>

- [<span data-ttu-id="85b4a-129">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="85b4a-129">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="85b4a-130">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="85b4a-130">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="85b4a-131">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="85b4a-131">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="85b4a-132">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="85b4a-132">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="85b4a-133">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="85b4a-133">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="85b4a-134">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="85b4a-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
