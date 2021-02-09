---
description: '詳細情報: リレーションシップの推論'
title: リレーションシップの推論
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: a117581d512c1427c638ea862169ab3c7623d783
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652147"
---
# <a name="inferring-relationships"></a><span data-ttu-id="ff599-103">リレーションシップの推論</span><span class="sxs-lookup"><span data-stu-id="ff599-103">Inferring Relationships</span></span>

<span data-ttu-id="ff599-104">テーブルとして推論される要素に、同じくテーブルとして推論される子の要素が含まれている場合には、2 つのテーブル間に <xref:System.Data.DataRelation> が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-104">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="ff599-105">この場合、**ParentTableName_Id** という名前の新しい列が、親の要素に対して作成されたテーブルと、子の要素に対して作成されたテーブルの両方に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-105">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="ff599-106">この ID 列の **ColumnMapping** プロパティは、**MappingType.Hidden** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-106">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="ff599-107">この列が、親テーブルの自動的にインクリメントされる主キーとなり、2 つのテーブル間の **DataRelation** で使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-107">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="ff599-108">推論される他のすべての列のデータ型は **System.String** になりますが、追加される ID 列のデータ型は **System.Int32** になります。</span><span class="sxs-lookup"><span data-stu-id="ff599-108">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="ff599-109">親テーブルと子テーブル両方の新しい列を使用して、**DeleteRule** = **Cascade** である <xref:System.Data.ForeignKeyConstraint> も作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-109">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="ff599-110">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="ff599-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="ff599-111">推論プロセスにより 2 つのテーブルが生成されます: **Element1** と **ChildElement1**。</span><span class="sxs-lookup"><span data-stu-id="ff599-111">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="ff599-112">**Element1** テーブルには、次の 2 つの列があります: **Element1_Id** と **ChildElement2**。</span><span class="sxs-lookup"><span data-stu-id="ff599-112">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="ff599-113">**Element1_Id** 列の **ColumnMapping** プロパティは、**MappingType.Hidden** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-113">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="ff599-114">**ChildElement2** 列の **ColumnMapping** プロパティは、**MappingType.Element** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-114">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="ff599-115">**Element1_Id** 列は、**Element1** テーブルの主キーとして設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-115">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="ff599-116">**ChildElement1** テーブルには、**attr1**、**attr2**、**Element1_Id** という名前の 3 つの列があります。</span><span class="sxs-lookup"><span data-stu-id="ff599-116">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="ff599-117">**attr1** 列と **attr2** 列の **ColumnMapping** プロパティは、**MappingType.Attribute** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-117">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="ff599-118">**Element1_Id** 列の **ColumnMapping** プロパティは、**MappingType.Hidden** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-118">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="ff599-119">両方のテーブルの **Element1_Id** 列を使用して、**DataRelation** と **ForeignKeyConstraint** が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ff599-119">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="ff599-120">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="ff599-120">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="ff599-121">**テーブル:** Element1</span><span class="sxs-lookup"><span data-stu-id="ff599-121">**Table:** Element1</span></span>  
  
|<span data-ttu-id="ff599-122">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="ff599-122">Element1_Id</span></span>|<span data-ttu-id="ff599-123">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="ff599-123">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="ff599-124">0</span><span class="sxs-lookup"><span data-stu-id="ff599-124">0</span></span>|<span data-ttu-id="ff599-125">Text2</span><span class="sxs-lookup"><span data-stu-id="ff599-125">Text2</span></span>|  
  
 <span data-ttu-id="ff599-126">**テーブル:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ff599-126">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="ff599-127">attr1</span><span class="sxs-lookup"><span data-stu-id="ff599-127">attr1</span></span>|<span data-ttu-id="ff599-128">attr2</span><span class="sxs-lookup"><span data-stu-id="ff599-128">attr2</span></span>|<span data-ttu-id="ff599-129">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="ff599-129">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="ff599-130">value1</span><span class="sxs-lookup"><span data-stu-id="ff599-130">value1</span></span>|<span data-ttu-id="ff599-131">value2</span><span class="sxs-lookup"><span data-stu-id="ff599-131">value2</span></span>|<span data-ttu-id="ff599-132">0</span><span class="sxs-lookup"><span data-stu-id="ff599-132">0</span></span>|  
  
 <span data-ttu-id="ff599-133">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ff599-133">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="ff599-134">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="ff599-134">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="ff599-135">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="ff599-135">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="ff599-136">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ff599-136">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="ff599-137">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="ff599-137">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="ff599-138">**Nested:** True</span><span class="sxs-lookup"><span data-stu-id="ff599-138">**Nested:** True</span></span>  
  
 <span data-ttu-id="ff599-139">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ff599-139">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="ff599-140">**Column:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="ff599-140">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="ff599-141">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="ff599-141">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="ff599-142">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ff599-142">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="ff599-143">**DeleteRule:** Cascade</span><span class="sxs-lookup"><span data-stu-id="ff599-143">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="ff599-144">**AcceptRejectRule:** None</span><span class="sxs-lookup"><span data-stu-id="ff599-144">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff599-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff599-145">See also</span></span>

- [<span data-ttu-id="ff599-146">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="ff599-146">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="ff599-147">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="ff599-147">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="ff599-148">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="ff599-148">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="ff599-149">DataRelation の入れ子化</span><span class="sxs-lookup"><span data-stu-id="ff599-149">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="ff599-150">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="ff599-150">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="ff599-151">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="ff599-151">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="ff599-152">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="ff599-152">ADO.NET Overview</span></span>](../ado-net-overview.md)
