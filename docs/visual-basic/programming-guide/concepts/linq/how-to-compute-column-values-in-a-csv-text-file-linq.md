---
description: '詳細情報: 方法:CSV テキスト ファイルの列値を計算する (LINQ) (Visual Basic)'
title: '方法: CSV テキスト ファイルの列値を計算する (LINQ)'
ms.date: 07/20/2015
ms.assetid: 88b2b9f3-c82e-41f3-b1b4-26ede5973a02
ms.openlocfilehash: f2bed49cf69d812659aae0cee398a735b3b42dbe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100484185"
---
# <a name="how-to-compute-column-values-in-a-csv-text-file-linq-visual-basic"></a><span data-ttu-id="85d09-103">方法: CSV テキスト ファイルの列値を計算する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85d09-103">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="85d09-104">この例では、合計、平均、最小、最大などの集計計算を .csv ファイルの列に対して実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85d09-104">This example shows how to perform aggregate computations such as Sum, Average, Min, and Max on the columns of a .csv file.</span></span> <span data-ttu-id="85d09-105">ここで説明する例の原則は、他の種類の構造化テキストにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="85d09-105">The example principles that are shown here can be applied to other types of structured text.</span></span>

### <a name="to-create-the-source-file"></a><span data-ttu-id="85d09-106">ソース ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="85d09-106">To create the source file</span></span>

1. <span data-ttu-id="85d09-107">次の行を scores.csv という名前のファイルにコピーし、プロジェクト フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="85d09-107">Copy the following lines into a file that is named scores.csv and save it in your project folder.</span></span> <span data-ttu-id="85d09-108">最初の列は学生 ID、それに続く列は 4 つの試験の点数を表していると仮定します。</span><span class="sxs-lookup"><span data-stu-id="85d09-108">Assume that the first column represents a student ID, and subsequent columns represent scores from four exams.</span></span>

    ```csv
    111, 97, 92, 81, 60
    112, 75, 84, 91, 39
    113, 88, 94, 65, 91
    114, 97, 89, 85, 82
    115, 35, 72, 91, 70
    116, 99, 86, 90, 94
    117, 93, 92, 80, 87
    118, 92, 90, 83, 78
    119, 68, 79, 88, 92
    120, 99, 82, 81, 79
    121, 96, 85, 91, 60
    122, 94, 92, 91, 91
    ```

## <a name="example"></a><span data-ttu-id="85d09-109">例</span><span class="sxs-lookup"><span data-stu-id="85d09-109">Example</span></span>

```vb
Class SumColumns

    Public Shared Sub Main()

        Dim lines As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' Specifies the column to compute
        ' This value could be passed in at runtime.
        Dim exam = 3

        ' Spreadsheet format:
        ' Student ID    Exam#1  Exam#2  Exam#3  Exam#4
        ' 111,          97,     92,     81,     60
        ' one is added to skip over the first column
        ' which holds the student ID.
        SumColumn(lines, exam + 1)
        Console.WriteLine()
        MultiColumns(lines)

        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit...")
        Console.ReadKey()

    End Sub

    Shared Sub SumColumn(ByVal lines As IEnumerable(Of String), ByVal col As Integer)

        ' This query performs two steps:
        ' split the string into a string array
        ' convert the specified element to
        ' integer and select it.
        Dim columnQuery = From line In lines
                           Let x = line.Split(",")
                           Select Convert.ToInt32(x(col))

        ' Execute and cache the results for performance.
        ' Only needed with very large files.
        Dim results = columnQuery.ToList()

        ' Perform aggregate calculations
        ' on the column specified by col.
        Dim avgScore = Aggregate score In results Into Average(score)
        Dim minScore = Aggregate score In results Into Min(score)
        Dim maxScore = Aggregate score In results Into Max(score)

        Console.WriteLine("Single Column Query:")
        Console.WriteLine("Exam #{0}: Average:{1:##.##} High Score:{2} Low Score:{3}",
                     col, avgScore, maxScore, minScore)

    End Sub

    Shared Sub MultiColumns(ByVal lines As IEnumerable(Of String))

        Console.WriteLine("Multi Column Query:")

        ' Create the query. It will produce nested sequences.
        ' multiColQuery performs these steps:
        ' 1) convert the string to a string array
        ' 2) skip over the "Student ID" column and take the rest
        ' 3) convert each field to an int and select that
        '    entire sequence as one row in the results.
        Dim multiColQuery = From line In lines
                            Let fields = line.Split(",")
                            Select From str In fields Skip 1
                                        Select Convert.ToInt32(str)

        Dim results = multiColQuery.ToList()

        ' Find out how many columns we have.
        Dim columnCount = results(0).Count()

        ' Perform aggregate calculations on each column.
        ' One loop for each score column in scores.
        ' We can use a for loop because we have already
        ' executed the multiColQuery in the call to ToList.

        For j As Integer = 0 To columnCount - 1
            Dim column = j
            Dim res2 = From row In results
                       Select row.ElementAt(column)

            ' Perform aggregate calculations
            ' on the column specified by col.
            Dim avgScore = Aggregate score In res2 Into Average(score)
            Dim minScore = Aggregate score In res2 Into Min(score)
            Dim maxScore = Aggregate score In res2 Into Max(score)

            ' Add 1 to column numbers because exams in this course start with #1
            Console.WriteLine("Exam #{0} Average: {1:##.##} High Score: {2} Low Score: {3}",
                              column + 1, avgScore, maxScore, minScore)

        Next
    End Sub

End Class
' Output:
' Single Column Query:
' Exam #4: Average:76.92 High Score:94 Low Score:39

' Multi Column Query:
' Exam #1 Average: 86.08 High Score: 99 Low Score: 35
' Exam #2 Average: 86.42 High Score: 94 Low Score: 72
' Exam #3 Average: 84.75 High Score: 91 Low Score: 65
' Exam #4 Average: 76.92 High Score: 94 Low Score: 39
```

<span data-ttu-id="85d09-110">このクエリでは、<xref:System.String.Split%2A> メソッドを使用してテキストの各行が配列に変換されます。</span><span class="sxs-lookup"><span data-stu-id="85d09-110">The query works by using the <xref:System.String.Split%2A> method to convert each line of text into an array.</span></span> <span data-ttu-id="85d09-111">各配列要素が列を表します。</span><span class="sxs-lookup"><span data-stu-id="85d09-111">Each array element represents a column.</span></span> <span data-ttu-id="85d09-112">最終的に、各列のテキストが数値表記に変換されます。</span><span class="sxs-lookup"><span data-stu-id="85d09-112">Finally, the text in each column is converted to its numeric representation.</span></span> <span data-ttu-id="85d09-113">ファイルがタブ区切りファイルの場合、`Split` メソッドの引数を `\t` に変更します。</span><span class="sxs-lookup"><span data-stu-id="85d09-113">If your file is a tab-separated file, just update the argument in the `Split` method to `\t`.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="85d09-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="85d09-114">Compile the code</span></span>

<span data-ttu-id="85d09-115">System.Linq 名前空間の `Imports` ステートメントを使用して、Visual Basic コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="85d09-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="85d09-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="85d09-116">See also</span></span>

- [<span data-ttu-id="85d09-117">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85d09-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="85d09-118">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85d09-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
