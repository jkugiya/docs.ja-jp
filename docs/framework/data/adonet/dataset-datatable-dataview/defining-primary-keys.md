---
description: '詳細情報: 主キーの定義'
title: 主キーの定義
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 2becfbd124af723f55edb39666352fc501044045
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652550"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="98e5d-103">主キーの定義</span><span class="sxs-lookup"><span data-stu-id="98e5d-103">Defining Primary Keys</span></span>

<span data-ttu-id="98e5d-104">通常、データベース テーブルには、テーブル内の各行を一意に識別する単一の列または複数の列があります。</span><span class="sxs-lookup"><span data-stu-id="98e5d-104">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="98e5d-105">行を識別するこのような列を、主キーと呼びます。</span><span class="sxs-lookup"><span data-stu-id="98e5d-105">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="98e5d-106">1 つの <xref:System.Data.DataColumn> を <xref:System.Data.DataTable> の <xref:System.Data.DataTable.PrimaryKey%2A> として指定すると、テーブルによってその列の <xref:System.Data.DataColumn.AllowDBNull%2A> プロパティが **false** に、<xref:System.Data.DataColumn.Unique%2A> プロパティが **true** に自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="98e5d-106">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="98e5d-107">複数列の主キーの場合は、**AllowDBNull** プロパティだけが自動的に **false** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="98e5d-107">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="98e5d-108"><xref:System.Data.DataTable> の **PrimaryKey** プロパティがその値として、1 つ以上の **DataColumn** オブジェクトから成る配列を受け取る例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="98e5d-108">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="98e5d-109">最初の例は、1 つの列を主キーとして定義しています。</span><span class="sxs-lookup"><span data-stu-id="98e5d-109">The first example defines a single column as the primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 <span data-ttu-id="98e5d-110">2 つの列を主キーとして定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="98e5d-110">The following example defines two columns as a primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a><span data-ttu-id="98e5d-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="98e5d-111">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="98e5d-112">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="98e5d-112">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="98e5d-113">DataTables</span><span class="sxs-lookup"><span data-stu-id="98e5d-113">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="98e5d-114">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="98e5d-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
