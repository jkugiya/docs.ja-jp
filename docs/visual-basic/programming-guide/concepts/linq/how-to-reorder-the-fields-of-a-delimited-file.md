---
description: '詳細情報: 方法:区切りファイルのフィールドの順序を変更する (LINQ) (Visual Basic)'
title: '方法: 区切り記号入りファイルのフィールドの順序を変更する (LINQ)'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: bfb06c396dbe33628ea146622c9c4ebe9534aae4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435006"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a><span data-ttu-id="7fa5a-103">方法: 区切りファイルのフィールドの順序を変更する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fa5a-103">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="7fa5a-104">コンマ区切り (CSV) ファイルは、テキスト ファイルです。多くの場合、行と列で表されるスプレッドシート データや他の表形式データの格納に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7fa5a-104">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="7fa5a-105"><xref:System.String.Split%2A> メソッドを使用してフィールドを区切ると、LINQ を使用した CSV ファイルのクエリと操作がとても簡単になります。</span><span class="sxs-lookup"><span data-stu-id="7fa5a-105">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="7fa5a-106">この手法は、CSV ファイルに限らず、行が構造化されているテキストの一部を並べ替えるときに利用できます。</span><span class="sxs-lookup"><span data-stu-id="7fa5a-106">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>

<span data-ttu-id="7fa5a-107">次の例では、学生の "名"、"姓"、"ID" を表す 3 つの列があります。</span><span class="sxs-lookup"><span data-stu-id="7fa5a-107">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="7fa5a-108">これらのフィールドは、学生の姓に基づいてアルファベット順に並べられています。</span><span class="sxs-lookup"><span data-stu-id="7fa5a-108">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="7fa5a-109">クエリによって、ID 列が最初に表示され、学生の姓と名を結合して 2 列目に表示されるように列順を変えます。</span><span class="sxs-lookup"><span data-stu-id="7fa5a-109">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="7fa5a-110">行は ID フィールドの順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="7fa5a-110">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="7fa5a-111">結果は新しいファイルに保存され、元のデータは変更されません。</span><span class="sxs-lookup"><span data-stu-id="7fa5a-111">The results are saved into a new file and the original data is not modified.</span></span>

### <a name="to-create-the-data-file"></a><span data-ttu-id="7fa5a-112">データ ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="7fa5a-112">To create the data file</span></span>

1. <span data-ttu-id="7fa5a-113">次の行を、spreadsheet1.csv というプレーン テキスト ファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7fa5a-113">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="7fa5a-114">プロジェクト フォルダーにファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="7fa5a-114">Save the file in your project folder.</span></span>

    ```csv
    Adams,Terry,120
    Fakhouri,Fadi,116
    Feng,Hanying,117
    Garcia,Cesar,114
    Garcia,Debra,115
    Garcia,Hugo,118
    Mortensen,Sven,113
    O'Donnell,Claire,112
    Omelchenko,Svetlana,111
    Tucker,Lance,119
    Tucker,Michael,122
    Zabokritski,Eugene,121
    ```

## <a name="example"></a><span data-ttu-id="7fa5a-115">例</span><span class="sxs-lookup"><span data-stu-id="7fa5a-115">Example</span></span>

```vb
Class CSVFiles

    Shared Sub Main()

        ' Create the IEnumerable data source.
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")

        ' Execute the query. Put field 2 first, then
        ' reverse and combine fields 0 and 1 from the old field
        Dim lineQuery = From line In lines
                        Let x = line.Split(New Char() {","})
                        Order By x(2)
                        Select x(2) & ", " & (x(1) & " " & x(0))

        ' Execute the query and write out the new file. Note that WriteAllLines
        ' takes a string array, so ToArray is called on the query.
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())

        ' Keep console window open in debug mode.
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output to spreadsheet2.csv:
' 111, Svetlana Omelchenko
' 112, Claire O'Donnell
' 113, Sven Mortensen
' 114, Cesar Garcia
' 115, Debra Garcia
' 116, Fadi Fakhouri
' 117, Hanying Feng
' 118, Hugo Garcia
' 119, Lance Tucker
' 120, Terry Adams
' 121, Eugene Zabokritski
' 122, Michael Tucker
```

## <a name="see-also"></a><span data-ttu-id="7fa5a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fa5a-116">See also</span></span>

- [<span data-ttu-id="7fa5a-117">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fa5a-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="7fa5a-118">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fa5a-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
- [<span data-ttu-id="7fa5a-119">方法: CSV ファイルから XML を生成する</span><span class="sxs-lookup"><span data-stu-id="7fa5a-119">How to: Generate XML from CSV Files</span></span>](../../../../standard/linq/generate-xml-csv-files.md)
