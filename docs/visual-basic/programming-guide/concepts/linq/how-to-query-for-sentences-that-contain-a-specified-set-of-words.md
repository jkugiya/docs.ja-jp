---
description: '詳細情報: 方法:指定された単語のセットを含む文章を照会する (LINQ) (Visual Basic)'
title: '方法: 指定された単語のセットを含む文章を照会する (LINQ)'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: b6d2f428e499b8b22fa5bc13015f2405430c1bbd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435097"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a><span data-ttu-id="87994-103">方法: 指定された単語のセットを含む文章を照会する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87994-103">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="87994-104">この例は、指定された一連の単語と一致する文言を含む文をテキスト ファイルから検索する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="87994-104">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="87994-105">この例では検索語句の配列をハードコーディングしていますが、実行時に動的に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="87994-105">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="87994-106">この例のクエリを実行すると、"Historically"、"data"、"integrated" という単語をすべて含んだ文が返されます。</span><span class="sxs-lookup"><span data-stu-id="87994-106">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>

## <a name="example"></a><span data-ttu-id="87994-107">例</span><span class="sxs-lookup"><span data-stu-id="87994-107">Example</span></span>

```vb
Class FindSentences

    Shared Sub Main()
        Dim text As String = "Historically, the world of data and the world of objects " &
        "have not been well integrated. Programmers work in C# or Visual Basic " &
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &
        "are tables, columns, rows, nodes, and separate languages for dealing with " &
        "them. Data types often require translation between the two worlds; there are " &
        "different standard functions. Because the object world has no notion of query, a " &
        "query can only be represented as a string without compile-time type checking or " &
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &
        "objects in memory is often tedious and error-prone."

        ' Split the text block into an array of sentences.
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})

        ' Define the search terms. This list could also be dynamically populated at runtime
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}

        ' Find sentences that contain all the terms in the wordsToMatch array
        ' Note that the number of terms to match is not specified at compile time
        Dim sentenceQuery = From sentence In sentences
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},
                                                   StringSplitOptions.RemoveEmptyEntries)
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()
                            Select sentence

        ' Execute the query
        For Each str As String In sentenceQuery
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Class
' Output:
' Historically, the world of data and the world of objects have not been well integrated
```

<span data-ttu-id="87994-108">このクエリではまず、テキストを文単位に分割し、個々の単語を保持する文字列の配列に分割しています。</span><span class="sxs-lookup"><span data-stu-id="87994-108">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="87994-109">その各配列について、重複する単語を <xref:System.Linq.Enumerable.Distinct%2A> メソッドですべて削除したうえで、それらの単語の配列と `wordsToMatch` 配列との <xref:System.Linq.Enumerable.Intersect%2A> 演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="87994-109">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="87994-110">共通部分のカウントと `wordsToMatch` 配列のカウントとが一致した場合、文を構成する単語内にすべての検索語句が見つかったものとして判断され、該当する文が返されます。</span><span class="sxs-lookup"><span data-stu-id="87994-110">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>

<span data-ttu-id="87994-111">句読点を文字列から削除するために、<xref:System.String.Split%2A> の呼び出しでは句読点を区切り記号として使用しています。</span><span class="sxs-lookup"><span data-stu-id="87994-111">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="87994-112">この処理がないと、たとえば "Historically," という文字列があった場合に、`wordsToMatch` 配列内の "Historically" と一致しません。</span><span class="sxs-lookup"><span data-stu-id="87994-112">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="87994-113">ソース テキストに使われている句読点の種類によっては、別の区切り記号を使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="87994-113">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="87994-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="87994-114">Compile the code</span></span>

<span data-ttu-id="87994-115">System.Linq 名前空間の `Imports` ステートメントを使用して、Visual Basic コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="87994-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="87994-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="87994-116">See also</span></span>

- [<span data-ttu-id="87994-117">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87994-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
