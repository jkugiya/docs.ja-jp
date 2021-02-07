---
description: '詳細情報: 追跡参加要素'
title: 追跡参加要素
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 2fa4edd0f93e72bff0ee4c9a07ad6f6988f3e040
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755175"
---
# <a name="tracking-participants"></a><span data-ttu-id="2088d-103">追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="2088d-103">Tracking Participants</span></span>

<span data-ttu-id="2088d-104">追跡参加要素は、ワークフロー開発者が <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> オブジェクトにアクセスし、そのオブジェクトを処理する機能拡張ポイントです。</span><span class="sxs-lookup"><span data-stu-id="2088d-104">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="2088d-105">には、追跡レコードを Event Tracing for Windows (ETW) イベントとして書き込む標準の追跡参加要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2088d-105">includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="2088d-106">これで要件が満たされない場合は、カスタムの追跡参加要素を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2088d-106">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="2088d-107">追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="2088d-107">Tracking Participants</span></span>  

 <span data-ttu-id="2088d-108">追跡インフラストラクチャを使用すると、送信の追跡レコードにフィルターを適用して、参加要素からレコードのサブセットに定期受信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2088d-108">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="2088d-109">フィルターを適用するメカニズムは、追跡プロファイルを通して行われます。</span><span class="sxs-lookup"><span data-stu-id="2088d-109">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="2088d-110">の Windows Workflow Foundation (WF) に [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] は、追跡レコードを ETW セッションに書き込む追跡参加要素が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2088d-110">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="2088d-111">参加要素は、追跡固有の動作を構成ファイルに追加することによって、ワークフロー サービスで構成されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-111">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="2088d-112">ETW 追跡参加要素を有効にすると、追跡レコードをイベント ビューアーで表示できます。</span><span class="sxs-lookup"><span data-stu-id="2088d-112">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="2088d-113">ETW ベースの追跡用の SDK のサンプルを使用すると、ETW ベースの追跡参加要素を使用した WF の追跡を理解するうえで便利です。</span><span class="sxs-lookup"><span data-stu-id="2088d-113">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="2088d-114">ETW 追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="2088d-114">ETW Tracking Participant</span></span>  

 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="2088d-115">には、追跡レコードを ETW セッションに書き込む ETW 追跡参加要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2088d-115">includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="2088d-116">これは、アプリケーションのパフォーマンスやサーバーのスループットに与える影響を最小限に抑えたまま、非常に効率的な方法で実行されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-116">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="2088d-117">標準の ETW 追跡参加要素を使用する利点は、受信する追跡レコードを他のアプリケーションや Windows イベント ビューアーのシステム ログで表示できることです。</span><span class="sxs-lookup"><span data-stu-id="2088d-117">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="2088d-118">次の例に示すように、標準の ETW 追跡参加要素は Web.config ファイルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-118">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
   <tracking>  
      <profiles>  
        <trackingProfile name="Sample Tracking Profile">  
        ….  
       </trackingProfile>  
      </profiles>  
    </tracking>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="2088d-119">`trackingProfile` または `<etwTracking/>` のように `<etwTracking profileName=""/>` の名前が指定されていない場合、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] と一緒にインストールされている Machine.config ファイルにある既定の追跡プロファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-119">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="2088d-120">Machine.config ファイルでは、既定の追跡プロファイルはワークフロー インスタンスのレコードとエラーに定期受信されています。</span><span class="sxs-lookup"><span data-stu-id="2088d-120">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="2088d-121">ETW では、イベントはプロバイダー ID を使用して ETW セッションに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="2088d-121">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="2088d-122">ETW 追跡参加要素が追跡レコードを ETW に書き込むのに使用するプロバイダー ID は、Web.config ファイルの診断セクション (`<system.serviceModel><diagnostics>` の下) に定義されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-122">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="2088d-123">既定では、プロバイダー ID が指定されていない場合、次の例に示すように ETW 追跡参加要素は既定のプロバイダー ID を使用します。</span><span class="sxs-lookup"><span data-stu-id="2088d-123">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="2088d-124">次の図は、ETW 追跡参加要素を使用した追跡データ フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="2088d-124">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="2088d-125">追跡データは、ETW セッションに到達すると、さまざまな方法でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2088d-125">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="2088d-126">これらのイベントにアクセスする最も便利な方法の 1 つはイベント ビューアーを使用することです。イベント ビューアーは、アプリケーションやサービスのログを表示して追跡する Windows の一般的なツールです。</span><span class="sxs-lookup"><span data-stu-id="2088d-126">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 ![ETW 追跡プロバイダーを使用した追跡データのフロー。](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="2088d-128">追跡参加要素のイベント データ</span><span class="sxs-lookup"><span data-stu-id="2088d-128">Tracking Participant Event Data</span></span>  

 <span data-ttu-id="2088d-129">追跡参加要素は、追跡レコードごとに 1 つのイベントという形式で、ETW セッションに追跡イベント データをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="2088d-129">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="2088d-130">イベントは、100 ～ 199 までの範囲内の ID を使用して識別されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-130">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="2088d-131">追跡参加要素によって出力される追跡イベントレコードの定義については、「 [追跡イベントのリファレンス](tracking-events-reference.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2088d-131">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="2088d-132">ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードのいずれか小さいほうの値に制限されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-132">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="2088d-133">イベントのサイズが ETW のどちらかの制限を超えると、イベントが切り捨てられ、任意の方法でその内容が削除されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-133">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="2088d-134">変数、引数、注釈、およびカスタム データは選択的に削除されません。</span><span class="sxs-lookup"><span data-stu-id="2088d-134">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="2088d-135">切り捨てが発生する場合は、イベント サイズが ETW の制限を超える原因となった値にかかわらず、これらのすべてが切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="2088d-135">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="2088d-136">削除されたデータは、`<item>..<item>` で置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="2088d-136">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="2088d-137">変数、引数、およびカスタムデータ項目の複合型は、クラスを使用して ETW イベントレコードにシリアル化され <xref:System.Runtime.Serialization.NetDataContractSerializer> ます。</span><span class="sxs-lookup"><span data-stu-id="2088d-137">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the <xref:System.Runtime.Serialization.NetDataContractSerializer> class.</span></span> <span data-ttu-id="2088d-138">このクラスでは、シリアル化された XML ストリームに CRL 型情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2088d-138">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="2088d-139">ETW の制限によってペイロード データが切り捨てられると、ETW セッションに送信される追跡レコードの重複が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2088d-139">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="2088d-140">このような状況は、複数のセッションがイベントをリッスンしており、セッションがそのイベントに対して異なるペイロードの制限を持っている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="2088d-140">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="2088d-141">セッションの制限が緩い場合、そのイベントが切り捨てられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2088d-141">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="2088d-142">あるセッションのイベントが切り捨てられ、ETW の参加要素がイベントの送信を 1 回再試行する場合、ETW 追跡参加要素はイベントをリッスンしているセッション数を把握していません。</span><span class="sxs-lookup"><span data-stu-id="2088d-142">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="2088d-143">このような場合、より大きなペイロード サイズを受け入れるように設定されているセッションがそのイベントを 2 回取得します (切り捨てられていないイベントと切り捨てられたイベント)。</span><span class="sxs-lookup"><span data-stu-id="2088d-143">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="2088d-144">すべての ETW セッションが同じバッファー サイズの制限を持つように設定すると、重複を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="2088d-144">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="2088d-145">イベント ビューアーでの ETW 追跡参加要素の追跡データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="2088d-145">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  

 <span data-ttu-id="2088d-146">ETW 追跡参加要素によって ETW セッションに書き込まれたイベントは、イベント ビューアーからアクセスできます (既定のプロバイダー ID を使用している場合)。</span><span class="sxs-lookup"><span data-stu-id="2088d-146">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="2088d-147">これによって、ワークフローが出力した追跡レコードをすぐに表示できます。</span><span class="sxs-lookup"><span data-stu-id="2088d-147">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2088d-148">ETW セッションに出力された追跡レコード イベントでは、100 ～ 199 の範囲のイベント ID を使用します。</span><span class="sxs-lookup"><span data-stu-id="2088d-148">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="2088d-149">イベント ビューアーで追跡レコードの表示を有効にするには</span><span class="sxs-lookup"><span data-stu-id="2088d-149">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1. <span data-ttu-id="2088d-150">イベント ビューアー (EVENTVWR.EXE) を起動します。</span><span class="sxs-lookup"><span data-stu-id="2088d-150">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2. <span data-ttu-id="2088d-151">[ **イベントビューアー]、[アプリケーションとサービスログ]、[Microsoft]、[Windows]、[アプリケーションサーバー-アプリケーション**] のどれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="2088d-151">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3. <span data-ttu-id="2088d-152">右クリックして、[ **表示]、[分析とデバッグログの表示** ] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2088d-152">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="2088d-153">有効でない場合は、ログを選択するとログの横にチェック マークが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-153">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="2088d-154">これにより、 **分析** ログ、 **パフォーマンス** ログ、および **デバッグ** ログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-154">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4. <span data-ttu-id="2088d-155">**分析** ログを右クリックし、[**ログの有効化**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2088d-155">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="2088d-156">ログは %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl ファイルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="2088d-156">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="2088d-157">カスタムの追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="2088d-157">Custom Tracking Participant</span></span>  

 <span data-ttu-id="2088d-158">追跡参加要素 API では、ワークフロー ランタイムが出力する追跡レコードを処理するためのカスタム ロジックを含めることが可能なユーザー指定の追跡参加要素を使用して、追跡ランタイムを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="2088d-158">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="2088d-159">カスタムの追跡参加要素を作成するためには、開発者が `Track` クラスの <xref:System.Activities.Tracking.TrackingParticipant> メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2088d-159">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="2088d-160">このメソッドは、ワークフロー ランタイムによって追跡レコードが出力されるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-160">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="2088d-161">追跡参加要素は <xref:System.Activities.Tracking.TrackingParticipant> クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="2088d-161">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="2088d-162">システムによって提供される <xref:System.Activities.Tracking.EtwTrackingParticipant> は、受信する追跡レコードごとに Event Tracking for Windows (ETW) イベントを出力します。</span><span class="sxs-lookup"><span data-stu-id="2088d-162">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="2088d-163">カスタムの追跡参加要素を作成するには、<xref:System.Activities.Tracking.TrackingParticipant> の派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2088d-163">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="2088d-164">基本的な追跡機能を提供するには、<xref:System.Activities.Tracking.TrackingParticipant.Track%2A> をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="2088d-164">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="2088d-165"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> は、ランタイムによって追跡レコードが送信されるときに呼び出され、必要な方法で処理できます。</span><span class="sxs-lookup"><span data-stu-id="2088d-165"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="2088d-166">次の例では、すべての追跡レコードをコンソール ウィンドウに出力するカスタムの追跡参加要素クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="2088d-166">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="2088d-167">また、<xref:System.Activities.Tracking.TrackingParticipant> および `BeginTrack` メソッドを使用して、非同期で追跡レコードを処理する `EndTrack` オブジェクトを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="2088d-167">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
```csharp  
class ConsoleTrackingParticipant : TrackingParticipant  
{  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        if (record != null)  
        {  
            Console.WriteLine("=================================");  
            Console.WriteLine(record);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="2088d-168">特定の追跡参加要素を使用するには、次の例に示すように、追跡するワークフロー インスタンスに追跡参加要素を登録します。</span><span class="sxs-lookup"><span data-stu-id="2088d-168">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="2088d-169">次の例では、<xref:System.Activities.Statements.Sequence> アクティビティを含む <xref:System.Activities.Statements.WriteLine> アクティビティから成るワークフローを作成します。</span><span class="sxs-lookup"><span data-stu-id="2088d-169">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="2088d-170">`ConsoleTrackingParticipant` が拡張機能に追加され、ワークフローが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2088d-170">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
```csharp  
Activity activity= new Sequence()  
{  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "Hello World."  
        }  
    }  
};  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
  
instance.Extensions.Add(new ConsoleTrackingParticipant());  
  instance.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
            {  
                Console.WriteLine("workflow instance completed, Id = " + instance.Id);  
                resetEvent.Set();  
            };  
            instance.Run();  
            Console.ReadLine();  
```  
  
## <a name="see-also"></a><span data-ttu-id="2088d-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="2088d-171">See also</span></span>

- <span data-ttu-id="2088d-172">[Windows Server App Fabric の監視](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2088d-172">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="2088d-173">[App Fabric を使用したアプリケーションの監視](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2088d-173">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
