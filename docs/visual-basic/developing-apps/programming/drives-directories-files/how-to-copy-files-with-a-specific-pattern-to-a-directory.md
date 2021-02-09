---
description: '詳細情報: 方法:Visual Basic で特定のパターンを持つファイルをディレクトリにコピーする'
title: '方法: 特定のパターンを持つファイルをディレクトリにコピーする'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 2a5163e6420d747a724fec9b8ede8dbcc6a938be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797628"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="6bcfb-103">方法 : Visual Basic で特定のパターンを持つファイルをディレクトリにコピーする</span><span class="sxs-lookup"><span data-stu-id="6bcfb-103">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>

<span data-ttu-id="6bcfb-104"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> メソッドは、ファイルのパス名を表す文字列の読み取り専用のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-104">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="6bcfb-105">`wildCards` パラメーターを使用して、特定のパターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-105">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="6bcfb-106">一致するファイルが見つからない場合は、空のコレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-106">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="6bcfb-107"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> メソッドを使用して、ファイルをディレクトリにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-107">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="6bcfb-108">特定のパターンを持つファイルをディレクトリにコピーするには</span><span class="sxs-lookup"><span data-stu-id="6bcfb-108">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="6bcfb-109">`GetFiles` メソッドを使用して、ファイルの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-109">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="6bcfb-110">この例は、指定したディレクトリ内のすべての .rtf ファイルを返します。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-110">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="6bcfb-111">`CopyFile` メソッドを使用して、ファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-111">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="6bcfb-112">この例では、 `testdirectory`という名前のディレクトリにファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-112">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="6bcfb-113">`For` ステートメントを `Next` ステートメントで閉じます。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-113">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="6bcfb-114">例</span><span class="sxs-lookup"><span data-stu-id="6bcfb-114">Example</span></span>  

 <span data-ttu-id="6bcfb-115">次の例は、上記のスニペットを完全な形で示したもので、指定したディレクトリのすべての .rtf ファイルを `testdirectory`という名前のディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-115">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="6bcfb-116">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="6bcfb-116">.NET Framework Security</span></span>  

 <span data-ttu-id="6bcfb-117">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6bcfb-118">次のいずれかの理由で、パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="6bcfb-119">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="6bcfb-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="6bcfb-120">ディレクトリが存在しない (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-120">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="6bcfb-121">ディレクトリが既存のファイルを指している (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-121">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="6bcfb-122">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="6bcfb-123">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="6bcfb-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="6bcfb-124">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="6bcfb-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="6bcfb-125">ユーザーに必要な権限がない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="6bcfb-125">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bcfb-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bcfb-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="6bcfb-127">方法: 特定のパターンに一致するサブディレクトリを検索する</span><span class="sxs-lookup"><span data-stu-id="6bcfb-127">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="6bcfb-128">トラブルシューティング : テキスト ファイルの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="6bcfb-128">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="6bcfb-129">方法: ディレクトリにあるファイルのコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="6bcfb-129">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
