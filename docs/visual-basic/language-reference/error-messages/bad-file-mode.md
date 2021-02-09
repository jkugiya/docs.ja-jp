---
description: '詳細情報: ファイル モードが正しくありません。'
title: ファイル モードが正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: da792407fb37f5c206be7ff39da14d314ef1e2d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797082"
---
# <a name="bad-file-mode"></a><span data-ttu-id="9f944-103">ファイル モードが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="9f944-103">Bad file mode</span></span>

<span data-ttu-id="9f944-104">ファイルの内容を操作するために使用されるステートメントは、ファイルが開かれたモードに適している必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f944-104">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="9f944-105">以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="9f944-105">Possible causes include:</span></span>  
  
- <span data-ttu-id="9f944-106">`FilePutObject` または `FileGetObject` ステートメントがシーケンシャル ファイルを指定しています。</span><span class="sxs-lookup"><span data-stu-id="9f944-106">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="9f944-107">`Print` ステートメントが、`Output` または `Append` 以外のアクセス モード用に開かれたファイルを指定しています。</span><span class="sxs-lookup"><span data-stu-id="9f944-107">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="9f944-108">`Input` ステートメントが、`Input` 以外のアクセス モードで開かれたファイルを指定しています</span><span class="sxs-lookup"><span data-stu-id="9f944-108">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="9f944-109">読み取り専用ファイルに書き込もうとしました。</span><span class="sxs-lookup"><span data-stu-id="9f944-109">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9f944-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9f944-110">To correct this error</span></span>  
  
- <span data-ttu-id="9f944-111">`FilePutObject` および `FileGetObject` が、`Random` または `Binary` アクセス用に開かれたファイルのみを参照していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9f944-111">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="9f944-112">`Print` が `Output` または `Append` アクセス モードのいずれかで開かれているファイルを指定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9f944-112">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="9f944-113">そうでない場合は、別のステートメントを使用してファイルにデータを格納するか、適切なモードでファイルを再度開きます。</span><span class="sxs-lookup"><span data-stu-id="9f944-113">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="9f944-114">`Input` が `Input` で開かれているファイルを指定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9f944-114">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="9f944-115">そうでない場合は、別のステートメントを使用してファイルにデータを格納するか、適切なモードでファイルを再度開きます。</span><span class="sxs-lookup"><span data-stu-id="9f944-115">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="9f944-116">読み取り専用ファイルに書き込む場合は、ファイルの読み取り/書き込みの状態を変更するか、ファイルへの書き込みを試みないようにします。</span><span class="sxs-lookup"><span data-stu-id="9f944-116">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="9f944-117">`My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="9f944-117">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f944-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f944-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="9f944-119">トラブルシューティング : テキスト ファイルの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="9f944-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
