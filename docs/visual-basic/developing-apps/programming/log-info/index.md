---
description: '詳細情報: アプリケーションからの情報のログ記録 (Visual Basic)'
title: アプリケーションからの情報のログ記録
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: 6e0adf45c12d98c8bc6d177d85accf9bee347f75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775072"
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="02552-103">アプリケーションからの情報のログ記録 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02552-103">Logging Information from the Application (Visual Basic)</span></span>

<span data-ttu-id="02552-104">このセクションには、`My.Application.Log` オブジェクトまたは `My.Log` オブジェクトを使ってアプリケーションの情報を記録する方法と、アプリケーションのログ機能を拡張する方法に関するトピックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="02552-104">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="02552-105">`Log` オブジェクトはアプリケーションのログ リスナーに情報を書き込むためのメソッドを提供し、`Log` オブジェクトの高度な `TraceSource` プロパティは詳細な構成情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="02552-105">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="02552-106">`Log` オブジェクトは、アプリケーションの構成ファイルによって構成されます。</span><span class="sxs-lookup"><span data-stu-id="02552-106">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="02552-107">`My.Log` オブジェクトは、ASP.NET アプリケーションでのみ使うことができます。</span><span class="sxs-lookup"><span data-stu-id="02552-107">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="02552-108">クライアント アプリケーションの場合は `My.Application.Log` を使います。</span><span class="sxs-lookup"><span data-stu-id="02552-108">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="02552-109">詳細については、「<xref:Microsoft.VisualBasic.Logging.Log>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02552-109">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="02552-110">タスク</span><span class="sxs-lookup"><span data-stu-id="02552-110">Tasks</span></span>  
  
|<span data-ttu-id="02552-111">終了</span><span class="sxs-lookup"><span data-stu-id="02552-111">To</span></span>|<span data-ttu-id="02552-112">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="02552-112">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="02552-113">イベントの情報をアプリケーションのログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="02552-113">Write event information to the application's logs.</span></span>|[<span data-ttu-id="02552-114">方法: ログ メッセージを書き込む</span><span class="sxs-lookup"><span data-stu-id="02552-114">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)|  
|<span data-ttu-id="02552-115">例外の情報をアプリケーションのログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="02552-115">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="02552-116">方法: 例外をログに記録する</span><span class="sxs-lookup"><span data-stu-id="02552-116">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)|  
|<span data-ttu-id="02552-117">アプリケーションの起動時または終了時に、トレース情報をアプリケーションのログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="02552-117">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="02552-118">方法: アプリケーションの起動時または終了時にメッセージをログに記録する</span><span class="sxs-lookup"><span data-stu-id="02552-118">How to: Log Messages When the Application Starts or Shuts Down</span></span>](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="02552-119">テキスト ファイルに情報を書き込むように `My.Application.Log` を構成します。</span><span class="sxs-lookup"><span data-stu-id="02552-119">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="02552-120">方法: イベント情報をテキスト ファイルに書き込む</span><span class="sxs-lookup"><span data-stu-id="02552-120">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="02552-121">イベント ログに情報を書き込むように `My.Application.Log` を構成します。</span><span class="sxs-lookup"><span data-stu-id="02552-121">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="02552-122">方法: アプリケーション イベント ログに書き込む</span><span class="sxs-lookup"><span data-stu-id="02552-122">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="02552-123">`My.Application.Log` が情報を書き込む場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="02552-123">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="02552-124">チュートリアル: My.Application.Log による情報の書き込み先の変更</span><span class="sxs-lookup"><span data-stu-id="02552-124">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="02552-125">`My.Application.Log` が情報を書き込む場所を取得します。</span><span class="sxs-lookup"><span data-stu-id="02552-125">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="02552-126">チュートリアル: My.Application.Log による情報の書き込み先の確認</span><span class="sxs-lookup"><span data-stu-id="02552-126">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="02552-127">`My.Application.Log` のカスタム ログ リスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="02552-127">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="02552-128">チュートリアル: カスタム ログ リスナーの作成</span><span class="sxs-lookup"><span data-stu-id="02552-128">Walkthrough: Creating Custom Log Listeners</span></span>](walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="02552-129">`My.Application.Log` ログの出力をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="02552-129">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="02552-130">チュートリアル: My.Application.Log の出力をフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="02552-130">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="02552-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="02552-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="02552-132">アプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="02552-132">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="02552-133">トラブルシューティング : ログ リスナー</span><span class="sxs-lookup"><span data-stu-id="02552-133">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)
