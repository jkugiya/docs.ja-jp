---
description: 詳細については、「WCF 分析トレース」を参照してください。
title: WCF 分析トレース
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: 1f5ec26828bba99a127fea6a81f57fed717943a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755695"
---
# <a name="wcf-analytic-tracing"></a><span data-ttu-id="65d7e-103">WCF 分析トレース</span><span class="sxs-lookup"><span data-stu-id="65d7e-103">WCF Analytic Tracing</span></span>

<span data-ttu-id="65d7e-104">このサンプルでは、の ETW への書き込みを Windows Communication Foundation (WCF) する分析トレースのストリームに独自のトレースイベントを追加する方法を示し [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-104">This sample demonstrates how to add your own tracing events into the stream of analytic traces that Windows Communication Foundation (WCF) writes to ETW in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="65d7e-105">分析トレースは、パフォーマンスを低下させずに簡単にサービスを確認できるようにするためのものです。</span><span class="sxs-lookup"><span data-stu-id="65d7e-105">Analytic traces are meant to make it easy to get visibility into your services without paying a high performance penalty.</span></span> <span data-ttu-id="65d7e-106">このサンプルでは、api を使用して、 <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> WCF サービスと統合するイベントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-106">This sample shows how to use the <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> APIs to write events that integrate with WCF services.</span></span>  
  
 <span data-ttu-id="65d7e-107">Api の詳細については <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> 、「」を参照してください <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="65d7e-107">For more information about the <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> APIs, see <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="65d7e-108">Windows のイベントトレースの詳細については、「 [ETW を使用したデバッグとパフォーマンスチューニングの向上](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65d7e-108">To learn more about event tracing in Windows, see [Improve Debugging and Performance Tuning with ETW](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).</span></span>  
  
## <a name="disposing-eventprovider"></a><span data-ttu-id="65d7e-109">EventProvider の破棄</span><span class="sxs-lookup"><span data-stu-id="65d7e-109">Disposing EventProvider</span></span>  

 <span data-ttu-id="65d7e-110">このサンプルでは、<xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> を実装した <xref:System.IDisposable?displayProperty=nameWithType> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-110">This sample uses the <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> class, which implements <xref:System.IDisposable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="65d7e-111">WCF サービスのトレースを実装する場合、 <xref:System.Diagnostics.Eventing.EventProvider> サービスの有効期間にリソースを使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65d7e-111">When implementing tracing for a WCF service, it is likely that you may use the <xref:System.Diagnostics.Eventing.EventProvider>’s resources for the lifetime of the service.</span></span> <span data-ttu-id="65d7e-112">そのため、読みやすくするためにも、このサンプルでは、ラップされた <xref:System.Diagnostics.Eventing.EventProvider> を破棄しません。</span><span class="sxs-lookup"><span data-stu-id="65d7e-112">For this reason, and for readability, this sample never disposes of the wrapped <xref:System.Diagnostics.Eventing.EventProvider>.</span></span> <span data-ttu-id="65d7e-113">何かの理由で、サービスに対して別のトレースの要件を設定し、このリソースを破棄しなければならない場合は、アンマネージ リソースの破棄に関するベスト プラクティスに従ってこのサンプルを変更してください。</span><span class="sxs-lookup"><span data-stu-id="65d7e-113">If for some reason your service has different requirements for tracing and you must dispose of this resource, then you should modify this sample in accordance with the best practices for disposing of unmanaged resources.</span></span> <span data-ttu-id="65d7e-114">アンマネージリソースの破棄の詳細については、「 [Dispose メソッドの実装](../../../standard/garbage-collection/implementing-dispose.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65d7e-114">For more information about disposing unmanaged resources, see [Implementing a Dispose Method](../../../standard/garbage-collection/implementing-dispose.md).</span></span>  
  
## <a name="self-hosting-vs-web-hosting"></a><span data-ttu-id="65d7e-115">自己ホスト型と Web ホスト型</span><span class="sxs-lookup"><span data-stu-id="65d7e-115">Self-Hosting vs. Web Hosting</span></span>  

 <span data-ttu-id="65d7e-116">Web ホストサービスの場合、WCF の分析トレースでは、トレースを出力するサービスを識別するために使用される "HostReference" というフィールドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-116">For Web-hosted services, WCF’s analytic traces provide a field, called "HostReference", which is used to identify the service that is emitting the traces.</span></span> <span data-ttu-id="65d7e-117">拡張可能なユーザー トレースをこのモデルに加えることができます。このサンプルで、そのためのベスト プラクティスを示します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-117">The extensible user traces can participate in this model and this sample demonstrates best practices for doing so.</span></span> <span data-ttu-id="65d7e-118">結果の文字列にパイプの ' &#124; ' 文字が実際に表示されている場合の Web ホスト参照の形式は、次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="65d7e-118">The format of a Web host reference when the pipe ‘&#124;’ character actually appears in the resulting string can be any one of the following:</span></span>  
  
- <span data-ttu-id="65d7e-119">アプリケーションがルート以外にある場合</span><span class="sxs-lookup"><span data-stu-id="65d7e-119">If the application is not at the root.</span></span>  
  
     <span data-ttu-id="65d7e-120">\<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName></span><span class="sxs-lookup"><span data-stu-id="65d7e-120">\<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName></span></span>  
  
- <span data-ttu-id="65d7e-121">アプリケーションがルートにある場合</span><span class="sxs-lookup"><span data-stu-id="65d7e-121">If the application is at the root.</span></span>  
  
     <span data-ttu-id="65d7e-122">\<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName></span><span class="sxs-lookup"><span data-stu-id="65d7e-122">\<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName></span></span>  
  
 <span data-ttu-id="65d7e-123">自己ホスト型サービスの場合、WCF の分析トレースでは、"HostReference" フィールドは設定されません。</span><span class="sxs-lookup"><span data-stu-id="65d7e-123">For self-hosted services, WCF’s analytic traces do not populate the "HostReference" field.</span></span> <span data-ttu-id="65d7e-124">このサンプルの `WCFUserEventProvider` クラスは、自己ホスト型サービスで使用した場合も同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-124">The `WCFUserEventProvider` class in this sample behaves consistently when used by a self-hosted service.</span></span>  
  
## <a name="custom-event-details"></a><span data-ttu-id="65d7e-125">カスタム イベントの詳細</span><span class="sxs-lookup"><span data-stu-id="65d7e-125">Custom Event Details</span></span>  

 <span data-ttu-id="65d7e-126">WCF の ETW イベントプロバイダーマニフェストは、サービスコード内から WCF サービス作成者によって出力されるように設計された3つのイベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-126">WCF’s ETW Event Provider manifest defines three events that are designed to be emitted by WCF service authors from within service code.</span></span> <span data-ttu-id="65d7e-127">次の表に、その 3 つのイベントの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-127">The following table shows a breakdown of the three events.</span></span>  
  
|<span data-ttu-id="65d7e-128">event</span><span class="sxs-lookup"><span data-stu-id="65d7e-128">Event</span></span>|<span data-ttu-id="65d7e-129">説明</span><span class="sxs-lookup"><span data-stu-id="65d7e-129">Description</span></span>|<span data-ttu-id="65d7e-130">イベント ID</span><span class="sxs-lookup"><span data-stu-id="65d7e-130">Event ID</span></span>|  
|-----------|-----------------|--------------|  
|<span data-ttu-id="65d7e-131">UserDefinedInformationEventOccurred</span><span class="sxs-lookup"><span data-stu-id="65d7e-131">UserDefinedInformationEventOccurred</span></span>|<span data-ttu-id="65d7e-132">このイベントは、問題以外の通知すべき処理がサービスで発生した場合に生成します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-132">Emit this event when something of note happens in your service that is not a problem.</span></span> <span data-ttu-id="65d7e-133">たとえば、データベースの呼び出しに成功した後にイベントを生成します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-133">For example, you might emit an event after successfully making a call to a database.</span></span>|<span data-ttu-id="65d7e-134">301</span><span class="sxs-lookup"><span data-stu-id="65d7e-134">301</span></span>|  
|<span data-ttu-id="65d7e-135">UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="65d7e-135">UserDefinedWarningOccurred</span></span>|<span data-ttu-id="65d7e-136">このイベントは、後続の処理でエラーになる可能性がある問題が発生した場合に生成します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-136">Emit this event when a problem occurs that may result in a failure in the future.</span></span> <span data-ttu-id="65d7e-137">たとえば、データベースの呼び出しが失敗したものの、冗長なデータ ストアを使用して回復できた場合に警告イベントを生成します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-137">For example, you may emit a warning event when a call to a database fails but you were able to recover by falling back to a redundant data store.</span></span>|<span data-ttu-id="65d7e-138">302</span><span class="sxs-lookup"><span data-stu-id="65d7e-138">302</span></span>|  
|<span data-ttu-id="65d7e-139">UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="65d7e-139">UserDefinedErrorOccurred</span></span>|<span data-ttu-id="65d7e-140">このイベントは、サービスが想定どおりに動作しなかった場合に生成します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-140">Emit this event when your service fails to behave as expected.</span></span> <span data-ttu-id="65d7e-141">たとえば、データベースの呼び出しが失敗し、別の場所からもデータを取得できなかった場合にイベントを生成します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-141">For example, you might emit an event if a call to a database fails and you could not retrieve the data from elsewhere.</span></span>|<span data-ttu-id="65d7e-142">303</span><span class="sxs-lookup"><span data-stu-id="65d7e-142">303</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="65d7e-143">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="65d7e-143">To use this sample</span></span>  
  
1. <span data-ttu-id="65d7e-144">Visual Studio 2012 を使用して、WCFAnalyticTracingExtensibility ソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-144">Using Visual Studio 2012, open the WCFAnalyticTracingExtensibility.sln solution file.</span></span>  
  
2. <span data-ttu-id="65d7e-145">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-145">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="65d7e-146">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-146">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="65d7e-147">Web ブラウザーで、[ **Calculator .svc**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65d7e-147">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="65d7e-148">サービスの WSDL ドキュメントの URI がブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-148">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="65d7e-149">その URI をコピーします。</span><span class="sxs-lookup"><span data-stu-id="65d7e-149">Copy that URI.</span></span>  
  
4. <span data-ttu-id="65d7e-150">WCF テストクライアント (WcfTestClient.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-150">Run the WCF test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="65d7e-151">WCF テストクライアント (WcfTestClient.exe) は、にあり `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe` ます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-151">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span> <span data-ttu-id="65d7e-152">既定の Visual Studio 2012 インストールディレクトリは `C:\Program Files\Microsoft Visual Studio 10.0` です。</span><span class="sxs-lookup"><span data-stu-id="65d7e-152">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>  
  
5. <span data-ttu-id="65d7e-153">WCF テストクライアント内で、[ **ファイル**] を選択し、[ **サービスの追加**] をクリックしてサービスを追加します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-153">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="65d7e-154">入力ボックスにエンドポイントのアドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-154">Add the endpoint address in the input box.</span></span>  
  
6. <span data-ttu-id="65d7e-155">[**OK**] をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-155">Click **OK** to close the dialog.</span></span>  
  
     <span data-ttu-id="65d7e-156">ICalculator サービスは、左側のウィンドウの [ **マイサービスプロジェクト**] の下に追加されます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-156">The ICalculator service is added in the left pane under **My Service Projects**.</span></span>  
  
7. <span data-ttu-id="65d7e-157">イベント ビューアー アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-157">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="65d7e-158">サービスを呼び出す前に、イベントビューアーを開始し、WCF サービスから生成された追跡イベントをイベントログがリッスンしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-158">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>  
  
8. <span data-ttu-id="65d7e-159">[ **スタート** ] メニューから [ **管理ツール**] を選択し、 **イベントビューアー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65d7e-159">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span> <span data-ttu-id="65d7e-160">**分析** ログと **デバッグ** ログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="65d7e-160">Enable the **Analytic** and **Debug** logs.</span></span>  
  
9. <span data-ttu-id="65d7e-161">イベントビューアーのツリービューで、[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="65d7e-162">[ **アプリケーションサーバー-アプリケーション**] を右クリックし、[ **表示**] をクリックして、[ **分析およびデバッグログ] を表示** します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-162">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="65d7e-163">[ **分析とデバッグログを表示** する] オプションがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-163">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span> <span data-ttu-id="65d7e-164">**分析** ログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="65d7e-164">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="65d7e-165">イベントビューアーのツリービューで、[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**]、[ **分析**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-165">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**, and then **Analytic**.</span></span> <span data-ttu-id="65d7e-166">[ **分析** ] を右クリックし、[ **ログを有効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-166">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="65d7e-167">WCF テスト クライアントを使用してサービスをテストします。</span><span class="sxs-lookup"><span data-stu-id="65d7e-167">Test the service using the WCF Test Client.</span></span>  
  
    1. <span data-ttu-id="65d7e-168">WCF テストクライアントで、[ICalculator service] ノードの下の [ **Add ()** ] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="65d7e-168">In the WCF Test Client, double-click **Add()** under the ICalculator service node.</span></span>  
  
         <span data-ttu-id="65d7e-169">**Add ()** メソッドが、右側のペインに2つのパラメーターと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-169">The **Add()** method appears in the right pane with two parameters.</span></span>  
  
    2. <span data-ttu-id="65d7e-170">最初のパラメーターに「2」と入力し、2 番目のパラメーターに「3」と入力します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-170">Type in 2 for the first parameter and 3 for the second parameter.</span></span>  
  
    3. <span data-ttu-id="65d7e-171">[ **呼び出し** ] をクリックしてメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-171">Click **Invoke** to invoke the method.</span></span>  
  
11. <span data-ttu-id="65d7e-172">既に開いている **イベントビューアー** ウィンドウにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="65d7e-172">Go to the **Event Viewer** window that you have already opened.</span></span> <span data-ttu-id="65d7e-173">[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-173">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span>  
  
12. <span data-ttu-id="65d7e-174">[ **分析** ] ノードを右クリックし、[ **更新**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-174">Right-click the **Analytic** node and select **Refresh**.</span></span>  
  
     <span data-ttu-id="65d7e-175">右ペインにイベントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-175">The events appear in the right pane.</span></span>  
  
13. <span data-ttu-id="65d7e-176">ID が 303 のイベントを探してダブルクリックして開き、内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-176">Locate the event with the ID of 303 and double-click it to open it up and inspect its contents.</span></span>  
  
     <span data-ttu-id="65d7e-177">このイベントは、ICalculator サービスのメソッドによって生成され、 `Add()` "2 + 3 = 5" に等しいペイロードがあります。</span><span class="sxs-lookup"><span data-stu-id="65d7e-177">This event was emitted by the `Add()` method of the ICalculator service and has a payload equal to "2+3=5".</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="65d7e-178">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="65d7e-178">To clean up (Optional)</span></span>  
  
1. <span data-ttu-id="65d7e-179">**イベント ビューアー** を開きます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-179">Open **Event Viewer**.</span></span>  
  
2. <span data-ttu-id="65d7e-180">[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーション-サーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-180">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="65d7e-181">[ **分析** ] を右クリックし、[ **ログを無効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-181">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3. <span data-ttu-id="65d7e-182">[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーション-サーバー-アプリケーション**]、[ **分析**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-182">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application-Server-Applications**, and then **Analytic**.</span></span> <span data-ttu-id="65d7e-183">[ **分析** ] を右クリックし、[ **ログの消去**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-183">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4. <span data-ttu-id="65d7e-184">[ **クリア** ] をクリックすると、イベントがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-184">Click **Clear** to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="65d7e-185">既知の問題</span><span class="sxs-lookup"><span data-stu-id="65d7e-185">Known Issue</span></span>  

 <span data-ttu-id="65d7e-186">**イベントビューアー** には、ETW イベントのデコードに失敗する可能性がある既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="65d7e-186">There is a known issue in the **Event Viewer** where it may fail to decode ETW events.</span></span> <span data-ttu-id="65d7e-187">次のエラーメッセージが表示されることがあります。 "ソースからのイベント ID の説明" \<id> Server-Applications が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="65d7e-187">You may see an error message that says: "The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="65d7e-188">このイベントを発生させるコンポーネントがローカル コンピューターにインストールされていないか、インストールが壊れています。</span><span class="sxs-lookup"><span data-stu-id="65d7e-188">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="65d7e-189">ローカルコンピューターにコンポーネントをインストールまたは修復できます。 "</span><span class="sxs-lookup"><span data-stu-id="65d7e-189">You can install or repair the component on the local computer."</span></span> <span data-ttu-id="65d7e-190">このエラーが発生した場合は、[**アクション**] メニューの [**更新**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="65d7e-190">If you encounter this error, select **Refresh** from the **Actions** menu.</span></span> <span data-ttu-id="65d7e-191">これにより、イベントが正常にデコードされます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-191">The event should then decode properly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="65d7e-192">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="65d7e-192">The samples may already be installed on your computer.</span></span> <span data-ttu-id="65d7e-193">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="65d7e-193">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="65d7e-194">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="65d7e-194">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="65d7e-195">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="65d7e-195">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a><span data-ttu-id="65d7e-196">関連項目</span><span class="sxs-lookup"><span data-stu-id="65d7e-196">See also</span></span>

- <span data-ttu-id="65d7e-197">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="65d7e-197">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
