---
description: '詳細情報: 方法:ログ メッセージを書き込む (Visual Basic)'
title: '方法: ログ メッセージを書き込む'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: ed455fdb2cebda908981514bef932942adf499ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797303"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="a7eb5-103">方法: ログ メッセージを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7eb5-103">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="a7eb5-104">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーションに関する情報をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="a7eb5-104">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="a7eb5-105">この例では、 `My.Application.Log.WriteEntry` メソッドを使用してトレース情報をログに記録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a7eb5-105">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="a7eb5-106">例外情報をログに記録するには、`My.Application.Log.WriteException` メソッドを使います。方法については、「[方法 : 例外をログに記録する](how-to-log-exceptions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a7eb5-106">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="a7eb5-107">例</span><span class="sxs-lookup"><span data-stu-id="a7eb5-107">Example</span></span>

<span data-ttu-id="a7eb5-108">この例では、 `My.Application.Log.WriteEntry` メソッドを使用してトレース情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a7eb5-108">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="a7eb5-109">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="a7eb5-109">.NET Framework Security</span></span>

<span data-ttu-id="a7eb5-110">ログに書き込むデータに、ユーザーのパスワードなどの機密情報が含まれないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7eb5-110">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="a7eb5-111">詳しくは、「[アプリケーション ログの使用](working-with-application-logs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a7eb5-111">For more information, see [Working with Application Logs](working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7eb5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7eb5-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="a7eb5-113">アプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="a7eb5-113">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="a7eb5-114">方法: 例外をログに記録する</span><span class="sxs-lookup"><span data-stu-id="a7eb5-114">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="a7eb5-115">チュートリアル : My.Application.Log による情報の書き込み先の確認</span><span class="sxs-lookup"><span data-stu-id="a7eb5-115">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="a7eb5-116">チュートリアル : My.Application.Log による情報の書き込み先の変更</span><span class="sxs-lookup"><span data-stu-id="a7eb5-116">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="a7eb5-117">チュートリアル: My.Application.Log の出力をフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="a7eb5-117">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)
