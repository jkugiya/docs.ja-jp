---
description: '詳細情報: DataView の変更'
title: DataView の変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: e0f62c0b8553cd4b83c28da99b8bdec316c8a91d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651835"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="e05c0-103">DataView の変更</span><span class="sxs-lookup"><span data-stu-id="e05c0-103">Modifying DataViews</span></span>

<span data-ttu-id="e05c0-104"><xref:System.Data.DataView> を使用して、データ行を基になるテーブルに追加、削除、または変更できます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-104">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="e05c0-105">基になるテーブルのデータを **DataView** で変更できるかどうかは、**DataView** の 3 つのブール値プロパティで制御されます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-105">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="e05c0-106">この 3 つのプロパティとは、<xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> および <xref:System.Data.DataView.AllowDelete%2A> です。</span><span class="sxs-lookup"><span data-stu-id="e05c0-106">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="e05c0-107">これらのプロパティの既定値は **true** です。</span><span class="sxs-lookup"><span data-stu-id="e05c0-107">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="e05c0-108">**AllowNew** が **true** の場合は、**DataView** の <xref:System.Data.DataView.AddNew%2A> メソッドを使用して新しい <xref:System.Data.DataRowView> を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-108">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="e05c0-109">**DataRowView** の <xref:System.Data.DataRowView.EndEdit%2A> メソッドが呼び出されるまで、基になる <xref:System.Data.DataTable> に新しい行が実際に追加されることはないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e05c0-109">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="e05c0-110">**DataRowView** の <xref:System.Data.DataRowView.CancelEdit%2A> メソッドが呼び出されると、新しい行は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-110">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="e05c0-111">また、一度に編集できる **DataRowView** は 1 つだけであることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="e05c0-111">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="e05c0-112">保留中の行がある間に、**DataRowView** の **AddNew** メソッドまたは **BeginEdit** メソッドを呼び出すと、保留中の行に対して **EndEdit** が暗黙的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-112">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="e05c0-113">**EndEdit** が呼び出されると、基になる **DataTable** に対して変更が適用されます。適用された変更をコミットするには **DataTable**、**DataSet**、または **DataRow** オブジェクトの **AcceptChanges** メソッドを使用し、拒否するにはこれらのオブジェクトの **RejectChanges** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e05c0-113">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="e05c0-114">**AllowNew** が **false** の場合は、**DataRowView** の **AddNew** メソッドを呼び出すと例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-114">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="e05c0-115">**AllowEdit** が **true** の場合は、**DataRowView** を使用して **DataRow** の内容を変更できます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-115">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="e05c0-116">基になる行の変更内容を確定するには **DataRowView.EndEdit** を使用し、変更内容を取り消すには **DataRowView.CancelEdit** を使用します。</span><span class="sxs-lookup"><span data-stu-id="e05c0-116">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="e05c0-117">一度に編集できるのは 1 行だけです。</span><span class="sxs-lookup"><span data-stu-id="e05c0-117">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="e05c0-118">保留中の行がある間に、**DataRowView** の **AddNew** メソッドまたは **BeginEdit** メソッドを呼び出すと、保留中の行に対して **EndEdit** が暗黙的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-118">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="e05c0-119">**EndEdit** が呼び出されると、基になる **DataRow** の **Current** 行バージョンに対して変更が適用されます。適用された変更をコミットするには **DataTable**、**DataSet**、または **DataRow** オブジェクトの **AcceptChanges** メソッドを使用し、拒否するにはこれらのオブジェクトの **RejectChanges** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e05c0-119">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="e05c0-120">**AllowEdit** が **false** の場合、**DataView** の値を変更しようとすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-120">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="e05c0-121">既存の **DataRowView** の編集中でも、まだ確定されていない変更に関して、基になる **DataTable** のイベントが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e05c0-121">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="e05c0-122">**DataRowView** に対して **EndEdit** と **CancelEdit** のどちらが呼び出されているかに関係なく、基になる **DataRow** に対して **EndEdit** を呼び出すと、確定されていない変更が適用され、**CancelEdit** を呼び出すと、確定されていない変更が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-122">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="e05c0-123">**AllowDelete** が **true** の場合は、**DataView** オブジェクトまたは **DataRowView** オブジェクトの **Delete** メソッドを使用して **DataView** から行を削除することができ、基になる **DataTable** から行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-123">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="e05c0-124">後でこの削除操作をコミットするには **AcceptChanges** を使用し、拒否するには **RejectChanges** を使用します。</span><span class="sxs-lookup"><span data-stu-id="e05c0-124">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="e05c0-125">**AllowDelete** が **false** の場合は、**DataView** または **DataRowView** の **Delete** メソッドを呼び出すと例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e05c0-125">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="e05c0-126">次のコード例では、**DataView** を使用して行を削除する機能を無効にし、**DataView** を使用して基になるテーブルに新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="e05c0-126">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="e05c0-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="e05c0-127">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="e05c0-128">DataViews</span><span class="sxs-lookup"><span data-stu-id="e05c0-128">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="e05c0-129">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="e05c0-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
