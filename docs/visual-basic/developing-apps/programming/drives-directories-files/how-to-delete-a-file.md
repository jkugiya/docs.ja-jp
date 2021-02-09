---
description: '詳細情報: 方法:Visual Basic でファイルを削除する'
title: '方法: ファイルを削除する'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 49bfe2e4a0d9114e2f653ae14dab303e35e2dfeb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797576"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="42a79-103">方法: Visual Basic でファイルを削除する</span><span class="sxs-lookup"><span data-stu-id="42a79-103">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="42a79-104">`My.Computer.FileSystem` オブジェクトの `DeleteFile` メソッドを使用すると、ファイルを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="42a79-104">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="42a79-105">削除したファイルを **ごみ箱** に送るかどうか、ファイルを削除することをユーザーに確認するかどうか、ユーザーが操作をキャンセルした場合の処理方法などが、オプションとして用意されています。</span><span class="sxs-lookup"><span data-stu-id="42a79-105">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="42a79-106">テキスト ファイルを削除するには</span><span class="sxs-lookup"><span data-stu-id="42a79-106">To delete a text file</span></span>  
  
- <span data-ttu-id="42a79-107">`DeleteFile` メソッドを使用してファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="42a79-107">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="42a79-108">次のコードは、`test.txt` という名前のファイルを削除する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="42a79-108">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="42a79-109">テキスト ファイルを削除して、ユーザーがファイルを削除することを確認するには</span><span class="sxs-lookup"><span data-stu-id="42a79-109">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="42a79-110">`showUI` を `AllDialogs` に設定し、`DeleteFile` メソッドを使用してファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="42a79-110">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="42a79-111">次のコードは、`test.txt` という名前のファイルを、ユーザーに削除するファイルを確認した上で削除する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="42a79-111">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="42a79-112">テキスト ファイルを削除してごみ箱に送るには</span><span class="sxs-lookup"><span data-stu-id="42a79-112">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="42a79-113">`recycle` パラメーターに `SendToRecycleBin` を指定し、`DeleteFile` メソッドを使用してファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="42a79-113">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="42a79-114">次のコードは、`test.txt` という名前のファイルを削除して **ごみ箱** に送る方法の例です。</span><span class="sxs-lookup"><span data-stu-id="42a79-114">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="42a79-115">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="42a79-115">Robust Programming</span></span>  

 <span data-ttu-id="42a79-116">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="42a79-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="42a79-117">次のいずれかの理由で、パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="42a79-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="42a79-118">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="42a79-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="42a79-119">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="42a79-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="42a79-120">パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="42a79-120">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="42a79-121">ファイルが使用中の場合 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="42a79-121">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="42a79-122">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="42a79-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="42a79-123">ファイルが存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="42a79-123">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="42a79-124">ファイルの削除に必要なアクセス許可がユーザーにないか、またはファイルが読み取り専用である (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="42a79-124">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="42a79-125">部分信頼の状況下で、必要なアクセス許可がユーザーにない (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="42a79-125">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="42a79-126">ユーザーが操作を取り消し、`onUserCancel` が `ThrowException` に設定されている (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="42a79-126">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a79-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="42a79-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="42a79-128">方法: ディレクトリにあるファイルのコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="42a79-128">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
