---
description: '詳細情報: 方法:Visual Basic でファイルをアップロードする'
title: '方法: ファイルをアップロードする'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: d38820cda6a143cf3f06bf6a2ca72cba5a9f3aef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675404"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="6280c-103">方法: Visual Basic でファイルをアップロードする</span><span class="sxs-lookup"><span data-stu-id="6280c-103">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="6280c-104"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> メソッドを利用してファイルをアップロードし、離れた場所に格納できます。</span><span class="sxs-lookup"><span data-stu-id="6280c-104">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="6280c-105">`ShowUI` パラメーターを `True` に設定した場合、アップロードの進行状況を示すダイアログ ボックスが表示され、ユーザーが操作をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="6280c-105">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="6280c-106">ファイルをアップロードするには</span><span class="sxs-lookup"><span data-stu-id="6280c-106">To upload a file</span></span>  
  
- <span data-ttu-id="6280c-107">`UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、およびアップロード先のディレクトリの場所を表す文字列または URI (Uniform Resource Identifier) を指定します。この例では、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="6280c-107">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="6280c-108">操作の進行状況を表示しながらファイルをアップロードするには</span><span class="sxs-lookup"><span data-stu-id="6280c-108">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="6280c-109">`UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、およびアップロード先のディレクトリの場所を表す文字列または URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="6280c-109">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="6280c-110">この例では、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。ユーザー名やパスワードは指定せず、アップロードの進行状況を表示し、タイムアウト間隔は 500 ミリ秒に設定しています。</span><span class="sxs-lookup"><span data-stu-id="6280c-110">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="6280c-111">ユーザー名とパスワードを指定してファイルをアップロードするには</span><span class="sxs-lookup"><span data-stu-id="6280c-111">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="6280c-112">`UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、アップロード先のディレクトリの場所を表す文字列または URI、およびユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="6280c-112">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="6280c-113">この例では、ユーザー名に `anonymous` を、パスワードに空白を指定して、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="6280c-113">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6280c-114">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="6280c-114">Robust Programming</span></span>  

 <span data-ttu-id="6280c-115">次の条件を満たす場合は、例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6280c-115">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="6280c-116">ローカル ファイル パスが有効ではありません (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="6280c-116">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="6280c-117">認証に失敗しました (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="6280c-117">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="6280c-118">接続がタイムアウトしました (<xref:System.TimeoutException>)。</span><span class="sxs-lookup"><span data-stu-id="6280c-118">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6280c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="6280c-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="6280c-120">方法: ファイルをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="6280c-120">How to: Download a File</span></span>](how-to-download-a-file.md)
- [<span data-ttu-id="6280c-121">方法: ファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="6280c-121">How to: Parse File Paths</span></span>](../drives-directories-files/how-to-parse-file-paths.md)
