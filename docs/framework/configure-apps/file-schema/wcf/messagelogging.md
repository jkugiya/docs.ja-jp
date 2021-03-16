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

この要素は Windows Communication Foundation (WCF) のメッセージ ログ機能の設定を定義します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`logEntireMessage`|メッセージ全体 (メッセージ ヘッダーと本文) を記録するかどうかを指定するブール値。 既定は `false` で、メッセージ ヘッダーだけが記録されます。 この設定は、すべてのメッセージ ログ レベル (サービス、トランスポート、および不正) に影響を与えます。|  
|`logMalformedMessages`|無効なメッセージを記録するかどうかを指定するブール値。 無効なメッセージは、`maxMessagesToLog` にカウントされません。 既定では、 `false`です。|  
|`logMessagesAtServiceLevel`|(暗号化およびトランスポートに関連する変換の前に) メッセージをサービス レベルでトレースするかどうかを指定するブール値。 既定では、 `false`です。|  
|`logMessagesAtTransportLevel`|メッセージをトランスポート レベルでトレースするかどうかを指定するブール値。 構成ファイルに指定されたフィルターが適用され、フィルターに一致するメッセージだけがトレースされます。 既定では、 `false`です。|  
|`maxMessagesToLog`|記録するメッセージの最大数を指定する正の整数。 既定値は 1000 です。|  
|`maxSizeOfMessageToLog`|記録するメッセージの最大サイズ (バイト単位) を指定する正の整数。 サイズが制限より大きなメッセージは、記録されません。 この設定は、すべてのトレース レベルに影響を与えます。 既定値は 262144 (0x4000) です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|filters|`filters` 要素には、XPath フィルターのコレクションが保持されます。 トランスポート メッセージ ログが有効な場合 (`logMessagesAtTransportLevel` が `true`)、フィルターに一致するメッセージだけが記録されます。<br /><br /> フィルターは、トランスポート層でのみ適用されます。 サービス レベルおよび形式が正しくないメッセージ ログ記録は、フィルターの影響を受けません。<br /><br /> この要素の唯一の属性である `filter` は、XpathFilter です。<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|診断|管理者が行うランタイムの検査と管理の WCF 設定を定義します。|  
  
## <a name="remarks"></a>解説  

 メッセージは、サービス、トランスポート、および不正の 3 種類のレベルで記録されます。 各レベルは、個別にアクティブにできます。  
  
 XPath フィルターは、トランスポート レベルとサービス レベルで特定のメッセージを記録するために追加できます。 フィルターが定義されていない場合、すべてのメッセージが記録されます。 フィルターは、メッセージのヘッダーにのみ適用されます。 本文は無視されます。 WCF は、パフォーマンスを強化するためにメッセージ本文を無視します。 本文の内容に基づいてフィルターを適用する場合は、そのためのフィルターを備えたカスタム リスナーを作成できます。  
  
 メッセージ トレースをアクティブ化するために、トレース リスナーを作成する必要があります。 リスナー自体には、<xref:System.Diagnostics> トレース アーキテクチャで動作するリスナーを指定できます。 次の例は、そのようなリスナーの作成方法を示します。  
  
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
  
## <a name="example"></a>例  
  
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
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [メッセージ ログの構成](../../../wcf/diagnostics/configuring-message-logging.md)
