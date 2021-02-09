---
description: '詳細情報: DataRow および DataRowView'
title: DataRow および DataRowView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: d7700922a9ae76fb9898412b6a08394059e6e494
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724948"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="f401d-103">DataRow および DataRowView</span><span class="sxs-lookup"><span data-stu-id="f401d-103">DataRows and DataRowViews</span></span>

<span data-ttu-id="f401d-104"><xref:System.Data.DataView> は、<xref:System.Data.DataRowView> オブジェクトの列挙可能なコレクションを公開します。</span><span class="sxs-lookup"><span data-stu-id="f401d-104">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="f401d-105">**DataRowView** オブジェクトは、基になるテーブルの列の名前または列の序数参照によってインデックスが設定されているオブジェクトの配列として値を公開します。</span><span class="sxs-lookup"><span data-stu-id="f401d-105">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="f401d-106">**DataRowView** の <xref:System.Data.DataRowView.Row%2A> プロパティを使用することによって、**DataRowView** で公開されている <xref:System.Data.DataRow> にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f401d-106">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="f401d-107">**DataRowView** を使用して値を表示している場合は、**DataView** の <xref:System.Data.DataView.RowStateFilter%2A> プロパティによって、基になる **DataRow** から公開される行バージョンが決まります。</span><span class="sxs-lookup"><span data-stu-id="f401d-107">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="f401d-108">**DataRow** を使用してさまざまな行バージョンにアクセスする方法については、「[行の状態とバージョン](row-states-and-row-versions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f401d-108">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="f401d-109">テーブルの現在の値と元の値をすべて表示するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f401d-109">The following code example displays all the current and original values in a table.</span></span>  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f401d-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="f401d-110">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="f401d-111">DataViews</span><span class="sxs-lookup"><span data-stu-id="f401d-111">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="f401d-112">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="f401d-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
