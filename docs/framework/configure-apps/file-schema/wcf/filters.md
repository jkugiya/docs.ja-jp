---
description: '詳細情報: <filters>'
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: c66dd07c91e78d1ae6e10790014c3d1b25e5538d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664601"
---
# \<filters>

<span data-ttu-id="22cef-102">`filters` 要素は、ログに記録されるメッセージの種類の制御に使用される XPath フィルターのコレクションを保持します。</span><span class="sxs-lookup"><span data-stu-id="22cef-102">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="22cef-103">フィルターは、`logMessagesAtTransportLevel` を `true` に設定することによって指定されるトランスポート層でのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="22cef-103">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="22cef-104">サービス レベルおよび形式が正しくないメッセージ ログ記録は、フィルターの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="22cef-104">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="22cef-105">コレクションにフィルターを追加するには、`add` を使用します。</span><span class="sxs-lookup"><span data-stu-id="22cef-105">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="22cef-106">1 つ以上のフィルターを定義した場合は、少なくとも 1 つのフィルターと一致するメッセージだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="22cef-106">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="22cef-107">フィルターを定義しなかった場合は、すべてのメッセージが通過します。</span><span class="sxs-lookup"><span data-stu-id="22cef-107">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="22cef-108">フィルターは、完全な XPath 構文をサポートし、構成ファイルでの出現順に適用されます。</span><span class="sxs-lookup"><span data-stu-id="22cef-108">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="22cef-109">フィルターが構文的に正しくない場合は、構成例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="22cef-109">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="22cef-110">SOAP ヘッダー セクションがあるメッセージだけを記録するフィルターの設定方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="22cef-110">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="22cef-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="22cef-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="22cef-112">メッセージ ログの構成</span><span class="sxs-lookup"><span data-stu-id="22cef-112">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
