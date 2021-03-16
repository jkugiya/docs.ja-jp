---
description: '詳細情報: <messageLogging>'
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: e26a616bb7974a8fbad9a7f920a28e06422e09c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749286"
---
# \<messageLogging>

<span data-ttu-id="b92c5-102">この要素は Windows Communication Foundation (WCF) のメッセージ ログ機能の設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="b92c5-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**  
  
## <a name="syntax"></a><span data-ttu-id="b92c5-103">構文</span><span class="sxs-lookup"><span data-stu-id="b92c5-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b92c5-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b92c5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b92c5-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b92c5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b92c5-106">属性</span><span class="sxs-lookup"><span data-stu-id="b92c5-106">Attributes</span></span>  
  
|<span data-ttu-id="b92c5-107">属性</span><span class="sxs-lookup"><span data-stu-id="b92c5-107">Attribute</span></span>|<span data-ttu-id="b92c5-108">説明</span><span class="sxs-lookup"><span data-stu-id="b92c5-108">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="b92c5-109">メッセージ全体 (メッセージ ヘッダーと本文) を記録するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="b92c5-109">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="b92c5-110">既定は `false` で、メッセージ ヘッダーだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-110">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="b92c5-111">この設定は、すべてのメッセージ ログ レベル (サービス、トランスポート、および不正) に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-111">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="b92c5-112">無効なメッセージを記録するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="b92c5-112">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="b92c5-113">無効なメッセージは、`maxMessagesToLog` にカウントされません。</span><span class="sxs-lookup"><span data-stu-id="b92c5-113">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="b92c5-114">既定では、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="b92c5-114">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="b92c5-115">(暗号化およびトランスポートに関連する変換の前に) メッセージをサービス レベルでトレースするかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="b92c5-115">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="b92c5-116">既定では、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="b92c5-116">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="b92c5-117">メッセージをトランスポート レベルでトレースするかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="b92c5-117">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="b92c5-118">構成ファイルに指定されたフィルターが適用され、フィルターに一致するメッセージだけがトレースされます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-118">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="b92c5-119">既定では、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="b92c5-119">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="b92c5-120">記録するメッセージの最大数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="b92c5-120">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="b92c5-121">既定値は 1000 です。</span><span class="sxs-lookup"><span data-stu-id="b92c5-121">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="b92c5-122">記録するメッセージの最大サイズ (バイト単位) を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="b92c5-122">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="b92c5-123">サイズが制限より大きなメッセージは、記録されません。</span><span class="sxs-lookup"><span data-stu-id="b92c5-123">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="b92c5-124">この設定は、すべてのトレース レベルに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-124">This setting affects all trace levels.</span></span> <span data-ttu-id="b92c5-125">既定値は 262144 (0x4000) です。</span><span class="sxs-lookup"><span data-stu-id="b92c5-125">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b92c5-126">子要素</span><span class="sxs-lookup"><span data-stu-id="b92c5-126">Child Elements</span></span>  
  
|<span data-ttu-id="b92c5-127">要素</span><span class="sxs-lookup"><span data-stu-id="b92c5-127">Element</span></span>|<span data-ttu-id="b92c5-128">説明</span><span class="sxs-lookup"><span data-stu-id="b92c5-128">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b92c5-129">filters</span><span class="sxs-lookup"><span data-stu-id="b92c5-129">filters</span></span>|<span data-ttu-id="b92c5-130">`filters` 要素には、XPath フィルターのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-130">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="b92c5-131">トランスポート メッセージ ログが有効な場合 (`logMessagesAtTransportLevel` が `true`)、フィルターに一致するメッセージだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-131">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="b92c5-132">フィルターは、トランスポート層でのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-132">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="b92c5-133">サービス レベルおよび形式が正しくないメッセージ ログ記録は、フィルターの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="b92c5-133">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="b92c5-134">この要素の唯一の属性である `filter` は、XpathFilter です。</span><span class="sxs-lookup"><span data-stu-id="b92c5-134">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="b92c5-135">親要素</span><span class="sxs-lookup"><span data-stu-id="b92c5-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b92c5-136">要素</span><span class="sxs-lookup"><span data-stu-id="b92c5-136">Element</span></span>|<span data-ttu-id="b92c5-137">説明</span><span class="sxs-lookup"><span data-stu-id="b92c5-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b92c5-138">診断</span><span class="sxs-lookup"><span data-stu-id="b92c5-138">diagnostics</span></span>|<span data-ttu-id="b92c5-139">管理者が行うランタイムの検査と管理の WCF 設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="b92c5-139">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b92c5-140">解説</span><span class="sxs-lookup"><span data-stu-id="b92c5-140">Remarks</span></span>  

 <span data-ttu-id="b92c5-141">メッセージは、サービス、トランスポート、および不正の 3 種類のレベルで記録されます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-141">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="b92c5-142">各レベルは、個別にアクティブにできます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-142">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="b92c5-143">XPath フィルターは、トランスポート レベルとサービス レベルで特定のメッセージを記録するために追加できます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-143">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="b92c5-144">フィルターが定義されていない場合、すべてのメッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-144">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="b92c5-145">フィルターは、メッセージのヘッダーにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-145">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="b92c5-146">本文は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-146">The body is ignored.</span></span> <span data-ttu-id="b92c5-147">WCF は、パフォーマンスを強化するためにメッセージ本文を無視します。</span><span class="sxs-lookup"><span data-stu-id="b92c5-147">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="b92c5-148">本文の内容に基づいてフィルターを適用する場合は、そのためのフィルターを備えたカスタム リスナーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-148">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="b92c5-149">メッセージ トレースをアクティブ化するために、トレース リスナーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b92c5-149">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="b92c5-150">リスナー自体には、<xref:System.Diagnostics> トレース アーキテクチャで動作するリスナーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b92c5-150">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="b92c5-151">次の例は、そのようなリスナーの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b92c5-151">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a><span data-ttu-id="b92c5-152">例</span><span class="sxs-lookup"><span data-stu-id="b92c5-152">Example</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="42"
                maxSizeOfMessageToLog="42">
  <filters>
    <clear />
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="b92c5-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="b92c5-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="b92c5-154">メッセージ ログの構成</span><span class="sxs-lookup"><span data-stu-id="b92c5-154">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
