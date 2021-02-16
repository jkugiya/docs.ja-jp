---
description: '詳細情報: データのグループ化 (Visual Basic)'
title: データのグループ化
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: fa6dbcc22c7d991d48775c3974cfc529840ef933
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469800"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="9a972-103">データのグループ化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a972-103">Grouping Data (Visual Basic)</span></span>

<span data-ttu-id="9a972-104">グループ化とは、各グループの要素が共通の属性を持つようにデータをグループに分ける操作を指します。</span><span class="sxs-lookup"><span data-stu-id="9a972-104">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="9a972-105">次の図は、文字のシーケンスをグループ化した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="9a972-105">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="9a972-106">各グループのキーは文字です。</span><span class="sxs-lookup"><span data-stu-id="9a972-106">The key for each group is the character.</span></span>  
  
 ![LINQ グループ化操作を示す図。](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="9a972-108">次のセクションでは、データ要素をグループ化する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="9a972-108">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a972-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="9a972-109">Methods</span></span>  
  
|<span data-ttu-id="9a972-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="9a972-110">Method Name</span></span>|<span data-ttu-id="9a972-111">説明</span><span class="sxs-lookup"><span data-stu-id="9a972-111">Description</span></span>|<span data-ttu-id="9a972-112">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="9a972-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="9a972-113">説明</span><span class="sxs-lookup"><span data-stu-id="9a972-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="9a972-114">GroupBy</span><span class="sxs-lookup"><span data-stu-id="9a972-114">GroupBy</span></span>|<span data-ttu-id="9a972-115">共通の属性を共有する要素をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="9a972-115">Groups elements that share a common attribute.</span></span> <span data-ttu-id="9a972-116">各グループは <xref:System.Linq.IGrouping%602> オブジェクトによって表されます。</span><span class="sxs-lookup"><span data-stu-id="9a972-116">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9a972-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="9a972-117">ToLookup</span></span>|<span data-ttu-id="9a972-118">キー セレクター関数に基づいて、<xref:System.Linq.Lookup%602> (一対多の辞書) に要素を挿入します。</span><span class="sxs-lookup"><span data-stu-id="9a972-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="9a972-119">該当なし。</span><span class="sxs-lookup"><span data-stu-id="9a972-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="9a972-120">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="9a972-120">Query Expression Syntax Example</span></span>  

 <span data-ttu-id="9a972-121">次のコード例では、`Group By` 句を使用して、偶数か奇数かによってリスト内の整数をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="9a972-121">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a972-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a972-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9a972-123">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a972-123">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="9a972-124">Group By 句</span><span class="sxs-lookup"><span data-stu-id="9a972-124">Group By Clause</span></span>](../../../language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="9a972-125">方法: 拡張機能でファイルをグループ化する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a972-125">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="9a972-126">方法: グループを使用してファイルを複数のファイルに分割する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a972-126">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
