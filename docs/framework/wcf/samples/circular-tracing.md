---
description: 詳細については、「循環トレース」を参照してください。
title: 循環トレース
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 4b50420c7eb0c6ca9bc6b3354c78e7922b00f16c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778751"
---
# <a name="circular-tracing"></a><span data-ttu-id="2b939-103">循環トレース</span><span class="sxs-lookup"><span data-stu-id="2b939-103">Circular Tracing</span></span>

<span data-ttu-id="2b939-104">このサンプルでは、循環バッファ トレース リスナの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="2b939-104">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="2b939-105">製品版サービスの一般的なシナリオは、長期間使用できるサービスを持つことと、トレース ログを低レベルで有効にすることです。</span><span class="sxs-lookup"><span data-stu-id="2b939-105">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="2b939-106">こうしたサービスは、大量のディスク領域を消費します。</span><span class="sxs-lookup"><span data-stu-id="2b939-106">These services consume a lot of disk space.</span></span> <span data-ttu-id="2b939-107">サービスのトラブルシューティングを行う場合、問題の解決に関連するのはトレース ログの最新データです。</span><span class="sxs-lookup"><span data-stu-id="2b939-107">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="2b939-108">このサンプルで示す循環バッファ トレース リスナの実装では、設定可能なデータ量を上限とする最新のトレースのみがディスク上に保持されます。</span><span class="sxs-lookup"><span data-stu-id="2b939-108">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="2b939-109">このサンプルは [はじめに](getting-started-sample.md) に基づいており、カスタムトレースリスナーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2b939-109">This sample is based on the [Getting Started](getting-started-sample.md) and includes a custom tracing listener.</span></span>

> [!NOTE]
> <span data-ttu-id="2b939-110">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b939-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="2b939-111">このサンプルでは、 [トレースとメッセージログ](tracing-and-message-logging.md) のサンプルについて理解しており、 [トレースとメッセージログ](tracing-and-message-logging.md) のサンプルに関するドキュメントを参照していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="2b939-111">This sample assumes that you are familiar with the [Tracing and Message Logging](tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](tracing-and-message-logging.md) sample.</span></span>

## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="2b939-112">循環バッファ トレース リスナ</span><span class="sxs-lookup"><span data-stu-id="2b939-112">Circular Buffer Trace Listener</span></span>

<span data-ttu-id="2b939-113">循環バッファ トレース リスナの実装の概念とは、2 つのファイルを使って、必要なトレース ログ データの全体量の半分を上限としたデータをそれぞれに保存することです。</span><span class="sxs-lookup"><span data-stu-id="2b939-113">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="2b939-114">リスナは 1 つのファイルを作成して、データ サイズの半分という限界に到達するまでデータを書き込みます。この限界に到達した時点で、2 番目のファイルに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="2b939-114">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="2b939-115">2 番目のファイルの限界に到達したら、リスナは最初のファイルを新しいトレースで上書きします。</span><span class="sxs-lookup"><span data-stu-id="2b939-115">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>

<span data-ttu-id="2b939-116">このリスナーは、から派生 `XmlWriteTraceListener` し、 [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)でログを表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2b939-116">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="2b939-117">ログの表示を試みる際に、サービス トレース ビューア ツールで 2 つのログ ファイルを両方同時に開くと、これらのファイルを簡単に再結合することができます。</span><span class="sxs-lookup"><span data-stu-id="2b939-117">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="2b939-118">サービス トレース ビューア ツールは、トレースが正しい順序で表示されるように自動的にトレースの並べ替えを管理します。</span><span class="sxs-lookup"><span data-stu-id="2b939-118">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>

## <a name="configuration"></a><span data-ttu-id="2b939-119">構成</span><span class="sxs-lookup"><span data-stu-id="2b939-119">Configuration</span></span>

<span data-ttu-id="2b939-120">サービスは、リスナとソースの要素に対して次のコードを追加することによって、循環バッファ トレース リスナを使用するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="2b939-120">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="2b939-121">ファイルの最大サイズは、循環トレース リスナの構成の `maxFileSizeKB` 属性を設定することによって指定します。</span><span class="sxs-lookup"><span data-stu-id="2b939-121">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="2b939-122">このコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="2b939-122">This is demonstrated in the following code.</span></span>

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">
      <listeners>
        <add name="CircularTraceListener" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />
  </sharedListeners>
  <trace autoflush="true" />
</system.diagnostics>
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2b939-123">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="2b939-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2b939-124">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2b939-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="2b939-125">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2b939-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="2b939-126">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2b939-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b939-127">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b939-127">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2b939-128">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2b939-128">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2b939-129">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="2b939-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2b939-130">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2b939-130">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a><span data-ttu-id="2b939-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b939-131">See also</span></span>

- <span data-ttu-id="2b939-132">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2b939-132">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
