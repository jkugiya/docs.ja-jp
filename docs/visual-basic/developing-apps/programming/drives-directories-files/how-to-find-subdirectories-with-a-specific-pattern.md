---
description: '詳細情報: 方法:特定のパターンに一致するサブディレクトリを検索する (Visual Basic)'
title: '方法: 特定のパターンに一致するサブディレクトリを検索する'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: aaf1fe0e844c6a3db2b011289613a80dbd1b43fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797550"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="03aa8-103">方法: 特定のパターンに一致するサブディレクトリを検索する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03aa8-103">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="03aa8-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> メソッドは、ディレクトリのサブディレクトリのパス名を表す文字列の読み取り専用のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="03aa8-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="03aa8-105">`wildCards` パラメーターを使用して、特定のパターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="03aa8-105">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="03aa8-106">サブディレクトリの内容を検索対象に含めるには、`searchType` パラメーターを `SearchOption.SearchAllSubDirectories` に設定します。</span><span class="sxs-lookup"><span data-stu-id="03aa8-106">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>

<span data-ttu-id="03aa8-107">指定したパターンに一致するディレクトリが見つからなかった場合は、空のコレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="03aa8-107">An empty collection is returned if no directories matching the specified pattern are found.</span></span>

## <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="03aa8-108">特定のパターンに一致するサブディレクトリを検索するには</span><span class="sxs-lookup"><span data-stu-id="03aa8-108">To find subdirectories with a specific pattern</span></span>

<span data-ttu-id="03aa8-109">検索するディレクトリの名前およびパスを指定して、`GetDirectories` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="03aa8-109">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="03aa8-110">次の例では、ディレクトリ構造内で名前に "Logs" という単語を含むすべてのディレクトリが返され、`ListBox1` に追加されます。</span><span class="sxs-lookup"><span data-stu-id="03aa8-110">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="03aa8-111">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="03aa8-111">Robust Programming</span></span>

<span data-ttu-id="03aa8-112">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="03aa8-112">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="03aa8-113">次のいずれかの理由で、パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="03aa8-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="03aa8-114">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="03aa8-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="03aa8-115">指定したワイルドカード文字の中に 1 つ以上の `Nothing`、空の文字列が含まれている、または空白のみである (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="03aa8-115">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="03aa8-116">`directory` が存在しない (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="03aa8-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="03aa8-117">`directory` が既存のファイルを指している (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="03aa8-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="03aa8-118">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="03aa8-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="03aa8-119">パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="03aa8-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="03aa8-120">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="03aa8-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="03aa8-121">ユーザーに必要な権限がない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="03aa8-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="03aa8-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="03aa8-122">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="03aa8-123">方法: 特定のパターンに一致するファイルを検索する</span><span class="sxs-lookup"><span data-stu-id="03aa8-123">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
