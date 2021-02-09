---
description: '詳細情報: DataRow の削除'
title: DataRow の削除
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: fff3117256629c2fa0262e2aa163da09174390dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739574"
---
# <a name="datarow-deletion"></a><span data-ttu-id="a6639-103">DataRow の削除</span><span class="sxs-lookup"><span data-stu-id="a6639-103">DataRow Deletion</span></span>

<span data-ttu-id="a6639-104"><xref:System.Data.DataTable> オブジェクトから <xref:System.Data.DataRow> オブジェクトを削除するには、<xref:System.Data.DataRowCollection> オブジェクトの **Remove** メソッドと **DataRow** オブジェクトの <xref:System.Data.DataRow.Delete%2A> メソッドの、2 つのメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6639-104">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="a6639-105"><xref:System.Data.DataRowCollection.Remove%2A> メソッドでは **DataRowCollection** から **DataRow** が削除されるのに対し、<xref:System.Data.DataRow.Delete%2A> メソッドでは削除対象の行がマークされるだけです。</span><span class="sxs-lookup"><span data-stu-id="a6639-105">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="a6639-106">実際の削除は、アプリケーションで **AcceptChanges** メソッドを呼び出すと実行されます。</span><span class="sxs-lookup"><span data-stu-id="a6639-106">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="a6639-107"><xref:System.Data.DataRow.Delete%2A> を使用すると、行を実際に削除する前に、削除対象としてどの行がマークされているかをプログラムによってチェックできます。</span><span class="sxs-lookup"><span data-stu-id="a6639-107">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="a6639-108">削除対象としてマークされている行の <xref:System.Data.DataRow.RowState%2A> プロパティは、<xref:System.Data.DataRow.Delete%2A> に設定されています。</span><span class="sxs-lookup"><span data-stu-id="a6639-108">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="a6639-109"><xref:System.Data.DataRow.Delete%2A> オブジェクトを反復処理している間は、foreach ループで <xref:System.Data.DataRowCollection.Remove%2A> も <xref:System.Data.DataRowCollection> も呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="a6639-109">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="a6639-110"><xref:System.Data.DataRow.Delete%2A> または <xref:System.Data.DataRowCollection.Remove%2A> はコレクションの状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="a6639-110"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="a6639-111">**DataAdapter** およびリレーショナル データ ソースに関連して <xref:System.Data.DataSet> または **DataTable** を使用するときは、**DataRow** の **Delete** メソッドを使用して行を削除します。</span><span class="sxs-lookup"><span data-stu-id="a6639-111">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="a6639-112">**Delete** メソッドでは、**DataSet** または **DataTable** の行が **Deleted** としてマークされますが、その行は削除されません。</span><span class="sxs-lookup"><span data-stu-id="a6639-112">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="a6639-113">代わりに、**DataAdapter** で **Deleted** としてマークされた行が検出されたときに、**DeleteCommand** メソッドが実行されて、データ ソースの該当する行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="a6639-113">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="a6639-114">その後、**AcceptChanges** メソッドを使用して、その行を永続的に削除できます。</span><span class="sxs-lookup"><span data-stu-id="a6639-114">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="a6639-115">**Remove** を使用して行を削除すると、行はテーブルから完全に削除されますが、**DataAdapter** ではデータ ソースの行は削除されません。</span><span class="sxs-lookup"><span data-stu-id="a6639-115">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="a6639-116">次の例で示すように、**DataRowCollection** の **Remove** メソッドに引数として **DataRow** を渡すと、その行がコレクションから削除されます。</span><span class="sxs-lookup"><span data-stu-id="a6639-116">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="a6639-117">これに対して、次の例では、**DataRow** で **Delete** メソッドを呼び出して、その **RowState** を **Deleted** に変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a6639-117">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="a6639-118">行を削除対象としてマークしてから **DataTable** オブジェクトの **AcceptChanges** メソッドを呼び出すと、その行が **DataTable** から削除されます。</span><span class="sxs-lookup"><span data-stu-id="a6639-118">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="a6639-119">これに対して、**RejectChanges** を呼び出すと、行の **RowState** はその行が **Deleted** としてマークされる前の状態に戻ります。</span><span class="sxs-lookup"><span data-stu-id="a6639-119">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6639-120">**DataRow** の **RowState** が **Added** である場合、つまりテーブルに行が追加された直後の状態の場合に、その行を **Deleted** としてマークすると、その行はテーブルから削除されます。</span><span class="sxs-lookup"><span data-stu-id="a6639-120">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6639-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6639-121">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="a6639-122">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="a6639-122">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="a6639-123">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="a6639-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
