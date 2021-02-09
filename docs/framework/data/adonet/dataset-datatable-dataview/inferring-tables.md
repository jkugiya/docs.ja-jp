---
description: '詳細情報: テーブルの推論'
title: テーブルの推論
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 00a24cbfc44aea4279b0a115214ec26d3eac59ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652160"
---
# <a name="inferring-tables"></a><span data-ttu-id="fb1d0-103">テーブルの推論</span><span class="sxs-lookup"><span data-stu-id="fb1d0-103">Inferring Tables</span></span>

<span data-ttu-id="fb1d0-104">XML ドキュメントから <xref:System.Data.DataSet> のスキーマを推論するときには、ADO.NET では、テーブルを表す XML 要素を最初に決定します。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-104">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="fb1d0-105">次に示す XML 構造では、**DataSet** スキーマのテーブルが推論されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-105">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="fb1d0-106">属性を持つ要素</span><span class="sxs-lookup"><span data-stu-id="fb1d0-106">Elements with attributes</span></span>  
  
- <span data-ttu-id="fb1d0-107">子要素を持つ要素</span><span class="sxs-lookup"><span data-stu-id="fb1d0-107">Elements with child elements</span></span>  
  
- <span data-ttu-id="fb1d0-108">繰り返し出現する要素</span><span class="sxs-lookup"><span data-stu-id="fb1d0-108">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="fb1d0-109">属性を持つ要素</span><span class="sxs-lookup"><span data-stu-id="fb1d0-109">Elements with Attributes</span></span>  

 <span data-ttu-id="fb1d0-110">要素に属性が指定されている場合は、それらの要素はテーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-110">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="fb1d0-111">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-111">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fb1d0-112">推論プロセスにより、"Element1" という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-112">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="fb1d0-113">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fb1d0-113">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fb1d0-114">**テーブル:** Element1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-114">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fb1d0-115">attr1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-115">attr1</span></span>|<span data-ttu-id="fb1d0-116">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="fb1d0-116">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="fb1d0-117">value1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-117">value1</span></span>||  
|<span data-ttu-id="fb1d0-118">value2</span><span class="sxs-lookup"><span data-stu-id="fb1d0-118">value2</span></span>|<span data-ttu-id="fb1d0-119">Text1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-119">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="fb1d0-120">子要素を持つ要素</span><span class="sxs-lookup"><span data-stu-id="fb1d0-120">Elements with Child Elements</span></span>  

 <span data-ttu-id="fb1d0-121">子要素を持つ要素は、テーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-121">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="fb1d0-122">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-122">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fb1d0-123">推論プロセスにより、"Element1" という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-123">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="fb1d0-124">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fb1d0-124">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fb1d0-125">**テーブル:** Element1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-125">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fb1d0-126">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-126">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="fb1d0-127">Text1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-127">Text1</span></span>|  
  
 <span data-ttu-id="fb1d0-128">ドキュメント (ルート) 要素に属性または子要素があり、それらが列として推論される場合には、そのドキュメント要素はテーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-128">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="fb1d0-129">ドキュメント要素の属性や子要素が列として推論されない場合、そのドキュメント要素は **DataSet** として推論されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-129">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="fb1d0-130">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-130">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fb1d0-131">推論プロセスにより、"DocumentElement" という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-131">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="fb1d0-132">**DataSet:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="fb1d0-132">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="fb1d0-133">**テーブル:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fb1d0-133">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="fb1d0-134">Element1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-134">Element1</span></span>|<span data-ttu-id="fb1d0-135">Element2</span><span class="sxs-lookup"><span data-stu-id="fb1d0-135">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="fb1d0-136">Text1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-136">Text1</span></span>|<span data-ttu-id="fb1d0-137">Text2</span><span class="sxs-lookup"><span data-stu-id="fb1d0-137">Text2</span></span>|  
  
 <span data-ttu-id="fb1d0-138">または、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-138">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fb1d0-139">推論プロセスにより、"Element1" という名前のテーブルを含む "DocumentElement" という名前の **DataSet** が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-139">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="fb1d0-140">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fb1d0-140">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fb1d0-141">**テーブル:** Element1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-141">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fb1d0-142">attr1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-142">attr1</span></span>|<span data-ttu-id="fb1d0-143">attr2</span><span class="sxs-lookup"><span data-stu-id="fb1d0-143">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="fb1d0-144">value1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-144">value1</span></span>|<span data-ttu-id="fb1d0-145">value2</span><span class="sxs-lookup"><span data-stu-id="fb1d0-145">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="fb1d0-146">繰り返し出現する要素</span><span class="sxs-lookup"><span data-stu-id="fb1d0-146">Repeating Elements</span></span>  

 <span data-ttu-id="fb1d0-147">繰り返し出現する要素は、単一のテーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-147">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="fb1d0-148">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-148">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fb1d0-149">推論プロセスにより、"Element1" という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="fb1d0-149">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="fb1d0-150">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fb1d0-150">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fb1d0-151">**テーブル:** Element1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-151">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fb1d0-152">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="fb1d0-152">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="fb1d0-153">Text1</span><span class="sxs-lookup"><span data-stu-id="fb1d0-153">Text1</span></span>|  
|<span data-ttu-id="fb1d0-154">Text2</span><span class="sxs-lookup"><span data-stu-id="fb1d0-154">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb1d0-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb1d0-155">See also</span></span>

- [<span data-ttu-id="fb1d0-156">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="fb1d0-156">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="fb1d0-157">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="fb1d0-157">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="fb1d0-158">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="fb1d0-158">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="fb1d0-159">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="fb1d0-159">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="fb1d0-160">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="fb1d0-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="fb1d0-161">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="fb1d0-161">ADO.NET Overview</span></span>](../ado-net-overview.md)
