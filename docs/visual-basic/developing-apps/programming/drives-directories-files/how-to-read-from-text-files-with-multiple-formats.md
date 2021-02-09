---
description: '詳細情報: 方法:Visual Basic で複数の書式を持つテキスト ファイルを読み取る'
title: 方法:複数の書式を持つテキスト ファイルを読み取る
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: 90d981ad051fb395d57604434cf9ba6b74603e7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797446"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="ddddf-103">方法:Visual Basic で複数の書式を持つテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="ddddf-103">How to: Read from fext files with multiple formats in Visual Basic</span></span>

<span data-ttu-id="ddddf-104"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> オブジェクトには、構造化されたテキスト ファイル (ログなど) を簡単にかつ効率的に解析する方法が備わっています。</span><span class="sxs-lookup"><span data-stu-id="ddddf-104">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="ddddf-105">`PeekChars` メソッドを使用して、ファイルを解析するときに各行の書式を判断すると、複数の書式を持つファイルを処理できます。</span><span class="sxs-lookup"><span data-stu-id="ddddf-105">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="ddddf-106">複数の書式を持つテキスト ファイルを解析するには</span><span class="sxs-lookup"><span data-stu-id="ddddf-106">To parse a text file with multiple formats</span></span>

1. <span data-ttu-id="ddddf-107">*testfile.txt* という名前のテキスト ファイルをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="ddddf-107">Add a text file named *testfile.txt* to your project.</span></span> <span data-ttu-id="ddddf-108">次の内容をテキスト ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="ddddf-108">Add the following content to the text file:</span></span>

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. <span data-ttu-id="ddddf-109">予期される形式と、エラーが報告されたときに使用される形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="ddddf-109">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="ddddf-110">各配列の最後のエントリは -1 です。そのため、最後のフィールドは可変幅であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="ddddf-110">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="ddddf-111">これは、配列の最後のエントリが 0 以下の場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="ddddf-111">This occurs when the last entry in the array is less than or equal to 0.</span></span>

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. <span data-ttu-id="ddddf-112">新しい <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> オブジェクトを作成し、幅と形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="ddddf-112">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. <span data-ttu-id="ddddf-113">各行をループし、読み取り前に書式を調べます。</span><span class="sxs-lookup"><span data-stu-id="ddddf-113">Loop through the rows, testing for format before reading.</span></span>

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. <span data-ttu-id="ddddf-114">エラーをコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ddddf-114">Write errors to the console.</span></span>

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a><span data-ttu-id="ddddf-115">例</span><span class="sxs-lookup"><span data-stu-id="ddddf-115">Example</span></span>

<span data-ttu-id="ddddf-116">この例では、`testfile.txt` ファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="ddddf-116">The following is the complete example that reads from the file `testfile.txt`:</span></span>

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a><span data-ttu-id="ddddf-117">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="ddddf-117">Robust programming</span></span>

<span data-ttu-id="ddddf-118">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ddddf-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ddddf-119">指定された形式で行を解析できない (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。</span><span class="sxs-lookup"><span data-stu-id="ddddf-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="ddddf-120">例外の原因となった行が例外メッセージで報告され、その行に含まれているテキストには <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> プロパティが代入されます。</span><span class="sxs-lookup"><span data-stu-id="ddddf-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>
- <span data-ttu-id="ddddf-121">指定されたファイルが存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="ddddf-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>
- <span data-ttu-id="ddddf-122">部分信頼の状況下で、ファイルにアクセスするために必要なアクセス許可がユーザーにない。</span><span class="sxs-lookup"><span data-stu-id="ddddf-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="ddddf-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ddddf-123">(<xref:System.Security.SecurityException>).</span></span>
- <span data-ttu-id="ddddf-124">パスが長すぎる (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="ddddf-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>
- <span data-ttu-id="ddddf-125">ファイルにアクセスする十分なアクセス許可がユーザーにない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="ddddf-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="ddddf-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddddf-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="ddddf-127">方法: コンマ区切りのテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="ddddf-127">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="ddddf-128">方法: 固定幅のテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="ddddf-128">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="ddddf-129">TextFieldParser オブジェクトによるテキスト ファイルの解析</span><span class="sxs-lookup"><span data-stu-id="ddddf-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
