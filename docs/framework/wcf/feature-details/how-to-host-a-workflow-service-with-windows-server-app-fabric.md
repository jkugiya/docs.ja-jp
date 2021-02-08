---
description: '詳細については、「方法: Windows Server App Fabric を使用してワークフローサービスをホストする」を参照してください。'
title: '方法: Windows Server AppFabric を使用してワークフロー サービスをホストする'
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: 057e81c50844d1a36e32fe899de3469f024d775b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793806"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a><span data-ttu-id="84582-103">方法: Windows Server AppFabric を使用してワークフロー サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="84582-103">How to: Host a Workflow Service with Windows Server App Fabric</span></span>

<span data-ttu-id="84582-104">AppFabric でのワークフロー サービスのホスティングは IIS/WAS でのホスティングに似ています。</span><span class="sxs-lookup"><span data-stu-id="84582-104">Hosting workflow services in App Fabric is similar to hosting under IIS/WAS.</span></span> <span data-ttu-id="84582-105">唯一の違いは、ワークフロー サービスの投入、監視、および管理のために AppFabric に用意されているツールです。</span><span class="sxs-lookup"><span data-stu-id="84582-105">The only difference is the tools App Fabric provides for deploying, monitoring, and managing workflow services.</span></span> <span data-ttu-id="84582-106">このトピックでは、 [実行時間の長いワークフローサービスの作成](creating-a-long-running-workflow-service.md)によって作成されたワークフローサービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="84582-106">This topic uses the workflow service created in the [Creating a Long-running Workflow Service](creating-a-long-running-workflow-service.md).</span></span> <span data-ttu-id="84582-107">ワークフロー サービスの作成方法はそちらのトピックで説明されています。</span><span class="sxs-lookup"><span data-stu-id="84582-107">That topic will walk you through creating a workflow service.</span></span> <span data-ttu-id="84582-108">このトピックでは、AppFabric を使用したワークフロー サービスのホスティング方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="84582-108">This topic will explain how to host the workflow service using App Fabric.</span></span> <span data-ttu-id="84582-109">Windows Server App Fabric の詳細については、 [Windows Server App fabric のドキュメント](/previous-versions/appfabric/ff384253(v=azure.10))を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84582-109">For more information about Windows Server App Fabric, see [Windows Server App Fabric Documentation](/previous-versions/appfabric/ff384253(v=azure.10)).</span></span> <span data-ttu-id="84582-110">下の手順を完了する前に、Windows Server AppFabric がインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="84582-110">Before completing the steps below make sure you have Windows Server App Fabric installed.</span></span>  <span data-ttu-id="84582-111">これを行うにはインターネットインフォメーションサービス (inetmgr.exe) を開き、[ **接続** ] ビューでサーバー名をクリックし、[サイト] をクリックして、[ **既定の Web サイト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84582-111">To do this open up Internet Information Services (inetmgr.exe), click your server name in the **Connections** view, click Sites, and click **Default Web Site**.</span></span> <span data-ttu-id="84582-112">画面の右側には、[ **App Fabric**] というセクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84582-112">In the right-hand side of the screen you should see a section called **App Fabric**.</span></span> <span data-ttu-id="84582-113">(右側のペインの一番上に表示される) このセクションが表示されない場合は、AppFabric がインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="84582-113">If you don’t see this section (it will be on the top of the right-hand pane) you do not have App Fabric installed.</span></span> <span data-ttu-id="84582-114">Windows Server App Fabric のインストールの詳細については、「 [Windows Server App fabric のインストール](/previous-versions/appfabric/ee790960(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84582-114">For more information about installing Windows Server App Fabric see [Installing Windows Server App Fabric](/previous-versions/appfabric/ee790960(v=azure.10)).</span></span>  
  
### <a name="creating-a-simple-workflow-service"></a><span data-ttu-id="84582-115">単純なワークフロー サービスの作成</span><span class="sxs-lookup"><span data-stu-id="84582-115">Creating a Simple Workflow Service</span></span>  
  
1. <span data-ttu-id="84582-116">Visual Studio 2012 を開き、 [実行時間の長いワークフローサービスの作成](creating-a-long-running-workflow-service.md) に関するトピックで作成した orderprocessing ソリューションを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="84582-116">Open Visual Studio 2012 and load the OrderProcessing solution you created in the [Creating a Long-running Workflow Service](creating-a-long-running-workflow-service.md) topic.</span></span>  
  
2. <span data-ttu-id="84582-117">**Orderservice** プロジェクトを右クリックし、[**プロパティ**] をクリックして、[ **Web** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="84582-117">Right click the **OrderService** project and select **Properties** and select the **Web** tab.</span></span>  
  
3. <span data-ttu-id="84582-118">プロパティページの [ **開始アクション** ] セクションで、 **特定のページ** を選択し、編集ボックスに「Service1. .xamlx」と入力します。</span><span class="sxs-lookup"><span data-stu-id="84582-118">In the **Start Action** section of the property page select **Specific Page** and type Service1.xamlx in the edit box.</span></span>  
  
4. <span data-ttu-id="84582-119">[プロパティ] ページの [ **サーバー** ] セクションで、[ **ローカル IIS Web サーバーを使用する** ] を選択し、次の URL を入力し `http://localhost/OrderService` ます。</span><span class="sxs-lookup"><span data-stu-id="84582-119">In the **Servers** section of the property page select **Use Local IIS Web Server** and type in the following URL: `http://localhost/OrderService`.</span></span>  
  
5. <span data-ttu-id="84582-120">[ **仮想ディレクトリの作成** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="84582-120">Click the **Create Virtual Directory** button.</span></span> <span data-ttu-id="84582-121">これで新しい仮想ディレクトリが作成され、プロジェクトが作成されるときに必要なファイルが仮想ディレクトリにコピーされるようにプロジェクトが設定されます。</span><span class="sxs-lookup"><span data-stu-id="84582-121">This will create a new virtual directory and set up the project to copy the needed files to the virtual directory when the project is built.</span></span>  <span data-ttu-id="84582-122">または、仮想ディレクトリに .xamlx、web.config、および必要な DLL を手動でコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="84582-122">Alternatively you could manually copy the .xamlx, the web.config, and any needed DLLs to the virtual directory.</span></span>  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a><span data-ttu-id="84582-123">Windows Server AppFabric でホストされるワークフロー サービスの構成</span><span class="sxs-lookup"><span data-stu-id="84582-123">Configuring a Workflow Service Hosted in Windows Server App Fabric</span></span>  
  
1. <span data-ttu-id="84582-124">インターネット インフォメーション サービス マネージャー (inetmgr.exe) を開きます。</span><span class="sxs-lookup"><span data-stu-id="84582-124">Open Internet Information Services Manager (inetmgr.exe).</span></span>  
  
2. <span data-ttu-id="84582-125">[ **接続** ] ウィンドウで、orderservice 仮想ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="84582-125">Navigate to the OrderService virtual directory in the **Connections** pane.</span></span>  
  
3. <span data-ttu-id="84582-126">[OrderService] を右クリックし、[ **WCF および WF サービスの管理**]、[ **構成.**..] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="84582-126">Right click OrderService and select **Manage WCF and WF Services**, **Configure…**.</span></span> <span data-ttu-id="84582-127">[ **アプリケーションの WCF と WF の構成** ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84582-127">The **Configure WCF and WF for Application** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="84582-128">[ **全般** ] タブを選択すると、次のスクリーンショットに示すように、アプリケーションに関する全般的な情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84582-128">Select the **General** tab to display general information about the application as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="84582-129">![[全般] タブ ([App Fabric の 構成] ダイアログ ボックス)](media/appfabricconfiguration-general.gif "AppFabricConfiguration-General")</span><span class="sxs-lookup"><span data-stu-id="84582-129">![General tab of the App Fabric Configuration dialog](media/appfabricconfiguration-general.gif "AppFabricConfiguration-General")</span></span>  
  
5. <span data-ttu-id="84582-130">[ **監視** ] タブを選択します。次のスクリーンショットに示すように、さまざまな監視設定が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84582-130">Select the **Monitoring** tab. This shows various monitoring settings as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="84582-131">![App Fabric の構成の [監視] タブ](media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration-Monitoring")</span><span class="sxs-lookup"><span data-stu-id="84582-131">![App Fabric Configuration Monitoring tab](media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration-Monitoring")</span></span>  
  
     <span data-ttu-id="84582-132">App Fabric でのワークフローサービスの監視の構成の詳細については、「 [App fabric で監視を構成する](/previous-versions/appfabric/ee677384(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84582-132">For more information about configuring workflow service monitoring in App Fabric see [Configuring monitoring with App Fabric](/previous-versions/appfabric/ee677384(v=azure.10)).</span></span>  
  
6. <span data-ttu-id="84582-133">[ **ワークフローの永続** 化] タブを選択します。これにより、次のスクリーンショットに示すように、App Fabric の既定の永続化プロバイダーを使用するようにアプリケーションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="84582-133">Select the **Workflow Persistence** tab. This allows you to configure your application to use App Fabric’s default persistence provider as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="84582-134">![App Fabric の構成 &#45; 永続化](media/appfabricconfiguration-persistence.gif "AppFabricConfiguration-Persistence")</span><span class="sxs-lookup"><span data-stu-id="84582-134">![App Fabric Configuration &#45; Persistence](media/appfabricconfiguration-persistence.gif "AppFabricConfiguration-Persistence")</span></span>  
  
     <span data-ttu-id="84582-135">Windows Server App Fabric でのワークフロー永続化の構成の詳細については、「 [App fabric でのワークフロー永続化の構成](/previous-versions/appfabric/ee677353(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84582-135">For more information about configuring workflow persistence in Windows Server App Fabric see [Configuring Workflow Persistence in App Fabric](/previous-versions/appfabric/ee677353(v=azure.10)).</span></span>  
  
7. <span data-ttu-id="84582-136">[ **ワークフローホストの管理** ] タブを選択します。これにより、次のスクリーンショットに示すように、アイドル状態のワークフローサービスインスタンスをアンロードして永続化する必要があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="84582-136">Select the **Workflow Host Management** tab. This allows you to specify when idle workflow service instances should be unloaded and persisted as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="84582-137">![App Fabric の構成ワークフローのホスト管理](media/appfabricconfiguration-management.gif "AppFabricConfiguration-Management")</span><span class="sxs-lookup"><span data-stu-id="84582-137">![App Fabric Configuration  Workflow Host Management](media/appfabricconfiguration-management.gif "AppFabricConfiguration-Management")</span></span>  
  
     <span data-ttu-id="84582-138">ワークフローホスト管理の構成の詳細については、「 [App Fabric でのワークフローホスト管理の構成](/previous-versions/appfabric/ff383424(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84582-138">For more information about workflow host management configuration see [Configuring Workflow Host Management in App Fabric](/previous-versions/appfabric/ff383424(v=azure.10)).</span></span>  
  
8. <span data-ttu-id="84582-139">[ **自動開始** ] タブを選択します。これにより、次のスクリーンショットに示すように、アプリケーションのワークフローサービスの自動開始設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="84582-139">Select the **Auto-Start** tab. This allows you to specify auto-start settings for the workflow services in the application as shown in the following screenshot.</span></span>  
  
     ![App Fabric の自動&#45;構成の開始を示すスクリーンショット。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-auto-start-configuration.gif)  
  
     <span data-ttu-id="84582-141">自動開始の構成の詳細については、「 [App Fabric を使用した自動開始の構成](/previous-versions/appfabric/ee677261(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84582-141">For more information about configuring Auto-Start see [Configuring Auto-Start with App Fabric](/previous-versions/appfabric/ee677261(v=azure.10)).</span></span>  
  
9. <span data-ttu-id="84582-142">[ **調整** ] タブを選択します。これにより、次のスクリーンショットに示すように、ワークフローサービスの制限設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="84582-142">Select the **Throttling** tab. This allows you to configure throttling settings for the workflow service as shown in the following screenshot.</span></span>  
  
     ![App Fabric の制限の構成を示すスクリーンショット。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-throttling-configuration.gif)  
  
     <span data-ttu-id="84582-144">スロットルの構成の詳細については、「 [App Fabric でのスロットルの構成](/previous-versions/appfabric/ee677261(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84582-144">For more information about configuring throttling see [Configuring Throttling with App Fabric](/previous-versions/appfabric/ee677261(v=azure.10)).</span></span>  
  
10. <span data-ttu-id="84582-145">[ **セキュリティ** ] タブを選択します。これにより、次のスクリーンショットに示すように、アプリケーションのセキュリティ設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="84582-145">Select the **Security** tab. This allows you to configure security settings for the application as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="84582-146">![App Fabric のセキュリティ構成](media/appfabricconfiguration-security.gif "AppFabricConfiguration-Security")</span><span class="sxs-lookup"><span data-stu-id="84582-146">![App Fabric Security Configuration](media/appfabricconfiguration-security.gif "AppFabricConfiguration-Security")</span></span>  
  
     <span data-ttu-id="84582-147">Windows Server App Fabric でセキュリティを構成する方法の詳細については、「 [App fabric でのセキュリティの構成](/previous-versions/appfabric/ee677278(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84582-147">For more information about configuring security with Windows Server App Fabric see [Configuring Security with App Fabric](/previous-versions/appfabric/ee677278(v=azure.10)).</span></span>  
  
### <a name="using-windows-server-app-fabric"></a><span data-ttu-id="84582-148">Windows Server AppFabric の使用</span><span class="sxs-lookup"><span data-stu-id="84582-148">Using Windows Server App Fabric</span></span>  
  
1. <span data-ttu-id="84582-149">ソリューションを作成して、仮想ディレクトリに必要なファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="84582-149">Build the solution to copy the necessary files to the virtual directory.</span></span>  
  
2. <span data-ttu-id="84582-150">OrderClient プロジェクトを右クリックし、[ **デバッグ**]、[ **新しいインスタンスを開始** ] の順に選択して、クライアントアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="84582-150">Right click the OrderClient project and select **Debug**, **Start New Instance** to launch the client application.</span></span>  
  
3. <span data-ttu-id="84582-151">クライアントが実行され、Visual Studio に [ **セキュリティ警告の添付** ] ダイアログボックスが表示されます。 [ **アタッチしない** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="84582-151">The client will run and Visual Studio will display an **Attach Security Warning** dialog box, click the **Don’t Attach** button.</span></span> <span data-ttu-id="84582-152">これにより、IIS プロセスにアタッチしてデバッグしないように Visual Studio に指示します。</span><span class="sxs-lookup"><span data-stu-id="84582-152">This tells Visual Studio to not attach to the IIS process for debugging.</span></span>  
  
4. <span data-ttu-id="84582-153">クライアント アプリケーションは直ちにワークフロー サービスを呼び出して待機します。</span><span class="sxs-lookup"><span data-stu-id="84582-153">The client application will immediately call the Workflow service and then wait.</span></span> <span data-ttu-id="84582-154">ワークフロー サービスはアイドル状態になり永続化されます。</span><span class="sxs-lookup"><span data-stu-id="84582-154">The workflow service will go idle and be persisted.</span></span> <span data-ttu-id="84582-155">これは、インターネット インフォメーション サービス (inetmgr.exe) を開始して、[接続] ペインで [OrderService] に移動し、それを選択することによって確認できます。</span><span class="sxs-lookup"><span data-stu-id="84582-155">You can verify this by starting Internet Information Services (inetmgr.exe), navigating to the OrderService in the Connections pane and selecting it.</span></span> <span data-ttu-id="84582-156">次に、右側のペインで [App Fabric ダッシュボード] のアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="84582-156">Next, click the App Fabric Dashboard icon in the right-hand pane.</span></span> <span data-ttu-id="84582-157">[永続化された WF インスタンス] には、次のスクリーンショットに示すように、永続化されたワークフローサービスインスタンスが1つ表示されます。</span><span class="sxs-lookup"><span data-stu-id="84582-157">Under Persisted WF Instances you will see there is one persisted workflow service instance as shown in the following screenshot.</span></span>  
  
     ![App Fabric ダッシュボードを示すスクリーンショット。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-dashboard.gif)  
  
     <span data-ttu-id="84582-159">**WF インスタンス履歴** には、ワークフローサービスのアクティブ化の数、ワークフローサービスインスタンスの入力候補の数、失敗したワークフローインスタンスの数など、ワークフローサービスに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84582-159">The **WF Instance History** lists information about the workflow service such as the number of workflow service activations, the number of workflow service instance completions, and the number of workflow instances with failures.</span></span> <span data-ttu-id="84582-160">アクティブまたはアイドル状態のインスタンスの下にリンクが表示されます。リンクをクリックすると、次のスクリーンショットに示すように、アイドル状態のワークフローインスタンスに関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84582-160">Under Active or Idle instances a link will be displayed, clicking on the link will display more information about the idle workflow instances as shown in the following screenshot.</span></span>  
  
     ![永続化されたワークフローインスタンスの詳細を示すスクリーンショット。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/persisted-workflow-instance-detail.gif)  
  
     <span data-ttu-id="84582-162">Windows Server App Fabric の機能とその使用方法の詳細については、「 [Windows Server App fabric のホスト機能](/previous-versions/appfabric/ee677189(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84582-162">For more information about Windows Server App Fabric features and how to use them see [Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84582-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="84582-163">See also</span></span>

- [<span data-ttu-id="84582-164">長時間のワークフロー サービスの作成</span><span class="sxs-lookup"><span data-stu-id="84582-164">Creating a Long-running Workflow Service</span></span>](creating-a-long-running-workflow-service.md)
- <span data-ttu-id="84582-165">[AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="84582-165">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
- <span data-ttu-id="84582-166">[Windows Server App Fabric のインストール](/previous-versions/appfabric/ee790960(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="84582-166">[Installing Windows Server App Fabric](/previous-versions/appfabric/ee790960(v=azure.10))</span></span>
- <span data-ttu-id="84582-167">[Windows Server App Fabric のドキュメント](/previous-versions/appfabric/ff384253(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="84582-167">[Windows Server App Fabric Documentation](/previous-versions/appfabric/ff384253(v=azure.10))</span></span>
