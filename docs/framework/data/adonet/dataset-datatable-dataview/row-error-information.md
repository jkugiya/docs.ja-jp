---
description: '詳細情報: 行エラー情報'
title: 行エラー情報
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: d3eb8b20893ad47720ebb03ad4ab61940f014bd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651692"
---
# <a name="row-error-information"></a><span data-ttu-id="a1882-103">行エラー情報</span><span class="sxs-lookup"><span data-stu-id="a1882-103">Row Error Information</span></span>

<span data-ttu-id="a1882-104"><xref:System.Data.DataTable> の値を編集しているときに、行エラーに対処する必要をなくすために、エラー情報を行に追加して後で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a1882-104">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="a1882-105"><xref:System.Data.DataRow> オブジェクトは、この目的のために各行に <xref:System.Data.DataRow.RowError%2A> プロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1882-105">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="a1882-106">**DataRow** の **RowError** プロパティにデータを追加すると、その **DataRow** の <xref:System.Data.DataRow.HasErrors%2A> プロパティが **true** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a1882-106">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="a1882-107">**DataRow** が **DataTable** の一部であり、**DataRow.HasErrors** が **true** である場合は、**DataTable.HasErrors** プロパティも **true** になります。</span><span class="sxs-lookup"><span data-stu-id="a1882-107">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="a1882-108">これは、**DataTable** が属している **DataSet** に対しても適用されます。</span><span class="sxs-lookup"><span data-stu-id="a1882-108">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="a1882-109">エラーの有無を確認する場合は、**HasErrors** プロパティをチェックして、エラー情報が追加された行があるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="a1882-109">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="a1882-110">**HasErrors** が **true** の場合は、次の例に示すように、**DataTable** の <xref:System.Data.DataTable.GetErrors%2A> メソッドを使用して、エラーのある行だけを返してチェックすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1882-110">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1882-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1882-111">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="a1882-112">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="a1882-112">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="a1882-113">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="a1882-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
