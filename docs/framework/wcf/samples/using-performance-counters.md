---
description: 詳細については、「パフォーマンスカウンターの使用」を参照してください。
title: パフォーマンス カウンターの使用
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: f2305310238df9c11ebc2612248f2d7d1b6ea6f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755734"
---
# <a name="using-performance-counters"></a><span data-ttu-id="55d2a-103">パフォーマンス カウンターの使用</span><span class="sxs-lookup"><span data-stu-id="55d2a-103">Using Performance Counters</span></span>

<span data-ttu-id="55d2a-104">このサンプルでは、Windows Communication Foundation (WCF) パフォーマンスカウンターにアクセスする方法と、ユーザー定義のパフォーマンスカウンターを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="55d2a-104">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="55d2a-105">このサンプルは、 [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="55d2a-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55d2a-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55d2a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="55d2a-107">このサンプルでは、クライアントが `ICalculator` サービスの 4 つのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="55d2a-107">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="55d2a-108">この処理は、ユーザーが中断するまで継続して行われます。</span><span class="sxs-lookup"><span data-stu-id="55d2a-108">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="55d2a-109">サービスは変更されません。</span><span class="sxs-lookup"><span data-stu-id="55d2a-109">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="55d2a-110">パフォーマンス カウンタは、サービスの Web.config ファイルの診断セクションで有効にします。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55d2a-110">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="55d2a-111">このタスクは、 [構成エディターツール (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)を使用して行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="55d2a-111">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="55d2a-112">パフォーマンスカウンターを有効にすると、WCF パフォーマンスカウンターのスイート全体がサービスに対して有効になります。</span><span class="sxs-lookup"><span data-stu-id="55d2a-112">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="55d2a-113">.NET Framework は、`ServiceModelService`、`ServiceModelEndpoint`、および `ServiceModelOperation` の 3 つのレベルで、パフォーマンス データを自動的に保持します。</span><span class="sxs-lookup"><span data-stu-id="55d2a-113">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="55d2a-114">これらの各レベルには、"呼び出し"、"1 秒あたりの呼び出し回数"、"承認されていないセキュリティ呼び出し" などのパフォーマンス カウンタがあります。</span><span class="sxs-lookup"><span data-stu-id="55d2a-114">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="55d2a-115">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="55d2a-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="55d2a-116">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="55d2a-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="55d2a-117">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="55d2a-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="55d2a-118">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="55d2a-118">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="55d2a-119">パフォーマンス データを表示するには</span><span class="sxs-lookup"><span data-stu-id="55d2a-119">To view performance data</span></span>  
  
1. <span data-ttu-id="55d2a-120">パフォーマンスモニターツールを起動するには、[**スタート**] ボタンをクリックし、[**実行**] をクリックして、enter キーを押します。 `perfmon` または、[コントロールパネル] で [  **管理ツール**] を選択し、[**パフォーマンス**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="55d2a-120">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="55d2a-121">サンプル コードが実行されるまでは、カウンタを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="55d2a-121">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="55d2a-122">一覧表示されているパフォーマンス カウンタを削除するには、削除するパフォーマンス カウンタを選択して Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="55d2a-122">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="55d2a-123">WCF カウンターを追加するには、グラフペインを右クリックし、[ **カウンターの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="55d2a-123">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="55d2a-124">[ **カウンターの追加** ] ダイアログボックスで、[パフォーマンスオブジェクト] ボックスの一覧の [ **ServiceModelOperation 3.0.0.0、ServiceModelEndpoint 3.0.0.0、または ServiceModelService 3.0.0.0** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="55d2a-124">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="55d2a-125">表示するカウンタを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="55d2a-125">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="55d2a-126">コンピューターで WCF サービスが実行されていない場合、サービスの WCF パフォーマンスカウンターはありません。</span><span class="sxs-lookup"><span data-stu-id="55d2a-126">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="55d2a-127">構成エディターを使用してカウンターを有効にするには</span><span class="sxs-lookup"><span data-stu-id="55d2a-127">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="55d2a-128">SvcConfigEditor.exe のインスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="55d2a-128">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="55d2a-129">[ファイル] メニューの [ **開く** ] をクリックし、[ **構成ファイル...**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55d2a-129">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="55d2a-130">サンプル アプリケーションの service フォルダーに移動し、Web.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="55d2a-130">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="55d2a-131">構成ツリーで [ **診断** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55d2a-131">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="55d2a-132">[**診断**] ウィンドウの [**パフォーマンスカウンター** ] を [すべて] に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="55d2a-132">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="55d2a-133">構成ファイルを保存し、エディターを終了します。</span><span class="sxs-lookup"><span data-stu-id="55d2a-133">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="55d2a-134">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="55d2a-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="55d2a-135">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="55d2a-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="55d2a-136">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="55d2a-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55d2a-137">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="55d2a-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="55d2a-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="55d2a-138">See also</span></span>

- <span data-ttu-id="55d2a-139">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="55d2a-139">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
