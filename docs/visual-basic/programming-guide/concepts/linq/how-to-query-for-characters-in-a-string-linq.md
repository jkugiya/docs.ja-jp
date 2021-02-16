---
description: '詳細情報: 方法:文字列内の文字を照会する (LINQ) (Visual Basic)'
title: '方法: 文字列内の文字をクエリする (LINQ)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: bd8fabc06e88c83ae4e89079378ad67efb13c446
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425751"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="0b269-103">方法: 文字列内の文字を照会する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b269-103">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="0b269-104"><xref:System.String> クラスはジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装しているため、任意の文字列を文字のシーケンスとしてクエリできます。</span><span class="sxs-lookup"><span data-stu-id="0b269-104">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="0b269-105">ただし、これは LINQ の一般的な使用方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="0b269-105">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="0b269-106">複雑なパターン一致操作には、<xref:System.Text.RegularExpressions.Regex> クラスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="0b269-106">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>

## <a name="example"></a><span data-ttu-id="0b269-107">例</span><span class="sxs-lookup"><span data-stu-id="0b269-107">Example</span></span>

<span data-ttu-id="0b269-108">次の例では、文字列を対象にクエリを実行して、その文字列に含まれる数字の数を特定します。</span><span class="sxs-lookup"><span data-stu-id="0b269-108">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="0b269-109">クエリは、最初に使用された後も "再利用" されます。</span><span class="sxs-lookup"><span data-stu-id="0b269-109">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="0b269-110">これができるのは、クエリ自体には実際の結果が格納されないためです。</span><span class="sxs-lookup"><span data-stu-id="0b269-110">This is possible because the query itself does not store any actual results.</span></span>

```vb
Class QueryAString

    Shared Sub Main()

        ' A string is an IEnumerable data source.
        Dim aString As String = "ABCDE99F-J74-12-89A"

        ' Select only those characters that are numbers
        Dim stringQuery = From ch In aString
                          Where Char.IsDigit(ch)
                          Select ch
        ' Execute the query
        For Each c As Char In stringQuery
            Console.Write(c & " ")
        Next

        ' Call the Count method on the existing query.
        Dim count As Integer = stringQuery.Count()
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)

        ' Select all characters before the first '-'
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")

        ' Execute the second query
        For Each ch In stringQuery2
            Console.Write(ch)
        Next

        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 9 9 7 4 1 2 8 9
' Count = 8
' ABCDE99F
```

## <a name="compile-the-code"></a><span data-ttu-id="0b269-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0b269-111">Compile the code</span></span>

<span data-ttu-id="0b269-112">System.Linq 名前空間の `Imports` ステートメントを使用して、Visual Basic コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0b269-112">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b269-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b269-113">See also</span></span>

- [<span data-ttu-id="0b269-114">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b269-114">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="0b269-115">LINQ クエリと正規表現を組み合わせる方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b269-115">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)
