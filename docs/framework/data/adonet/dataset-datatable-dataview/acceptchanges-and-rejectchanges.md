---
description: '詳細情報: AcceptChange と RejectChange'
title: AcceptChange と RejectChange
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: e21952063bf27f4f969669eb76b964fc7537b59a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725260"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="956d2-103">AcceptChange と RejectChange</span><span class="sxs-lookup"><span data-stu-id="956d2-103">AcceptChanges and RejectChanges</span></span>

<span data-ttu-id="956d2-104"><xref:System.Data.DataTable> 内のデータに行われた変更が正確であるかどうかを検証した後で、<xref:System.Data.DataRow>、<xref:System.Data.DataTable>、または <xref:System.Data.DataSet> の <xref:System.Data.DataRow.AcceptChanges%2A> メソッドを使用して、変更を受け入れることができます。変更を受け入れると、**Current** 行の値が **Original** の値に設定され、**RowState** プロパティが **Unchanged** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="956d2-104">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="956d2-105">変更を受け入れるかまたは拒否すると、**RowError** 情報が削除され、**HasErrors** プロパティが **false** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="956d2-105">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="956d2-106">変更を受け入れるかまたは拒否した場合、データ ソース内で実行中の更新操作にも影響することがあります。</span><span class="sxs-lookup"><span data-stu-id="956d2-106">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="956d2-107">詳しくは、「[DataAdapter によるデータ ソースの更新](../updating-data-sources-with-dataadapters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="956d2-107">For more information, see [Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="956d2-108">**DataTable** に外部キー制約が存在する場合、**AcceptChanges** と **RejectChanges** を使用して受け入れられた変更または拒否された変更は、**ForeignKeyConstraint.AcceptRejectRule** に従って **DataRow** の子の行に反映されます。</span><span class="sxs-lookup"><span data-stu-id="956d2-108">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="956d2-109">詳しくは、「[DataTable の制約](datatable-constraints.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="956d2-109">For more information, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="956d2-110">行にエラーがあるかどうかをチェックし、必要に応じてエラーを解決し、エラーを解決できない場合にはその行を拒否する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="956d2-110">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="956d2-111">解決されたエラーについては、**RowError** 値が空の文字列にリセットされるため、**HasErrors** プロパティが **false** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="956d2-111">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="956d2-112">エラーのある行がすべて解決または拒否された時点で、**DataTable** 全体に対するすべての変更を受け入れるために、**AcceptChanges** が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="956d2-112">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a><span data-ttu-id="956d2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="956d2-113">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="956d2-114">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="956d2-114">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="956d2-115">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="956d2-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
