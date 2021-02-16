---
description: '詳細情報: 方法:LINQ を使用して ArrayList を照会する (Visual Basic)'
title: '方法: LINQ を使用して ArrayList を照会する'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: df7c6e1cee6d8e37074ce209f3bea97a402d8dbe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428520"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="5467e-103">方法: LINQ を使用して ArrayList を照会する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5467e-103">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>

<span data-ttu-id="5467e-104">LINQ を使用して <xref:System.Collections.ArrayList> などの非ジェネリックの <xref:System.Collections.IEnumerable> コレクションをクエリする場合、範囲変数の型を明示的に宣言して、オブジェクトの特定の型をコレクションに反映させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5467e-104">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="5467e-105">たとえば、`Student` オブジェクトの <xref:System.Collections.ArrayList> がある場合、[From 句](../../../language-reference/queries/from-clause.md)は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5467e-105">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../language-reference/queries/from-clause.md) should look like this:</span></span>

```vb
Dim query = From student As Student In arrList
'...
```

<span data-ttu-id="5467e-106">範囲変数の型を指定することで、<xref:System.Collections.ArrayList> 内の各項目を `Student` にキャストします。</span><span class="sxs-lookup"><span data-stu-id="5467e-106">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>

<span data-ttu-id="5467e-107">明示的に型指定された範囲変数をクエリ式で使用すると、<xref:System.Linq.Enumerable.Cast%2A> メソッドを呼び出した場合と同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="5467e-107">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="5467e-108">指定したキャストを実行できない場合、<xref:System.Linq.Enumerable.Cast%2A> は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="5467e-108"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="5467e-109"><xref:System.Linq.Enumerable.Cast%2A> および <xref:System.Linq.Enumerable.OfType%2A> は、非ジェネリックの <xref:System.Collections.IEnumerable> 型で動作する、2 つの標準クエリ演算子メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5467e-109"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="5467e-110">Visual Basic では、データ ソースの <xref:System.Linq.Enumerable.Cast%2A> メソッドを明示的に呼び出して、特定の範囲変数の型を確保する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5467e-110">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="5467e-111">詳細については、「[クエリ操作での型の関係 (Visual Basic)](type-relationships-in-query-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5467e-111">For more information, see [Type Relationships in Query Operations (Visual Basic)](type-relationships-in-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="5467e-112">例</span><span class="sxs-lookup"><span data-stu-id="5467e-112">Example</span></span>

<span data-ttu-id="5467e-113">次の例では、<xref:System.Collections.ArrayList> に対して単純なクエリを実行しています。</span><span class="sxs-lookup"><span data-stu-id="5467e-113">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="5467e-114">この例では、コードが <xref:System.Collections.ArrayList.Add%2A> メソッドを呼び出すときにオブジェクト初期化子を使用していますが、これは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="5467e-114">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>

```vb
Imports System.Collections
Imports System.Linq

Module Module1

    Public Class Student
        Public Property FirstName As String
        Public Property LastName As String
        Public Property Scores As Integer()
    End Class

    Sub Main()

        Dim student1 As New Student With {.FirstName = "Svetlana",
                                     .LastName = "Omelchenko",
                                     .Scores = New Integer() {98, 92, 81, 60}}
        Dim student2 As New Student With {.FirstName = "Claire",
                                    .LastName = "O'Donnell",
                                    .Scores = New Integer() {75, 84, 91, 39}}
        Dim student3 As New Student With {.FirstName = "Cesar",
                                    .LastName = "Garcia",
                                    .Scores = New Integer() {97, 89, 85, 82}}
        Dim student4 As New Student With {.FirstName = "Sven",
                                    .LastName = "Mortensen",
                                    .Scores = New Integer() {88, 94, 65, 91}}

        Dim arrList As New ArrayList()
        arrList.Add(student1)
        arrList.Add(student2)
        arrList.Add(student3)
        arrList.Add(student4)

        ' Use an explicit type for non-generic collections
        Dim query = From student As Student In arrList
                    Where student.Scores(0) > 95
                    Select student

        For Each student As Student In query
            Console.WriteLine(student.LastName & ": " & student.Scores(0))
        Next
        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Module
' Output:
'   Omelchenko: 98
'   Garcia: 97
```

## <a name="see-also"></a><span data-ttu-id="5467e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5467e-115">See also</span></span>

- [<span data-ttu-id="5467e-116">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5467e-116">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
