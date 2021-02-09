---
description: '詳細情報: 方法:Visual Basic でファイルをダウンロードする'
title: '方法: ファイルをダウンロードする'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: dd296a5958431b74ccc8e0fb41a49073f4847ded
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797693"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="8d835-103">方法 : Visual Basic でファイルをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="8d835-103">How to: Download a File in Visual Basic</span></span>

<span data-ttu-id="8d835-104"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> メソッドを使用すると、リモート ファイルをダウンロードして、指定した場所へ保存できます。</span><span class="sxs-lookup"><span data-stu-id="8d835-104">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="8d835-105">`ShowUI` パラメーターを `True` に設定した場合、ダウンロードの進行状況を示すダイアログ ボックスが表示されます。ユーザーは、このダイアログ ボックスで操作をキャンセルすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8d835-105">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="8d835-106">既定では、同じ名前を持つ既存のファイルは上書きされません。既存のファイルを上書きするには、`overwrite` パラメーターを `True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="8d835-106">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>

<span data-ttu-id="8d835-107">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8d835-107">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="8d835-108">ドライブ名が有効ではない (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="8d835-108">Drive name is not valid (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="8d835-109">必要な認証が付与されていない (<xref:System.UnauthorizedAccessException> または <xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="8d835-109">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="8d835-110">指定した `connectionTimeout` 内にサーバーが応答しない (<xref:System.TimeoutException>)。</span><span class="sxs-lookup"><span data-stu-id="8d835-110">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>

- <span data-ttu-id="8d835-111">要求が Web サイトにより拒否された (<xref:System.Net.WebException>)。</span><span class="sxs-lookup"><span data-stu-id="8d835-111">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> <span data-ttu-id="8d835-112">ファイル名からファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="8d835-112">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="8d835-113">たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="8d835-113">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="8d835-114">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="8d835-114">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="8d835-115">ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8d835-115">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

### <a name="to-download-a-file"></a><span data-ttu-id="8d835-116">ファイルをダウンロードするには</span><span class="sxs-lookup"><span data-stu-id="8d835-116">To download a file</span></span>

- <span data-ttu-id="8d835-117">`DownloadFile` メソッドを使用してファイルをダウンロードします。その際、ターゲット ファイルの場所を表す文字列または URI と、ファイルを格納する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="8d835-117">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="8d835-118">この例では、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードし、`C:\Documents and Settings\All Users\Documents` に保存します。</span><span class="sxs-lookup"><span data-stu-id="8d835-118">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="8d835-119">タイムアウト間隔を指定して、ファイルをダウンロードには</span><span class="sxs-lookup"><span data-stu-id="8d835-119">To download a file, specifying a time-out interval</span></span>

- <span data-ttu-id="8d835-120">`DownloadFile` メソッドを使用してファイルをダウンロードします。その際、ターゲット ファイルの場所を表す文字列または URI、ファイルを格納する場所、およびタイムアウト間隔 (ミリ秒単位、既定値は 1000) を指定します。</span><span class="sxs-lookup"><span data-stu-id="8d835-120">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="8d835-121">この例では、タイムアウト間隔に 500 ミリ秒を指定し、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードして、`C:\Documents and Settings\All Users\Documents` に保存します。</span><span class="sxs-lookup"><span data-stu-id="8d835-121">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="8d835-122">ユーザー名とパスワードを指定して、ファイルをダウンロードするには</span><span class="sxs-lookup"><span data-stu-id="8d835-122">To download a file, supplying a user name and password</span></span>

- <span data-ttu-id="8d835-123">`DownLoadFile` メソッドを使用してファイルをダウンロードします。その際、ターゲット ファイルの場所を表す文字列または URI、ファイルを格納する場所、ユーザー名、およびパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="8d835-123">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="8d835-124">この例では、ユーザー名に `anonymous` を、パスワードに空白を指定し、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードして、`C:\Documents and Settings\All Users\Documents` に保存します。</span><span class="sxs-lookup"><span data-stu-id="8d835-124">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > <span data-ttu-id="8d835-125">`DownLoadFile` メソッドで使用される FTP プロトコルは、パスワードを含む情報をプレーンテキストで送信するため、重要な情報の送信には使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="8d835-125">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d835-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d835-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="8d835-127">方法: ファイルをアップロードする</span><span class="sxs-lookup"><span data-stu-id="8d835-127">How to: Upload a File</span></span>](how-to-upload-a-file.md)
- [<span data-ttu-id="8d835-128">方法: ファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="8d835-128">How to: Parse File Paths</span></span>](../drives-directories-files/how-to-parse-file-paths.md)
