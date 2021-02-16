---
description: '詳細情報: 方法:文字列での単語の出現回数をカウントする (LINQ) (Visual Basic)'
title: '方法: 文字列での単語の出現回数をカウントする (LINQ)'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: dd00d1840f8f4eacdf949b0c1200b26f3692e00d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464808"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="d1991-103">方法: 文字列での単語の出現回数をカウントする (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1991-103">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="d1991-104">この例では、LINQ クエリを使用して、指定された単語が文字列内に出現する回数をカウントする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d1991-104">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="d1991-105">カウントを実行するには、まず <xref:System.String.Split%2A> メソッドを呼び出して単語の配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="d1991-105">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="d1991-106"><xref:System.String.Split%2A> メソッドを呼び出すと、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="d1991-106">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="d1991-107">文字列に対する操作が単語のカウントのみである場合は、<xref:System.Text.RegularExpressions.Regex.Matches%2A> または <xref:System.String.IndexOf%2A> メソッドの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="d1991-107">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="d1991-108">ただし、パフォーマンスが重要でない場合や、他の種類のクエリを実行する目的で事前に文章を分割している場合は、LINQ を使用して単語や語句をカウントすることにも意味があります。</span><span class="sxs-lookup"><span data-stu-id="d1991-108">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>

## <a name="example"></a><span data-ttu-id="d1991-109">例</span><span class="sxs-lookup"><span data-stu-id="d1991-109">Example</span></span>

```vb
Class CountWords

    Shared Sub Main()

        Dim text As String = "Historically, the world of data and the world of objects" &
                  " have not been well integrated. Programmers work in C# or Visual Basic" &
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &
                  " them. Data types often require translation between the two worlds; there are" &
                  " different standard functions. Because the object world has no notion of query, a" &
                  " query can only be represented as a string without compile-time type checking or" &
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &
                  " objects in memory is often tedious and error-prone."

        Dim searchTerm As String = "data"

        ' Convert the string into an array of words.
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},
                                                 StringSplitOptions.RemoveEmptyEntries)

        ' Create and execute the query. It executes immediately
        ' because a singleton value is produced.
        ' Use ToLower to match "data" and "Data"
        Dim matchQuery = From word In dataSource
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()
                      Select word

        ' Count the matches.
        Dim count As Integer = matchQuery.Count()
        Console.WriteLine(count & " occurrence(s) of the search term """ &
                          searchTerm & """ were found.")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 3 occurrence(s) of the search term "data" were found.
```

## <a name="compile-the-code"></a><span data-ttu-id="d1991-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d1991-110">Compile the code</span></span>

<span data-ttu-id="d1991-111">System.Linq 名前空間の `Imports` ステートメントを使用して、Visual Basic コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1991-111">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1991-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1991-112">See also</span></span>

- [<span data-ttu-id="d1991-113">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1991-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
