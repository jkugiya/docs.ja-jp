---
description: '詳細情報: DataTable の編集'
title: DataTable の編集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 983a4016fbdb71baa3bcd4ce8a34175d10b604d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739470"
---
# <a name="datatable-edits"></a><span data-ttu-id="eb050-103">DataTable の編集</span><span class="sxs-lookup"><span data-stu-id="eb050-103">DataTable Edits</span></span>

<span data-ttu-id="eb050-104"><xref:System.Data.DataRow> 内の列値を変更すると、その変更はすぐに行の現在の状態に反映されます。</span><span class="sxs-lookup"><span data-stu-id="eb050-104">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="eb050-105">次に、<xref:System.Data.DataRowState> は **Modified** に設定され、**DataRow** の <xref:System.Data.DataRow.AcceptChanges%2A> または <xref:System.Data.DataRow.RejectChanges%2A> メソッドを使用して、変更が承認または拒否されます。</span><span class="sxs-lookup"><span data-stu-id="eb050-105">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="eb050-106">**DataRow** では、行の編集中に、その行の状態を保留にしておくために使用できる 3 つのメソッドも提供されます。</span><span class="sxs-lookup"><span data-stu-id="eb050-106">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="eb050-107">これらのメソッドとは、<xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> および <xref:System.Data.DataRow.CancelEdit%2A> です。</span><span class="sxs-lookup"><span data-stu-id="eb050-107">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="eb050-108">**DataRow** の列値が直接変更されると、**DataRow** によって、**Current**、**Default**、**Original** の各行バージョンを使用して列値が管理されます。</span><span class="sxs-lookup"><span data-stu-id="eb050-108">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="eb050-109">**BeginEdit**、**EndEdit**、**CancelEdit** の各メソッドでは、これらの行バージョンに加えて、4 番目の行バージョンが使用されます: **Proposed**。</span><span class="sxs-lookup"><span data-stu-id="eb050-109">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="eb050-110">行バージョンについて詳しくは、「[行の状態とバージョン](row-states-and-row-versions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eb050-110">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="eb050-111">**Proposed** 行バージョンは、編集操作中に存在するバージョンです。編集操作は、**BeginEdit** への呼び出しによって開始し、**EndEdit** または **CancelEdit** の使用あるいは **AcceptChanges** または **RejectChanges** の呼び出しによって終了します。</span><span class="sxs-lookup"><span data-stu-id="eb050-111">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="eb050-112">編集操作中に、**DataTable** の **ColumnChanged** イベントで **ProposedValue** を評価することにより、個々の列に検証ロジックを適用できます。</span><span class="sxs-lookup"><span data-stu-id="eb050-112">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="eb050-113">**ColumnChanged** イベントは、変更されている列への参照および **ProposedValue** への参照を維持する **DataColumnChangeEventArgs** を保持します。</span><span class="sxs-lookup"><span data-stu-id="eb050-113">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="eb050-114">提示された値を評価した後で、値を変更するか、または編集をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="eb050-114">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="eb050-115">編集が終了すると、行は **Proposed** 状態ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="eb050-115">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="eb050-116">**EndEdit** を呼び出すと編集内容を確定でき、**CancelEdit** を呼び出すと編集内容をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="eb050-116">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="eb050-117">**EndEdit** は編集内容を確定しますが、**DataSet** は **AcceptChanges** が呼び出されるまでは実際には変更を受け入れません。</span><span class="sxs-lookup"><span data-stu-id="eb050-117">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="eb050-118">また、**EndEdit** または **CancelEdit** を使用して編集を終了する前に **AcceptChanges** を呼び出した場合は、編集が終了し、**Proposed** 行値が **Current** 行バージョンと **Original** 行バージョンの両方に受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="eb050-118">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="eb050-119">同様に、**RejectChanges** を呼び出した場合も編集が終了し、**Current** 行バージョンと **Proposed** 行バージョンの両方が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="eb050-119">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="eb050-120">**AcceptChanges** または **RejectChanges** を呼び出した後で **EndEdit** または **CancelEdit** を呼び出しても、編集が既に終了しているため、その呼び出しは無効になります。</span><span class="sxs-lookup"><span data-stu-id="eb050-120">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="eb050-121">**BeginEdit**、**EndEdit**、および **CancelEdit** を使用する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="eb050-121">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="eb050-122">この例では、**ColumnChanged** イベントで **ProposedValue** をチェックして、編集をキャンセルするかどうかを決定しています。</span><span class="sxs-lookup"><span data-stu-id="eb050-122">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb050-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb050-123">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="eb050-124">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="eb050-124">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="eb050-125">DataTable イベントの処理</span><span class="sxs-lookup"><span data-stu-id="eb050-125">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="eb050-126">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="eb050-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
