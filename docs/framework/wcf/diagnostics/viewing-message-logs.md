---
description: '詳細情報: メッセージログの表示'
title: メッセージ ログを参照する
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: c640b2c3793839be4a31123701865fa944eaebc8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99758035"
---
# <a name="viewing-message-logs"></a><span data-ttu-id="f8012-103">メッセージ ログを参照する</span><span class="sxs-lookup"><span data-stu-id="f8012-103">Viewing Message Logs</span></span>

<span data-ttu-id="f8012-104">ここでは、メッセージ ログの表示方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8012-104">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="f8012-105">サービス トレース ビューアーでのメッセージ ログの表示</span><span class="sxs-lookup"><span data-stu-id="f8012-105">Viewing Message Logs in the Service Trace Viewer</span></span>  

 <span data-ttu-id="f8012-106">メッセージは、WCF によって処理されるときに変換されます。</span><span class="sxs-lookup"><span data-stu-id="f8012-106">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="f8012-107">そのため、ログ記録されたメッセージは、ログ記録された時点でのメッセージの内容を反映しているにすぎず、ネットワーク上での内容ではありません。</span><span class="sxs-lookup"><span data-stu-id="f8012-107">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="f8012-108">メッセージ ログの出力はメッセージの転送形式とは関係がないため、メッセージ ログは常にデコードされたメッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="f8012-108">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="f8012-109">メッセージ ログが適切に設定されていれば、すべてのログ メッセージはプレーンテキストになります。</span><span class="sxs-lookup"><span data-stu-id="f8012-109">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="f8012-110">たとえば、ログ メッセージの形式 (プレーンテキスト) は、バイナリ メッセージ エンコーダーの使用には影響されません。</span><span class="sxs-lookup"><span data-stu-id="f8012-110">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="f8012-111">XmlWriterTraceListener の出力は、一連の XML フラグメントを含んだファイルです。</span><span class="sxs-lookup"><span data-stu-id="f8012-111">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="f8012-112">このファイルは有効な XML ファイルではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f8012-112">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="f8012-113">メッセージログファイルを表示するには、 [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f8012-113">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="f8012-114">このツールの使用方法の詳細については、「 [サービストレースビューアーを使用した相関トレースの表示とトラブルシューティング](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8012-114">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="f8012-115">サービストレースビューアーでは、メッセージは [ **メッセージ** ] タブに一覧表示されます。エラーの重大度によっては、処理エラーが発生したメッセージ、またはに関連するメッセージが、黄色 (警告レベル) または赤色 (エラーレベル) で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8012-115">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="f8012-116">メッセージをダブルクリックすると、要求の処理のコンテキストに従ってメッセージ トレースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8012-116">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8012-117">メッセージにヘッダーがない場合は、`<header/>` タグがログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="f8012-117">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="f8012-118">クライアント、中継、およびサービスによって記録されたメッセージの表示</span><span class="sxs-lookup"><span data-stu-id="f8012-118">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  

 <span data-ttu-id="f8012-119">環境には、クライアント、クライアントからメッセージが送信される中継、中継からさらにメッセージが転送されるサービスが含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="f8012-119">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="f8012-120">3つのすべての場所でメッセージログが有効になっていて、3つのメッセージログがすべて [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) で同時に表示されている場合、メッセージログの交換は誤って表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8012-120">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="f8012-121">これは、メッセージ ヘッダーの `CorrelationId` と `ActivityId` が、すべての送受信ペアで一意にならなくなるためです。</span><span class="sxs-lookup"><span data-stu-id="f8012-121">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="f8012-122">この問題を解決するには、次のいずれかの方法に従います。</span><span class="sxs-lookup"><span data-stu-id="f8012-122">You can use either one of the following methods to resolve this problem.</span></span>  
  
- <span data-ttu-id="f8012-123">[サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)の3つのメッセージログのうち、常に2つだけを表示します。</span><span class="sxs-lookup"><span data-stu-id="f8012-123">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
- <span data-ttu-id="f8012-124">[サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)の3つのログをすべて同時に表示する必要がある場合は、新しいインスタンスを作成してリレーサービスを変更でき <xref:System.ServiceModel.Channels.Message> ます。</span><span class="sxs-lookup"><span data-stu-id="f8012-124">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="f8012-125">このインスタンスは、受信メッセージの本文のコピーであり、また、`ActivityId` ヘッダーおよび `Action` ヘッダーを除くすべてのヘッダーのコピーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="f8012-125">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="f8012-126">これを実行する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="f8012-126">The following example code demonstrates how to do this.</span></span>  
  
```csharp
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="f8012-127">メッセージ ログ内容が不正確になる例外的なケース</span><span class="sxs-lookup"><span data-stu-id="f8012-127">Exceptional Cases for Inaccurate Message Logging Content</span></span>  

 <span data-ttu-id="f8012-128">次の条件では、ログ記録されたメッセージがネットワーク上にあるオクテット ストリームの正確な表現とはならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f8012-128">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
- <span data-ttu-id="f8012-129">BasicHttpBinding の場合、エンベロープ ヘッダーは /addressing/none 名前空間の受信メッセージについてログ記録されます。</span><span class="sxs-lookup"><span data-stu-id="f8012-129">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
- <span data-ttu-id="f8012-130">空白は一致しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f8012-130">White spaces can be mismatched.</span></span>  
  
- <span data-ttu-id="f8012-131">受信メッセージの場合、空の要素が異なる表現になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f8012-131">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="f8012-132">たとえば、 \<tag> \</tag> の代わりに\<tag/></span><span class="sxs-lookup"><span data-stu-id="f8012-132">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
- <span data-ttu-id="f8012-133">既知の PII ログ記録が、既定または enableLoggingKnownPii="true" という明示的な設定で、無効になっている場合。</span><span class="sxs-lookup"><span data-stu-id="f8012-133">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
- <span data-ttu-id="f8012-134">UTF-8 へ変換するためのエンコードが有効な場合。</span><span class="sxs-lookup"><span data-stu-id="f8012-134">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8012-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8012-135">See also</span></span>

- [<span data-ttu-id="f8012-136">サービス トレース ビューアー ツール (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="f8012-136">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [<span data-ttu-id="f8012-137">サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f8012-137">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="f8012-138">メッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="f8012-138">Message Logging</span></span>](message-logging.md)
