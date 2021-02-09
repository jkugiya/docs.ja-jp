---
description: '詳細情報: DataTable スキーマの定義'
title: DataTable スキーマの定義
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: b1a48c8a129607dc8d683aa4735ea0e86ed32cc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652615"
---
# <a name="datatable-schema-definition"></a><span data-ttu-id="f2864-103">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="f2864-103">DataTable Schema Definition</span></span>

<span data-ttu-id="f2864-104">テーブルのスキーマ (構造) は、列と制約で表されます。</span><span class="sxs-lookup"><span data-stu-id="f2864-104">The schema, or structure, of a table is represented by columns and constraints.</span></span> <span data-ttu-id="f2864-105"><xref:System.Data.DataTable> のスキーマは、<xref:System.Data.DataColumn>、<xref:System.Data.ForeignKeyConstraint>、<xref:System.Data.UniqueConstraint> の各オブジェクトを使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="f2864-105">You define the schema of a <xref:System.Data.DataTable> using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="f2864-106">テーブルの列は、データ ソースの列に割り当てたり、式で算出された値を格納したり、格納されている値を自動的にインクリメントしたり、主キー値を格納したりできます。</span><span class="sxs-lookup"><span data-stu-id="f2864-106">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="f2864-107">テーブルの列、リレーション、および制約を名前で参照する場合は、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="f2864-107">References by name to columns, relations, and constraints in a table are case-sensitive.</span></span> <span data-ttu-id="f2864-108">複数の列、リレーション、または制約の名前が同じであっても、大文字と小文字が異なっていれば、1 つのテーブルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2864-108">Two or more columns, relations, or constraints can therefore exist in a table that have the same name, but that differ in case.</span></span> <span data-ttu-id="f2864-109">たとえば、**Col1** と **col1** を同時に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2864-109">For example, you can have **Col1** and **col1**.</span></span> <span data-ttu-id="f2864-110">この場合、列を名前で参照するときは、列名の大文字と小文字を正確に指定する必要があります。正確に指定しない場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f2864-110">In such as case, a reference to one of the columns by name must match the case of the column name exactly; otherwise an exception is thrown.</span></span> <span data-ttu-id="f2864-111">たとえば、テーブル **myTable** に列 **Col1** と列 **col1** がある場合、**Col1** は名前 **myTable.Columns["Col1"]** で参照され、**col1** は名前 **myTable.Columns["col1"]** で参照されます。</span><span class="sxs-lookup"><span data-stu-id="f2864-111">For example, if the table **myTable** contains the columns **Col1** and **col1**, you would reference **Col1** by name as **myTable.Columns["Col1"]**, and **col1** as **myTable.Columns["col1"]**.</span></span> <span data-ttu-id="f2864-112">いずれかの列を **myTable.Columns["COL1"]** という名前で参照しようとすると、例外が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f2864-112">Attempting to reference either of the columns as **myTable.Columns["COL1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="f2864-113">大文字と小文字の区別の規則は、特定の名前の列、リレーション、または制約が 1 つしかない場合には適用されません。</span><span class="sxs-lookup"><span data-stu-id="f2864-113">The case-sensitivity rule does not apply if only one column, relation, or constraint  with a particular name exists.</span></span> <span data-ttu-id="f2864-114">つまり、特定の列、リレーション、または制約オブジェクトと名前が一致する列、リレーション、または制約オブジェクトがテーブルに存在しない場合は、大文字と小文字を区別せずにそのオブジェクトを名前で参照することができます。このとき、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="f2864-114">That is, if no other column, relation, or constraint object in the table matches the name of that particular column, relation, or constraint object, you may reference the object by name using any case, and no exception is thrown.</span></span> <span data-ttu-id="f2864-115">たとえば、テーブルに **Col1** が 1 つしかない場合は、**my.Columns["COL1"]** を使用してこの列を参照できます。</span><span class="sxs-lookup"><span data-stu-id="f2864-115">For example, if the table has only **Col1**, you can reference it using **my.Columns["COL1"]**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2864-116">したがって、この動作は **DataTable** の <xref:System.Data.DataTable.CaseSensitive%2A> プロパティの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="f2864-116">The <xref:System.Data.DataTable.CaseSensitive%2A> property of the **DataTable** does not affect this behavior.</span></span> <span data-ttu-id="f2864-117">**CaseSensitive** プロパティは、テーブルのデータに適用され、並べ替え、検索、フィルター処理、制約の適用などに影響を及ぼします。このプロパティは、テーブルの列、リレーション、および制約の参照には適用されません。</span><span class="sxs-lookup"><span data-stu-id="f2864-117">The **CaseSensitive** property applies to the data in a table and affects sorting, searching, filtering, enforcing constraints, and so on, but not to references to the columns, relations, and constraints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2864-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f2864-118">In This Section</span></span>  

 [<span data-ttu-id="f2864-119">DataTable への列の追加</span><span class="sxs-lookup"><span data-stu-id="f2864-119">Adding Columns to a DataTable</span></span>](adding-columns-to-a-datatable.md)  
 <span data-ttu-id="f2864-120">**DataColumn** オブジェクトを使用して、テーブルの列を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2864-120">Describes how to define the columns of a table using **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="f2864-121">式列の作成</span><span class="sxs-lookup"><span data-stu-id="f2864-121">Creating Expression Columns</span></span>](creating-expression-columns.md)  
 <span data-ttu-id="f2864-122">列の **Expression** プロパティを使用して、同じ行にある他の列の値を基に値を計算する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2864-122">Explains how the **Expression** property of a column can be used to calculate values based on the values from other columns in the row.</span></span>  
  
 [<span data-ttu-id="f2864-123">AutoIncrement 列の作成</span><span class="sxs-lookup"><span data-stu-id="f2864-123">Creating AutoIncrement Columns</span></span>](creating-autoincrement-columns.md)  
 <span data-ttu-id="f2864-124">数値を自動的にインクリメントして行ごとに一意の列値が割り当てられるように列を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2864-124">Describes how a column can be set to automatically increment numerical values to ensure a unique column value per row.</span></span>  
  
 [<span data-ttu-id="f2864-125">主キーの定義</span><span class="sxs-lookup"><span data-stu-id="f2864-125">Defining Primary Keys</span></span>](defining-primary-keys.md)  
 <span data-ttu-id="f2864-126">1 つ以上の **DataColumn** オブジェクトからテーブルの主キーを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2864-126">Describes how to specify the primary key of a table from one or more **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="f2864-127">DataTable の制約</span><span class="sxs-lookup"><span data-stu-id="f2864-127">DataTable Constraints</span></span>](datatable-constraints.md)  
 <span data-ttu-id="f2864-128">テーブルの列の外部キー制約と UNIQUE 制約を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2864-128">Describes how to define foreign key and unique constraints for columns in a table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2864-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2864-129">See also</span></span>

- [<span data-ttu-id="f2864-130">DataTables</span><span class="sxs-lookup"><span data-stu-id="f2864-130">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="f2864-131">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="f2864-131">ADO.NET Overview</span></span>](../ado-net-overview.md)
