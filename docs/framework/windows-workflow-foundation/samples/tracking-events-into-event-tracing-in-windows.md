---
description: 詳細については、「Windows のイベントトレースへのイベントの追跡」を参照してください。
title: Windows のイベント トレースへの追跡イベント
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 92ad4aaee100bb3ba7f4174bbbde1dc7eaed58de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653746"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="b6c65-103">Windows のイベント トレースへの追跡イベント</span><span class="sxs-lookup"><span data-stu-id="b6c65-103">Tracking Events into Event Tracing in Windows</span></span>

<span data-ttu-id="b6c65-104">このサンプルでは、ワークフローサービスで Windows Workflow Foundation (WF) 追跡を有効にし、Windows イベントトレーシング (ETW) で追跡イベントを出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-104">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="b6c65-105">ワークフロー追跡レコードを ETW に出力するために、このサンプルでは ETW 追跡参加要素 (<xref:System.Activities.Tracking.EtwTrackingParticipant>) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-105">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>

<span data-ttu-id="b6c65-106">このサンプルのワークフローでは、要求を受け取り、入力データの逆数を入力変数に割り当てて、クライアントに逆数を返します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-106">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="b6c65-107">入力データが 0 の場合、処理されない 0 による除算の例外が発生し、ワークフローが中止されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-107">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="b6c65-108">追跡を有効にすると、エラー追跡レコードが ETW に出力され、後でエラーをトラブルシューティングする際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-108">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="b6c65-109">ETW 追跡参加要素は、追跡レコードを定期受信するように追跡プロファイルで構成されています。</span><span class="sxs-lookup"><span data-stu-id="b6c65-109">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="b6c65-110">追跡プロファイルは、Web.config ファイルで定義され、構成パラメーターとして ETW 追跡参加要素に渡されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-110">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="b6c65-111">ETW 追跡参加要素は、ワークフロー サービスの Web.config ファイルで構成され、サービス動作としてサービスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-111">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="b6c65-112">このサンプルでは、イベント ログの追跡イベントをイベント ビューアーを使用して確認します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-112">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>

## <a name="workflow-tracking-details"></a><span data-ttu-id="b6c65-113">ワークフロー追跡の詳細</span><span class="sxs-lookup"><span data-stu-id="b6c65-113">Workflow Tracking Details</span></span>

<span data-ttu-id="b6c65-114">Windows Workflow Foundation は、ワークフローインスタンスの実行を追跡するための追跡インフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-114">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="b6c65-115">追跡ランタイムは、ワークフロー ライフサイクルに関連するイベント、ワークフロー アクティビティのイベント、およびカスタム イベントを出力するワークフロー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-115">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="b6c65-116">次の表で、追跡インフラストラクチャの主要コンポーネントの詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-116">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="b6c65-117">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b6c65-117">Component</span></span>|<span data-ttu-id="b6c65-118">説明</span><span class="sxs-lookup"><span data-stu-id="b6c65-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b6c65-119">追跡ランタイム</span><span class="sxs-lookup"><span data-stu-id="b6c65-119">Tracking runtime</span></span>|<span data-ttu-id="b6c65-120">追跡レコードを出力するためのインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-120">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="b6c65-121">追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="b6c65-121">Tracking participants</span></span>|<span data-ttu-id="b6c65-122">追跡レコードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="b6c65-122">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] <span data-ttu-id="b6c65-123">には、追跡レコードを Event Tracing for Windows (ETW) イベントとして書き込む追跡参加要素が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b6c65-123">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="b6c65-124">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="b6c65-124">Tracking profile</span></span>|<span data-ttu-id="b6c65-125">ワークフロー インスタンスから出力された追跡レコードのサブセットを追跡参加要素から定期受信するためのフィルター機構。</span><span class="sxs-lookup"><span data-stu-id="b6c65-125">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

<span data-ttu-id="b6c65-126">次の表で、ワークフロー ランタイムが出力する追跡レコードの詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-126">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="b6c65-127">追跡レコード</span><span class="sxs-lookup"><span data-stu-id="b6c65-127">Tracking record</span></span>|<span data-ttu-id="b6c65-128">説明</span><span class="sxs-lookup"><span data-stu-id="b6c65-128">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="b6c65-129">ワークフロー インスタンスの追跡レコード</span><span class="sxs-lookup"><span data-stu-id="b6c65-129">Workflow instance tracking records.</span></span>|<span data-ttu-id="b6c65-130">ワークフロー インスタンスのライフサイクルを表します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-130">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="b6c65-131">たとえば、ワークフローの開始時または完了時にインスタンス レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-131">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="b6c65-132">アクティビティ状態の追跡レコード</span><span class="sxs-lookup"><span data-stu-id="b6c65-132">Activity state tracking records.</span></span>|<span data-ttu-id="b6c65-133">アクティビティの実行状況を詳しく記録します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-133">Details activity execution.</span></span> <span data-ttu-id="b6c65-134">これらのレコードは、アクティビティをスケジュールしたとき、アクティビティが完了したとき、エラーがスローされたときなど、ワークフロー アクティビティの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-134">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="b6c65-135">ブックマーク再開レコード</span><span class="sxs-lookup"><span data-stu-id="b6c65-135">Bookmark resumption record.</span></span>|<span data-ttu-id="b6c65-136">ワークフロー インスタンス内のブックマークが再開されたときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-136">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="b6c65-137">カスタム追跡レコード</span><span class="sxs-lookup"><span data-stu-id="b6c65-137">Custom tracking records.</span></span>|<span data-ttu-id="b6c65-138">ワークフロー作成者はカスタム追跡レコードを作成し、カスタム アクティビティ内で出力できます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-138">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="b6c65-139">このレコードは、アクティビティが別のアクティビティをスケジュールするときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-139">This record is emitted when an activity schedules another activity.</span></span>|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="b6c65-140">このレコードは、アクティビティからエラーが伝達されたときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-140">This record is emitted when a fault is propagated from an activity.</span></span>|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="b6c65-141">このレコードは、アクティビティが別のアクティビティによって取り消されたときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-141">This record is emitted when an activity is canceled by another activity.</span></span>|

<span data-ttu-id="b6c65-142">追跡参加要素は、追跡プロファイルを使用して、出力された追跡レコードのサブセットを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-142">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="b6c65-143">追跡プロファイルには、特定の追跡レコード タイプを定期受信するための追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b6c65-143">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="b6c65-144">追跡プロファイルは、コードで指定したり、構成で指定したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-144">Tracking profiles can be specified in code or in configuration.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="b6c65-145">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="b6c65-145">To use this sample</span></span>

1. <span data-ttu-id="b6c65-146">Visual Studio 2010 を使用して、EtwTrackingParticipantSample ソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-146">Using Visual Studio 2010, open the EtwTrackingParticipantSample.sln solution file.</span></span>

2. <span data-ttu-id="b6c65-147">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-147">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="b6c65-148">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-148">To run the solution, press F5.</span></span>

    <span data-ttu-id="b6c65-149">既定では、サービスはポート 53797 () でリッスンしてい `http://localhost:53797/SampleWorkflowService.xamlx` ます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-149">By default, the service is listening on port 53797 (`http://localhost:53797/SampleWorkflowService.xamlx`).</span></span>

4. <span data-ttu-id="b6c65-150">ファイルエクスプローラーを使用して、WCF テストクライアントを開きます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-150">Using File Explorer, open the WCF test client.</span></span>

    <span data-ttu-id="b6c65-151">WCF テストクライアント (WcfTestClient.exe) は \Common7\IDE\ フォルダーにあり \<Visual Studio 2010 installation folder> ます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-151">The WCF test client (WcfTestClient.exe) is located in the \<Visual Studio 2010 installation folder>\Common7\IDE\ folder.</span></span>

    <span data-ttu-id="b6c65-152">既定の Visual Studio 2010 インストールフォルダーは、C:\Program の Visual Studio 10.0 です。</span><span class="sxs-lookup"><span data-stu-id="b6c65-152">The default Visual Studio 2010 installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>

5. <span data-ttu-id="b6c65-153">WCF テストクライアントで、[**ファイル**] メニューの [**サービスの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-153">In WCF test client, select **Add Service** from the **File** menu.</span></span>

    <span data-ttu-id="b6c65-154">入力ボックスにエンドポイントのアドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-154">Add the endpoint address in the input box.</span></span> <span data-ttu-id="b6c65-155">既定値は、`http://localhost:53797/SampleWorkflowService.xamlx` です。</span><span class="sxs-lookup"><span data-stu-id="b6c65-155">The default is `http://localhost:53797/SampleWorkflowService.xamlx`.</span></span>

6. <span data-ttu-id="b6c65-156">イベント ビューアー アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-156">Open the Event Viewer application.</span></span>

    <span data-ttu-id="b6c65-157">サービスを呼び出す前に、[ **スタート** ] メニューからイベントビューアーを開始し、[ **実行** ] を選択して「」と入力し `eventvwr.exe` ます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-157">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="b6c65-158">ワークフロー サービスから生成された追跡イベントをイベント ログでリッスンしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-158">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>

7. <span data-ttu-id="b6c65-159">イベントビューアーのツリービューで、[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-159">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="b6c65-160">[ **Microsoft** ] を右クリックして [ **表示** ] を選択し、[ **分析およびデバッグログの表示** ] をクリックして、分析ログとデバッグログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b6c65-160">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>

    <span data-ttu-id="b6c65-161">[ **分析とデバッグログを表示** する] オプションがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-161">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

8. <span data-ttu-id="b6c65-162">イベントビューアーのツリービューで、[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-162">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b6c65-163">[ **分析** ] を右クリックし、[ **ログを有効** にする] を選択して、 **分析** ログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b6c65-163">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>

9. <span data-ttu-id="b6c65-164">WCF テスト クライアントで、`GetData` をダブルクリックしてサービスをテストします。</span><span class="sxs-lookup"><span data-stu-id="b6c65-164">Test the service using the WCF test client by double-clicking `GetData`.</span></span>

    <span data-ttu-id="b6c65-165">`GetData` メソッドが開きます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-165">This opens the `GetData` method.</span></span> <span data-ttu-id="b6c65-166">この要求はパラメーターを 1 つ受け取ります。値が 0 (既定値) になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-166">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>

     <span data-ttu-id="b6c65-167">[ **呼び出し**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6c65-167">Click **Invoke**.</span></span>

10. <span data-ttu-id="b6c65-168">ワークフローから出力されたイベントを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-168">Observe the events emitted from the workflow.</span></span>

    <span data-ttu-id="b6c65-169">イベントビューアーに戻り、[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-169">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b6c65-170">[ **分析** ] を右クリックし、[ **更新**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-170">Right-click **Analytic** and select **Refresh**.</span></span>

    <span data-ttu-id="b6c65-171">イベント ビューアーにワークフロー イベントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-171">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="b6c65-172">ワークフロー実行イベントが表示され、その中にワークフローのエラーに対応する未処理の例外が含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b6c65-172">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="b6c65-173">また、アクティビティがエラーをスローしたことを示す警告イベントもワークフロー アクティビティから出力されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-173">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>

11. <span data-ttu-id="b6c65-174">エラーがスローされないように入力データを 0 以外にして、手順 9. と 10. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-174">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>

<span data-ttu-id="b6c65-175">追跡プロファイルを使用すると、実行時にワークフロー インスタンスの状態が変化したときに生成されるイベントを定期受信できます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-175">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="b6c65-176">監視の要件に応じて、ワークフローの主な状態変化の少数のセットを定期受信する、大まかなプロファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-176">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="b6c65-177">それとは反対に、後で実行を十分に再構築できるほど出力が豊富な、詳細なプロファイルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-177">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="b6c65-178">このサンプルでは、イベントの少数のセットを出力する `HealthMonitoring Tracking Profile` を使用して、ワークフロー ランタイムから ETW に出力されるイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-178">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="b6c65-179">Web.config には、それよりも多くのワークフロー追跡イベントを出力する `Troubleshooting Tracking Profile` という名前の別のプロファイルも用意されています。</span><span class="sxs-lookup"><span data-stu-id="b6c65-179">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="b6c65-180">[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] をインストールすると、Machine.config ファイルでは、空の名前の既定のプロファイルが構成されています。</span><span class="sxs-lookup"><span data-stu-id="b6c65-180">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="b6c65-181">このプロファイルは、プロファイル名が指定されなかった場合や空のプロファイル名が指定された場合に、ETW 追跡動作の構成で使用されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-181">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>

<span data-ttu-id="b6c65-182">状態監視追跡プロファイルでは、ワークフロー インスタンス レコードとアクティビティ エラー伝達レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-182">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="b6c65-183">このプロファイルは、Web.config 構成ファイルに次の追跡プロファイルを追加して作成されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-183">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="HealthMonitoring Tracking Profile">
      <workflow activityDefinitionId="*">
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Started"/>
              <state name="Completed"/>
              <state name="Aborted"/>
              <state name="UnhandledException"/>
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

 <span data-ttu-id="b6c65-184">プロファイルを変更するには、`EtwTrackingParticipant` 構成を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-184">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <etwTracking profileName="HealthMonitoring Tracking Profile"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

#### <a name="to-clean-up-optional"></a><span data-ttu-id="b6c65-185">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="b6c65-185">To clean up (Optional)</span></span>

1. <span data-ttu-id="b6c65-186">イベント ビューアーを開きます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-186">Open Event Viewer.</span></span>

2. <span data-ttu-id="b6c65-187">[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-187">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b6c65-188">[ **分析** ] を右クリックし、[ **ログを無効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-188">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="b6c65-189">[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-189">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b6c65-190">[ **分析** ] を右クリックし、[ **ログの消去**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-190">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="b6c65-191">[ **クリア** ] オプションを選択して、イベントを消去します。</span><span class="sxs-lookup"><span data-stu-id="b6c65-191">Choose the **Clear** option to clear the events.</span></span>

## <a name="known-issue"></a><span data-ttu-id="b6c65-192">既知の問題</span><span class="sxs-lookup"><span data-stu-id="b6c65-192">Known Issue</span></span>

> [!NOTE]
> <span data-ttu-id="b6c65-193">イベント ビューアーの既知の問題により、ETW イベントをデコードできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b6c65-193">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="b6c65-194">その場合、次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-194">You may see an error message that looks like the following.</span></span>
>
> <span data-ttu-id="b6c65-195">\<id>ソース Microsoft-Windows-Application Server-Applications からのイベント ID の説明が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="b6c65-195">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="b6c65-196">このイベントを発生させるコンポーネントがローカル コンピューターにインストールされていないか、インストールが壊れています。</span><span class="sxs-lookup"><span data-stu-id="b6c65-196">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="b6c65-197">ローカル コンピューターにコンポーネントをインストールするか、コンポーネントを修復してください。</span><span class="sxs-lookup"><span data-stu-id="b6c65-197">You can install or repair the component on the local computer.</span></span>
>
> <span data-ttu-id="b6c65-198">このエラーが発生した場合は、操作ウィンドウで [最新の情報に更新] をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="b6c65-198">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="b6c65-199">これにより、イベントが正常にデコードされます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-199">The event should now decode properly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6c65-200">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b6c65-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b6c65-201">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b6c65-201">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b6c65-202">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="b6c65-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b6c65-203">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b6c65-203">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`

## <a name="see-also"></a><span data-ttu-id="b6c65-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6c65-204">See also</span></span>

- <span data-ttu-id="b6c65-205">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b6c65-205">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
