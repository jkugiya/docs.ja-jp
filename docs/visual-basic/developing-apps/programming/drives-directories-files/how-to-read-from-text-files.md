---
description: '詳細情報: 方法:テキスト ファイルからデータを読み取る (Visual Basic)'
title: '方法: テキスト ファイルからデータを読み取る'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 76f8bbbb7a0064818d324fc6dd9f1f37f7271401
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797433"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="474c7-103">方法: テキスト ファイルからデータを読み取る (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="474c7-103">How to: Read From Text Files in Visual Basic</span></span>

<span data-ttu-id="474c7-104"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> オブジェクトの `My.Computer.FileSystem` メソッドを使用すると、テキスト ファイルを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="474c7-104">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="474c7-105">ファイルの内容が ASCII や UTF-8 などのエンコーディングを使用している場合、ファイル エンコーディングを指定できます。</span><span class="sxs-lookup"><span data-stu-id="474c7-105">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>

<span data-ttu-id="474c7-106">読み取るファイルで拡張文字が使用されている場合、ファイル エンコーディングを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="474c7-106">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>

> [!NOTE]
> <span data-ttu-id="474c7-107">ファイルから 1 回に 1 行のテキストを読み取るには、<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> オブジェクトの `My.Computer.FileSystem` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="474c7-107">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="474c7-108">`OpenTextFileReader` メソッドが <xref:System.IO.StreamReader> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="474c7-108">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="474c7-109"><xref:System.IO.StreamReader.ReadLine%2A> オブジェクトの `StreamReader` メソッドを使用して、ファイルから 1 回に 1 行を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="474c7-109">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="474c7-110"><xref:System.IO.StreamReader.EndOfStream%2A> オブジェクトの `StreamReader` メソッドを使用して、ファイルの最後かどうかをテストできます。</span><span class="sxs-lookup"><span data-stu-id="474c7-110">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>

## <a name="to-read-from-a-text-file"></a><span data-ttu-id="474c7-111">テキスト ファイルを読み取るには</span><span class="sxs-lookup"><span data-stu-id="474c7-111">To read from a text file</span></span>

<span data-ttu-id="474c7-112">`ReadAllText` オブジェクトの `My.Computer.FileSystem` メソッドを使用して、ファイルのパスを指定し、テキスト ファイルの内容を文字列に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="474c7-112">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="474c7-113">次の例は、test.txt の内容を文字列に読み取り、メッセージ ボックスに表示します。</span><span class="sxs-lookup"><span data-stu-id="474c7-113">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="474c7-114">エンコードされているテキスト ファイルを読み取るには</span><span class="sxs-lookup"><span data-stu-id="474c7-114">To read from a text file that is encoded</span></span>

<span data-ttu-id="474c7-115">`ReadAllText` オブジェクトの `My.Computer.FileSystem` メソッドを使用して、ファイルのパスとファイル エンコードの種類を指定し、テキスト ファイルの内容を文字列に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="474c7-115">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="474c7-116">次の例は、UTF32 ファイルである test.txt の内容を文字列に読み取り、メッセージ ボックスに表示します。</span><span class="sxs-lookup"><span data-stu-id="474c7-116">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a><span data-ttu-id="474c7-117">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="474c7-117">Robust Programming</span></span>

<span data-ttu-id="474c7-118">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="474c7-118">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="474c7-119">パスが無効である場合。1) 長さが 0 の文字列である、2) 空白だけが含まれている、3) 無効な文字が含まれている、4) デバイス パスである、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="474c7-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="474c7-120">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="474c7-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="474c7-121">ファイルが存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="474c7-121">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>

- <span data-ttu-id="474c7-122">他のプロセスがファイルを使用しているか、または I/O エラーが発生した (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="474c7-122">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="474c7-123">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="474c7-123">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="474c7-124">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="474c7-124">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="474c7-125">文字列をバッファーに書き込むための十分なメモリがない (<xref:System.OutOfMemoryException>)</span><span class="sxs-lookup"><span data-stu-id="474c7-125">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>

- <span data-ttu-id="474c7-126">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="474c7-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

<span data-ttu-id="474c7-127">ファイル名からファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="474c7-127">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="474c7-128">たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="474c7-128">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>

<span data-ttu-id="474c7-129">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="474c7-129">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="474c7-130">ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="474c7-130">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

## <a name="see-also"></a><span data-ttu-id="474c7-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="474c7-131">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [<span data-ttu-id="474c7-132">ファイルの読み取り</span><span class="sxs-lookup"><span data-stu-id="474c7-132">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="474c7-133">方法: コンマ区切りのテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="474c7-133">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="474c7-134">方法: 固定幅のテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="474c7-134">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="474c7-135">方法: 複数の書式を持つテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="474c7-135">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="474c7-136">トラブルシューティング : テキスト ファイルの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="474c7-136">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="474c7-137">チュートリアル: Visual Basic によるファイルとディレクトリの操作</span><span class="sxs-lookup"><span data-stu-id="474c7-137">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="474c7-138">ファイル エンコーディング</span><span class="sxs-lookup"><span data-stu-id="474c7-138">File Encodings</span></span>](file-encodings.md)
