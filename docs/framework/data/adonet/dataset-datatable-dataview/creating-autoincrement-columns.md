---
description: '詳細情報: AutoIncrement 列の作成'
title: AutoIncrement 列の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 7568b1013b7af5aef7a6fc1f28dc163a082743a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739639"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="f8d90-103">AutoIncrement 列の作成</span><span class="sxs-lookup"><span data-stu-id="f8d90-103">Creating AutoIncrement Columns</span></span>

<span data-ttu-id="f8d90-104">列値を一意にするために、新しい行がテーブルに追加されたときに列値が自動的にインクリメントされるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="f8d90-104">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="f8d90-105">自動インクリメント <xref:System.Data.DataColumn> を作成するには、列の <xref:System.Data.DataColumn.AutoIncrement%2A> プロパティを **true** に設定します。</span><span class="sxs-lookup"><span data-stu-id="f8d90-105">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="f8d90-106"><xref:System.Data.DataColumn> の値は <xref:System.Data.DataColumn.AutoIncrementSeed%2A> プロパティで定義された値から開始され、行が追加されるたびに、**AutoIncrement** 列の値には、列の <xref:System.Data.DataColumn.AutoIncrementStep%2A> プロパティで定義された値が加算されます。</span><span class="sxs-lookup"><span data-stu-id="f8d90-106">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="f8d90-107">**AutoIncrement** 列では、**DataColumn** の <xref:System.Data.DataColumn.ReadOnly%2A> プロパティを **true** に設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f8d90-107">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="f8d90-108">値 200 から開始して 3 ずつインクリメントする列を作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="f8d90-108">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8d90-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8d90-109">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="f8d90-110">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="f8d90-110">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="f8d90-111">DataTables</span><span class="sxs-lookup"><span data-stu-id="f8d90-111">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="f8d90-112">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="f8d90-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
