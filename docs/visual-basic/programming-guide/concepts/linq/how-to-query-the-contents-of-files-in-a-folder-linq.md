---
description: '詳細情報: フォルダー内のファイルの内容を照会する方法 (LINQ) (Visual Basic)'
title: フォルダー内のファイルの内容を照会する方法 (LINQ)
ms.date: 07/20/2015
ms.assetid: edacbcd3-f3e4-4429-a8be-28a58dc0dd70
ms.openlocfilehash: 5043f64a0bb38811b6155394b18a88f702515cc5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434993"
---
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a><span data-ttu-id="486ad-103">フォルダー内のファイルの内容を照会する方法 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="486ad-103">How to query the contents of files in a folder (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="486ad-104">この例では、指定したディレクトリ ツリーに含まれるすべてのファイルを照会し、個々のファイルを開いて、その内容を調べています。</span><span class="sxs-lookup"><span data-stu-id="486ad-104">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="486ad-105">同様の手法を使えば、ディレクトリ ツリーの内容に対するインデックスや逆インデックスを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="486ad-105">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="486ad-106">この例で行っているのは単純な文字列検索です。</span><span class="sxs-lookup"><span data-stu-id="486ad-106">A simple string search is performed in this example.</span></span> <span data-ttu-id="486ad-107">しかし正規表現を使うと、もっと複雑なパターン マッチングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="486ad-107">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="486ad-108">詳細については、[LINQ クエリと正規表現を組み合わせる (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="486ad-108">For more information, see [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="486ad-109">例</span><span class="sxs-lookup"><span data-stu-id="486ad-109">Example</span></span>  
  
```vb
Imports System.IO

Module Module1  
    'QueryContents  
    Public Sub Main()  
  
        ' Modify this path as necessary.  
        Dim startFolder = "C:\Program Files (x86)\Microsoft Visual Studio 14.0"  

        ' Take a snapshot of the folder contents.
        Dim dir As New DirectoryInfo(startFolder)
        Dim fileList = dir.GetFiles("*.*", SearchOption.AllDirectories)

        Dim searchTerm = "Welcome"

        ' Search the contents of each file.
        ' A regular expression created with the RegEx class
        ' could be used instead of the Contains method.
        Dim queryMatchingFiles = From file In fileList _
                                 Where file.Extension = ".html" _
                                 Let fileText = GetFileText(file.FullName) _
                                 Where fileText.Contains(searchTerm) _
                                 Select file.FullName

        Console.WriteLine("The term " & searchTerm & " was found in:")

        ' Execute the query.
        For Each filename In queryMatchingFiles
            Console.WriteLine(filename)
        Next

        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit")
        Console.ReadKey()

    End Sub

    ' Read the contents of the file. This is done in a separate
    ' function in order to handle potential file system errors.
    Function GetFileText(name As String) As String

        ' If the file has been deleted, the right thing
        ' to do in this case is return an empty string.
        Dim fileContents = String.Empty

        ' If the file has been deleted since we took
        ' the snapshot, ignore it and return the empty string.
        If File.Exists(name) Then
            fileContents = File.ReadAllText(name)
        End If

        Return fileContents

    End Function
End Module
```

## <a name="compile-the-code"></a><span data-ttu-id="486ad-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="486ad-110">Compile the code</span></span>

<span data-ttu-id="486ad-111">Visual Basic のコンソール アプリケーション プロジェクトを作成し、コード サンプルをコピーして貼り付け、プロジェクトのプロパティでスタートアップ オブジェクトの値を調整します。</span><span class="sxs-lookup"><span data-stu-id="486ad-111">Create a Visual Basic console application project, copy and paste the code sample, and adjust the Startup object value in the project properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="486ad-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="486ad-112">See also</span></span>

- [<span data-ttu-id="486ad-113">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="486ad-113">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="486ad-114">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="486ad-114">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
