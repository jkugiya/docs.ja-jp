---
description: '詳細情報: 行の検索'
title: 行の検索
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: bf4752255945d5bbc0dd5551cd6e84c98fd78c3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652472"
---
# <a name="finding-rows"></a><span data-ttu-id="49d22-103">行の検索</span><span class="sxs-lookup"><span data-stu-id="49d22-103">Finding Rows</span></span>

<span data-ttu-id="49d22-104"><xref:System.Data.DataView.Find%2A> の <xref:System.Data.DataView.FindRows%2A> メソッドと <xref:System.Data.DataView> メソッドを使用すると、並べ替えキーの値に基づいて行を検索できます。</span><span class="sxs-lookup"><span data-stu-id="49d22-104">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="49d22-105">**Find** メソッドと **FindRows** メソッドによる検索で、値の大文字と小文字が区別されるかどうかは、基になる <xref:System.Data.DataTable> の **CaseSensitive** プロパティによって決まります。</span><span class="sxs-lookup"><span data-stu-id="49d22-105">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="49d22-106">検索結果を返すには、検索値が既存の並べ替えキーの値と完全に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="49d22-106">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="49d22-107">**Find** メソッドは、検索条件に一致する <xref:System.Data.DataRowView> のインデックスの整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="49d22-107">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="49d22-108">複数の行が検索条件に一致する場合は、一致した最初の **DataRowView** のインデックスが返されます。</span><span class="sxs-lookup"><span data-stu-id="49d22-108">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="49d22-109">一致する DataRowView がない場合には、**Find** は -1 を返します。</span><span class="sxs-lookup"><span data-stu-id="49d22-109">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="49d22-110">複数の行に一致する検索結果を返すには、**FindRows** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="49d22-110">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="49d22-111">**FindRows** は **Find** メソッドと同様に機能しますが、**DataView** 内で条件に一致するすべての行を参照する **DataRowView** 配列を返す点が Find メソッドとは異なります。</span><span class="sxs-lookup"><span data-stu-id="49d22-111">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="49d22-112">一致する行が見つからない場合、**DataRowView** 配列は空になります。</span><span class="sxs-lookup"><span data-stu-id="49d22-112">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="49d22-113">**Find** メソッドまたは **FindRows** メソッドを使用するには、並べ替え順序を指定する必要があります。並べ替え順序を指定するには、**ApplyDefaultSort** を **true** に設定するか、または **Sort** プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="49d22-113">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="49d22-114">並べ替え順序が指定されないと、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="49d22-114">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="49d22-115">**Find** メソッドと **FindRows** メソッドには、並べ替え順序に指定されている列の数と長さが一致する値配列を入力として渡します。</span><span class="sxs-lookup"><span data-stu-id="49d22-115">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="49d22-116">1 つの列に基づく並べ替えの場合は、1 つの値を渡します。</span><span class="sxs-lookup"><span data-stu-id="49d22-116">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="49d22-117">複数列に基づく並べ替えの場合は、オブジェクトの配列を渡します。</span><span class="sxs-lookup"><span data-stu-id="49d22-117">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="49d22-118">複数の列の並べ替えでは、オブジェクト配列内の値が、**DataView** の **Sort** プロパティで指定されている列の順序と一致している必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="49d22-118">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="49d22-119">1 列の並べ替え順序が設定されている **DataView** に対して **Find** メソッドを呼び出すコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="49d22-119">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 <span data-ttu-id="49d22-120">**Sort** プロパティで複数の列が指定される場合は、次のコード サンプルに示すように、各列に対応する検索値を **Sort** プロパティで指定されている順序で格納したオブジェクト配列を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="49d22-120">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a><span data-ttu-id="49d22-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="49d22-121">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="49d22-122">DataViews</span><span class="sxs-lookup"><span data-stu-id="49d22-122">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="49d22-123">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="49d22-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
