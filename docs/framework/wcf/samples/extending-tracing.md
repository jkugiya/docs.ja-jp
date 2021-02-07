---
description: 詳細については、「トレースの拡張」をご覧ください。
title: トレースの拡張
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: e387f49eb4b31ce8dc0b726853ef69d20c8af063
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752367"
---
# <a name="extend-tracing"></a><span data-ttu-id="4a24e-103">トレースの拡張</span><span class="sxs-lookup"><span data-stu-id="4a24e-103">Extend tracing</span></span>

<span data-ttu-id="4a24e-104">このサンプルでは、ユーザー定義のアクティビティトレースをクライアントとサービスコードに記述することによって、Windows Communication Foundation (WCF) トレース機能を拡張する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4a24e-104">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="4a24e-105">ユーザー定義のアクティビティトレースを記述すると、ユーザーはトレースアクティビティを作成し、トレースを論理的な作業単位にグループ化することができます。</span><span class="sxs-lookup"><span data-stu-id="4a24e-105">Writing user-defined activity traces allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="4a24e-106">さらに、転送 (同じエンドポイント内) や伝達 (異なるエンドポイント間) を経由してアクティビティを相互に関連付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="4a24e-106">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="4a24e-107">このサンプルでは、トレースはクライアントとサービスの両方で有効です。</span><span class="sxs-lookup"><span data-stu-id="4a24e-107">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="4a24e-108">クライアントとサービスの構成ファイルでトレースを有効にする方法の詳細については、「 [トレースとメッセージログ](tracing-and-message-logging.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a24e-108">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="4a24e-109">このサンプルは、 [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="4a24e-109">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a24e-110">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a24e-110">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4a24e-111">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="4a24e-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4a24e-112">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4a24e-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4a24e-113">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="4a24e-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4a24e-114">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4a24e-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="4a24e-115">トレースとアクティビティの伝達</span><span class="sxs-lookup"><span data-stu-id="4a24e-115">Tracing and Activity Propagation</span></span>  

 <span data-ttu-id="4a24e-116">ユーザー定義のアクティビティトレースを使用すると、ユーザーは独自のトレースアクティビティを作成して、トレースを論理的な作業単位にグループ化し、転送と伝達を通じてアクティビティを相互に関連付けることができます。また、WCF トレース (ログファイルのディスク領域コストなど) のパフォーマンスコストを削減することもできます。</span><span class="sxs-lookup"><span data-stu-id="4a24e-116">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="add-custom-sources"></a><span data-ttu-id="4a24e-117">カスタムソースの追加</span><span class="sxs-lookup"><span data-stu-id="4a24e-117">Add custom sources</span></span>  

 <span data-ttu-id="4a24e-118">ユーザー定義のトレースは、クライアントとサービス コードの両方に追加できます。</span><span class="sxs-lookup"><span data-stu-id="4a24e-118">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="4a24e-119">トレースソースをクライアントまたはサービスの構成ファイルに追加することで、これらのカスタムトレースを記録し、 [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)に表示することができます。</span><span class="sxs-lookup"><span data-stu-id="4a24e-119">Adding trace sources to the client or service configuration files allows for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="4a24e-120">次のコードは、`ServerCalculatorTraceSource` というユーザー定義のトレース ソースを構成ファイルに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4a24e-120">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a><span data-ttu-id="4a24e-121">アクティビティの関連付け</span><span class="sxs-lookup"><span data-stu-id="4a24e-121">Correlate activities</span></span>  

 <span data-ttu-id="4a24e-122">エンドポイント間でアクティビティを直接関連付けるには、`propagateActivity` トレース ソースの `true` 属性を `System.ServiceModel` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a24e-122">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="4a24e-123">また、WCF アクティビティを介さずにトレースを伝達するには、ServiceModel アクティビティトレースをオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a24e-123">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="4a24e-124">次のコード サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a24e-124">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a24e-125">ServiceModel アクティビティ トレースをオフにすることは、`switchValue` プロパティが表すトレース レベルをオフにすることとは異なります。</span><span class="sxs-lookup"><span data-stu-id="4a24e-125">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a><span data-ttu-id="4a24e-126">パフォーマンスコストの軽減</span><span class="sxs-lookup"><span data-stu-id="4a24e-126">Lessen performance cost</span></span>  

 <span data-ttu-id="4a24e-127">`ActivityTracing` トレース ソースの `System.ServiceModel` をオフに設定すると、ユーザー定義のアクティビティ トレースのみを含み、ServiceModel アクティビティ トレースは含まないトレース ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4a24e-127">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="4a24e-128">ServiceModel アクティビティトレースを除外すると、ログファイルが大幅に小さくなります。</span><span class="sxs-lookup"><span data-stu-id="4a24e-128">Excluding ServiceModel activity traces results in a much smaller log file.</span></span> <span data-ttu-id="4a24e-129">ただし、WCF 処理トレースを相互に関連付ける機会は失われます。</span><span class="sxs-lookup"><span data-stu-id="4a24e-129">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="4a24e-130">サンプルをセットアップ、ビルド、および実行する</span><span class="sxs-lookup"><span data-stu-id="4a24e-130">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4a24e-131">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4a24e-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4a24e-132">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4a24e-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4a24e-133">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4a24e-133">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a24e-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a24e-134">See also</span></span>

- <span data-ttu-id="4a24e-135">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4a24e-135">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
