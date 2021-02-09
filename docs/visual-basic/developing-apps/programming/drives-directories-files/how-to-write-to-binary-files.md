---
description: '詳細情報: 方法:Visual Basic でバイナリ ファイルに書き込む'
title: '方法: バイナリ ファイルに書き込む'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: a1fe18c9143c26fd40e6a1d9cde36581c2c0be12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797329"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="120c8-103">方法 : Visual Basic でバイナリ ファイルに書き込む</span><span class="sxs-lookup"><span data-stu-id="120c8-103">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="120c8-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> メソッドは、バイナリ ファイルにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="120c8-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="120c8-105">`append` パラメーターが `True` の場合、データはファイルに追加されます。それ以外の場合は、ファイル内のデータが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="120c8-105">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="120c8-106">指定されたパスのファイル名を除く部分が有効でない場合は、<xref:System.IO.DirectoryNotFoundException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="120c8-106">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="120c8-107">パスが有効でもファイルが存在しない場合は、ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="120c8-107">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="120c8-108">バイナリ ファイルに書き込むには</span><span class="sxs-lookup"><span data-stu-id="120c8-108">To write to a binary file</span></span>

<span data-ttu-id="120c8-109">`WriteAllBytes` メソッドを使い、ファイルのパス、ファイルの名前、書き込むバイトを指定します。</span><span class="sxs-lookup"><span data-stu-id="120c8-109">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="120c8-110">この例では、データ配列 `CustomerData` を `CollectedData.dat` という名前のファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="120c8-110">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="120c8-111">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="120c8-111">Robust Programming</span></span>

<span data-ttu-id="120c8-112">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="120c8-112">The following conditions may create an exception:</span></span>

- <span data-ttu-id="120c8-113">文字列の長さが 0 である、空白文字だけが含まれる、または無効な文字が含まれるために、パスが無効である</span><span class="sxs-lookup"><span data-stu-id="120c8-113">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="120c8-114">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="120c8-114">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="120c8-115">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="120c8-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="120c8-116">`File` が、存在しないパスを指している (<xref:System.IO.FileNotFoundException> または <xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="120c8-116">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="120c8-117">他のプロセスがファイルを使用しているか、または I/O エラーが発生した (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="120c8-117">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="120c8-118">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="120c8-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="120c8-119">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="120c8-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="120c8-120">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="120c8-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="120c8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="120c8-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="120c8-122">方法: ファイルにテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="120c8-122">How to: Write Text to Files</span></span>](how-to-write-text-to-files.md)
