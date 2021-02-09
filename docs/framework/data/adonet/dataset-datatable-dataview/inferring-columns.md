---
description: '詳細情報: 列の推論'
title: 列の推論
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 528d4ea20260b5f1fbf30536eafcaec8c5f9215a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652251"
---
# <a name="inferring-columns"></a><span data-ttu-id="0dad8-103">列の推論</span><span class="sxs-lookup"><span data-stu-id="0dad8-103">Inferring Columns</span></span>

<span data-ttu-id="0dad8-104">ADO.NET は、<xref:System.Data.DataSet> のテーブルとして推論する要素を、XML ドキュメントから決定した後、それらのテーブルの列を推論します。</span><span class="sxs-lookup"><span data-stu-id="0dad8-104">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="0dad8-105">ADO.NET 2.0 では、各 **simpleType** 要素の厳密に型指定されたデータ型を推論する新しいスキーマ推論エンジンが導入されました。</span><span class="sxs-lookup"><span data-stu-id="0dad8-105">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="0dad8-106">以前のバージョンでは、推論される **simpleType** 要素のデータ型は、常に **xsd:string** でした。</span><span class="sxs-lookup"><span data-stu-id="0dad8-106">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="0dad8-107">移行および下位互換性</span><span class="sxs-lookup"><span data-stu-id="0dad8-107">Migration and Backward Compatibility</span></span>  

 <span data-ttu-id="0dad8-108">**ReadXml** メソッドは、**InferSchema** 型の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0dad8-108">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="0dad8-109">この引数を使用することにより、以前のバージョンと互換性のある推論方法を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-109">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="0dad8-110">**InferSchema** 列挙型で使用できる値を、次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="0dad8-110">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="0dad8-111">単純型を <xref:System.String> として常に推論することで下位互換性を提供します。</span><span class="sxs-lookup"><span data-stu-id="0dad8-111">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="0dad8-112">厳密に型指定されたデータ型を推論します。</span><span class="sxs-lookup"><span data-stu-id="0dad8-112">Infers a strongly typed data type.</span></span> <span data-ttu-id="0dad8-113"><xref:System.Data.DataTable> で使用した場合、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="0dad8-113">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="0dad8-114">インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマに読み取ります。</span><span class="sxs-lookup"><span data-stu-id="0dad8-114">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="0dad8-115">属性</span><span class="sxs-lookup"><span data-stu-id="0dad8-115">Attributes</span></span>  

 <span data-ttu-id="0dad8-116">「[テーブルの推論](inferring-tables.md)」で説明されているように、属性を持つ要素は、テーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-116">As defined in [Inferring Tables](inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="0dad8-117">その要素の属性は、そのテーブルの列として推論されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-117">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="0dad8-118">スキーマが XML に書き戻される場合に、列の名前が確実に属性として書き込まれるように、推論された列の **ColumnMapping** プロパティは **MappingType.Attribute** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-118">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="0dad8-119">属性の値は、テーブルの行に格納されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-119">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="0dad8-120">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="0dad8-120">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0dad8-121">推論プロセスにより、**attr1** および **attr2** という 2 つの列を持つ **Element1** という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-121">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="0dad8-122">2 つの列の **ColumnMapping** プロパティは、**MappingType.Attribute** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-122">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="0dad8-123">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0dad8-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0dad8-124">**テーブル:** Element1</span><span class="sxs-lookup"><span data-stu-id="0dad8-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0dad8-125">attr1</span><span class="sxs-lookup"><span data-stu-id="0dad8-125">attr1</span></span>|<span data-ttu-id="0dad8-126">attr2</span><span class="sxs-lookup"><span data-stu-id="0dad8-126">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="0dad8-127">value1</span><span class="sxs-lookup"><span data-stu-id="0dad8-127">value1</span></span>|<span data-ttu-id="0dad8-128">value2</span><span class="sxs-lookup"><span data-stu-id="0dad8-128">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="0dad8-129">属性または子の要素を持たない要素</span><span class="sxs-lookup"><span data-stu-id="0dad8-129">Elements Without Attributes or Child Elements</span></span>  

 <span data-ttu-id="0dad8-130">要素に子の要素または属性がない場合、その要素は列として推論されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-130">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="0dad8-131">列の **ColumnMapping** プロパティは、**MappingType.Element** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-131">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="0dad8-132">子の要素のテキストは、テーブルの行に格納されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-132">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="0dad8-133">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="0dad8-133">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0dad8-134">推論プロセスにより、**ChildElement1** および **ChildElement2** という 2 つの列を持つ **Element1** という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-134">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="0dad8-135">2 つの列の **ColumnMapping** プロパティは、**MappingType.Element** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0dad8-135">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="0dad8-136">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0dad8-136">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0dad8-137">**テーブル:** Element1</span><span class="sxs-lookup"><span data-stu-id="0dad8-137">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0dad8-138">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0dad8-138">ChildElement1</span></span>|<span data-ttu-id="0dad8-139">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="0dad8-139">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="0dad8-140">Text1</span><span class="sxs-lookup"><span data-stu-id="0dad8-140">Text1</span></span>|<span data-ttu-id="0dad8-141">Text2</span><span class="sxs-lookup"><span data-stu-id="0dad8-141">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0dad8-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="0dad8-142">See also</span></span>

- [<span data-ttu-id="0dad8-143">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="0dad8-143">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="0dad8-144">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="0dad8-144">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="0dad8-145">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="0dad8-145">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="0dad8-146">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="0dad8-146">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="0dad8-147">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="0dad8-147">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="0dad8-148">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="0dad8-148">ADO.NET Overview</span></span>](../ado-net-overview.md)
