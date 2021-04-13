---
title: トレースとメッセージ ログの推奨設定
description: WCF のさまざまな動作環境に対して推奨されるトレースとメッセージ ログの設定について説明します。
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: b23298b8ee95b3bcd61a3712e9ff91acf6a6a3e9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240096"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="b2d0b-103">トレースとメッセージ ログの推奨設定</span><span class="sxs-lookup"><span data-stu-id="b2d0b-103">Recommended Settings for Tracing and Message Logging</span></span>

<span data-ttu-id="b2d0b-104">このトピックでは、さまざまな動作環境における、推奨されるトレースとメッセージ ログの設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-104">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="b2d0b-105">本運用環境での推奨される設定</span><span class="sxs-lookup"><span data-stu-id="b2d0b-105">Recommended Settings for a Production Environment</span></span>  

 <span data-ttu-id="b2d0b-106">本運用環境で WCF トレース ソースを使用する場合は、`switchValue` を Warning に設定します。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-106">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="b2d0b-107">WCF `System.ServiceModel` トレース ソースを使用する場合は、`switchValue` 属性を `Warning` に設定し、`propagateActivity` 属性を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-107">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="b2d0b-108">ユーザー定義のトレース ソースを使用する場合は、`switchValue` 属性を `Warning, ActivityTracing` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-108">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="b2d0b-109">これは、[構成エディター ツール (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md) を使用して手動で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-109">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="b2d0b-110">前述のすべての場合において、パフォーマンスに影響しないと思われる場合は、`switchValue` 属性を `Information` に設定できます。これにより、相当な量のトレース データが生成されます。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-110">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="b2d0b-111">次の例に、これらの推奨設定を示します。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-111">The following example demonstrates these recommended settings.</span></span>  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="b2d0b-112">展開またはデバッグでの推奨される設定</span><span class="sxs-lookup"><span data-stu-id="b2d0b-112">Recommended Settings for Deployment or Debugging</span></span>  

 <span data-ttu-id="b2d0b-113">展開またはデバッグ環境では、`Information` または `Verbose` を選択すると共に、ユーザー定義のトレース ソースまたは `ActivityTracing` トレース ソースの場合は `System.ServiceModel` を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-113">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="b2d0b-114">また、デバッグ機能を向上させるには、トレース ソース (`System.ServiceModel.MessageLogging`) を構成に追加してメッセージ ログを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-114">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="b2d0b-115">`switchValue` 属性はこのトレース ソースに影響しません。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-115">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="b2d0b-116">次の例に、`XmlWriterTraceListener` を利用した共有リスナーを使用する推奨設定を示します。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-116">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging
           logEntireMessage="true"
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="b2d0b-117">WMI を使用した設定変更</span><span class="sxs-lookup"><span data-stu-id="b2d0b-117">Using WMI to Modify Settings</span></span>  

 <span data-ttu-id="b2d0b-118">WMI を使用して実行時に構成設定を変更できます (前述の構成例のように構成の `wmiProviderEnabled` 属性を有効にします)。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-118">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="b2d0b-119">たとえば、CIM Studio 内で WMI を使用し、実行時にトレース ソース レベルを Warning から Information に変更できます。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-119">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="b2d0b-120">この方法でライブ デバッグを実行した場合のパフォーマンスへの負荷は非常に高くなる可能性があるので注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-120">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="b2d0b-121">WMI の使用方法の詳細については、「[診断用の WMI (Windows Management Instrumentation) の使用](../wmi/index.md)」トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-121">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="b2d0b-122">ASP.NET トレースでの相関イベントの有効化</span><span class="sxs-lookup"><span data-stu-id="b2d0b-122">Enable Correlated Events in ASP.NET Tracing</span></span>  

 <span data-ttu-id="b2d0b-123">ASP.NET イベントでは、ASP.NET イベントのトレースが有効になっていないと、相関 ID (ActivityID) が設定されません。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-123">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="b2d0b-124">相関イベントを適切に表示するには、 **[スタート]** 、 **[ファイル名を指定して実行]** をクリックして「**cmd**」と入力することで起動するコマンド コンソールで、次のコマンドを使用して ASP.NET イベントのトレースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-124">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="b2d0b-125">ASP.NET イベントのトレースを無効にするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b2d0b-125">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2d0b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2d0b-126">See also</span></span>

- [<span data-ttu-id="b2d0b-127">診断用の WMI (Windows Management Instrumentation) の使用</span><span class="sxs-lookup"><span data-stu-id="b2d0b-127">Using Windows Management Instrumentation for Diagnostics</span></span>](../wmi/index.md)
