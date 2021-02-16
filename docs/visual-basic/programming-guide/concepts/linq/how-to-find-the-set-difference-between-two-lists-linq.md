---
description: '詳細情報: 方法:2 つのリストの差集合を見つける (LINQ) (Visual Basic)'
title: '方法: 2 つのリストの差集合を見つける (LINQ)'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: c877be03c3ff82d4be4814035a6401385d907e60
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483691"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a><span data-ttu-id="3156e-103">方法: 2 つのリストの差集合を見つける (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3156e-103">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="3156e-104">この例では、LINQ を使用して、2 つの文字列リストを比較し、names2.txt ではなく names1.txt でそれらの行を出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3156e-104">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="3156e-105">データ ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="3156e-105">To create the data files</span></span>  
  
1. <span data-ttu-id="3156e-106">「[方法:文字列コレクションを結合および比較する (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)」に示されているように、ソリューション フォルダーに names1.txt と names2.txt をコピーします。</span><span class="sxs-lookup"><span data-stu-id="3156e-106">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3156e-107">例</span><span class="sxs-lookup"><span data-stu-id="3156e-107">Example</span></span>  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 <span data-ttu-id="3156e-108"><xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Union%2A>、および <xref:System.Linq.Enumerable.Concat%2A> など、Visual Basic のいくつかの種類のクエリ操作は、メソッドベースの構文でのみ表すことができます。</span><span class="sxs-lookup"><span data-stu-id="3156e-108">Some types of query operations in Visual Basic, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="3156e-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="3156e-109">Compile the code</span></span>  

<span data-ttu-id="3156e-110">System.Linq 名前空間の `Imports` ステートメントを使用して、Visual Basic コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3156e-110">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3156e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3156e-111">See also</span></span>

- [<span data-ttu-id="3156e-112">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3156e-112">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
