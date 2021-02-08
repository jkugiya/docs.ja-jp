---
description: 詳細については、「カスタム追跡」を参照してください。
title: カスタム追跡
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: a06faaaa50a06d613f7183ca018438a8f2b4460b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792558"
---
# <a name="custom-tracking"></a><span data-ttu-id="896e7-103">カスタム追跡</span><span class="sxs-lookup"><span data-stu-id="896e7-103">Custom Tracking</span></span>

<span data-ttu-id="896e7-104">このサンプルでは、カスタムの追跡参加要素を作成し、追跡データをコンソールに出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="896e7-104">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="896e7-105">また、ユーザー定義データが設定された <xref:System.Activities.Tracking.CustomTrackingRecord> オブジェクトを出力する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="896e7-105">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="896e7-106">コンソール ベースの追跡参加要素は、コードで作成された追跡プロファイル オブジェクトを使用して、ワークフローで出力された <xref:System.Activities.Tracking.TrackingRecord> オブジェクトをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="896e7-106">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="896e7-107">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="896e7-107">Sample Details</span></span>

 <span data-ttu-id="896e7-108">Windows Workflow Foundation (WF) は、ワークフローインスタンスの実行を追跡するための追跡インフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="896e7-108">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="896e7-109">追跡ランタイムは、ワークフロー ライフサイクルに関連するイベント、ワークフロー アクティビティのイベント、およびカスタム追跡イベントを出力するワークフロー インスタンスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="896e7-109">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="896e7-110">次の表で、追跡インフラストラクチャの主要コンポーネントの詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="896e7-110">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="896e7-111">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="896e7-111">Component</span></span>|<span data-ttu-id="896e7-112">説明</span><span class="sxs-lookup"><span data-stu-id="896e7-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="896e7-113">追跡ランタイム</span><span class="sxs-lookup"><span data-stu-id="896e7-113">Tracking runtime</span></span>|<span data-ttu-id="896e7-114">追跡レコードを出力するためのインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="896e7-114">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="896e7-115">追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="896e7-115">Tracking participants</span></span>|<span data-ttu-id="896e7-116">追跡レコードを処理します。</span><span class="sxs-lookup"><span data-stu-id="896e7-116">Consumes the tracking records.</span></span> <span data-ttu-id="896e7-117">.NET Framework 4 には、追跡レコードを Windows イベントトレーシング (ETW) イベントとして書き込む追跡参加要素が付属しています。</span><span class="sxs-lookup"><span data-stu-id="896e7-117">.NET Framework 4 ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="896e7-118">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="896e7-118">Tracking profile</span></span>|<span data-ttu-id="896e7-119">ワークフロー インスタンスから出力された追跡レコードのサブセットを追跡参加要素から定期受信するためのフィルター機構。</span><span class="sxs-lookup"><span data-stu-id="896e7-119">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="896e7-120">次の表で、ワークフロー ランタイムが出力する追跡レコードの詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="896e7-120">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="896e7-121">追跡レコード</span><span class="sxs-lookup"><span data-stu-id="896e7-121">Tracking Record</span></span>|<span data-ttu-id="896e7-122">説明</span><span class="sxs-lookup"><span data-stu-id="896e7-122">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="896e7-123">ワークフロー インスタンスの追跡レコード</span><span class="sxs-lookup"><span data-stu-id="896e7-123">Workflow instance tracking records.</span></span>|<span data-ttu-id="896e7-124">ワークフロー インスタンスのライフサイクルを表します。</span><span class="sxs-lookup"><span data-stu-id="896e7-124">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="896e7-125">たとえば、ワークフローの開始時または完了時にインスタンス レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="896e7-125">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="896e7-126">アクティビティ状態の追跡レコード</span><span class="sxs-lookup"><span data-stu-id="896e7-126">Activity state Tracking Records.</span></span>|<span data-ttu-id="896e7-127">アクティビティの実行状況を詳しく記録します。</span><span class="sxs-lookup"><span data-stu-id="896e7-127">Details activity execution.</span></span> <span data-ttu-id="896e7-128">これらのレコードは、アクティビティをスケジュールしたとき、アクティビティが完了したとき、エラーがスローされたときなど、ワークフロー アクティビティの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="896e7-128">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="896e7-129">ブックマーク再開レコード</span><span class="sxs-lookup"><span data-stu-id="896e7-129">Bookmark resumption record.</span></span>|<span data-ttu-id="896e7-130">ワークフロー インスタンス内のブックマークが再開されたときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="896e7-130">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="896e7-131">カスタム追跡レコード</span><span class="sxs-lookup"><span data-stu-id="896e7-131">Custom Tracking Records.</span></span>|<span data-ttu-id="896e7-132">ワークフロー作成者はカスタム追跡レコードを作成し、カスタム アクティビティ内で出力できます。</span><span class="sxs-lookup"><span data-stu-id="896e7-132">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="896e7-133">追跡参加要素は、追跡プロファイルを使用して、出力された <xref:System.Activities.Tracking.TrackingRecord> オブジェクトのサブセットを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="896e7-133">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="896e7-134">追跡プロファイルには、特定の追跡レコード タイプを定期受信するための追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="896e7-134">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="896e7-135">追跡プロファイルは、コードで指定したり、構成で指定したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="896e7-135">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="896e7-136">カスタムの追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="896e7-136">Custom Tracking Participant</span></span>

 <span data-ttu-id="896e7-137">追跡参加要素 API では、ワークフロー ランタイムが出力する <xref:System.Activities.Tracking.TrackingRecord> オブジェクトを処理するためのカスタム ロジックを含めることが可能なユーザー指定の追跡参加要素を使用して、追跡ランタイムを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="896e7-137">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="896e7-138">追跡参加要素を書き込むには、ユーザーは <xref:System.Activities.Tracking.TrackingParticipant> を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="896e7-138">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="896e7-139">具体的には、カスタム参加要素で <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="896e7-139">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="896e7-140">このメソッドは、ワークフロー ランタイムによって <xref:System.Activities.Tracking.TrackingRecord> が出力されるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="896e7-140">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="896e7-141">完全な追跡参加要素は、ConsoleTrackingParticipant.cs ファイルに実装されます。</span><span class="sxs-lookup"><span data-stu-id="896e7-141">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.</span></span> <span data-ttu-id="896e7-142">カスタム追跡参加要素のメソッドを次のコード例に示し <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="896e7-142">The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

```csharp
protected override void Track(TrackingRecord record, TimeSpan timeout)
{
    ...
    WorkflowInstanceRecord workflowInstanceRecord = record as WorkflowInstanceRecord;
    if (workflowInstanceRecord != null)
    {
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " Workflow InstanceID: {0} Workflow instance state: {1}",
            record.InstanceId, workflowInstanceRecord.State));
    }

    ActivityStateRecord activityStateRecord = record as ActivityStateRecord;
    if (activityStateRecord != null)
    {
        IDictionary<String, object> variables = activityStateRecord.Variables;
        StringBuilder vars = new StringBuilder();

        if (variables.Count > 0)
        {
            vars.AppendLine("\n\tVariables:");
            foreach (KeyValuePair<string, object> variable in variables)
            {
                vars.AppendLine(String.Format(
                    "\t\tName: {0} Value: {1}", variable.Key, variable.Value));
            }
        }
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " :Activity DisplayName: {0} :ActivityInstanceState: {1} {2}",
                activityStateRecord.Activity.Name, activityStateRecord.State,
            ((variables.Count > 0) ? vars.ToString() : String.Empty)));
    }

    CustomTrackingRecord customTrackingRecord = record as CustomTrackingRecord;

    if ((customTrackingRecord != null) && (customTrackingRecord.Data.Count > 0))
    {
        ...
    }
    Console.WriteLine();

}
```

 <span data-ttu-id="896e7-143">次のコード例では、ワークフロー呼び出しの起動者にコンソール参加要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="896e7-143">The following code example adds the console participant to the workflow invoker.</span></span>

```csharp
ConsoleTrackingParticipant customTrackingParticipant = new ConsoleTrackingParticipant()
{
    ...
    // The tracking profile is set here, refer to Program.CS
...
}

WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
```

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="896e7-144">カスタム追跡レコードの出力</span><span class="sxs-lookup"><span data-stu-id="896e7-144">Emitting Custom Tracking Records</span></span>

 <span data-ttu-id="896e7-145">このサンプルでは、カスタム ワークフロー アクティビティから <xref:System.Activities.Tracking.CustomTrackingRecord> オブジェクトを出力する機能も示します。</span><span class="sxs-lookup"><span data-stu-id="896e7-145">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

- <span data-ttu-id="896e7-146"><xref:System.Activities.Tracking.CustomTrackingRecord> オブジェクトは、レコードと一緒に出力する必要があるユーザー定義データを使用して作成および設定します。</span><span class="sxs-lookup"><span data-stu-id="896e7-146">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

- <span data-ttu-id="896e7-147">は <xref:System.Activities.Tracking.CustomTrackingRecord> 、の track メソッドを呼び出すことによって出力され <xref:System.Activities.ActivityContext> ます。</span><span class="sxs-lookup"><span data-stu-id="896e7-147">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="896e7-148">次の例では、カスタム アクティビティ内で <xref:System.Activities.Tracking.CustomTrackingRecord> オブジェクトを出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="896e7-148">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

```csharp
// Create the Custom Tracking Record
CustomTrackingRecord customRecord = new CustomTrackingRecord("OrderIn")
{
    Data =
    {
        {"OrderId", 200},
        {"OrderDate", "20 Aug 2001"}
    }
};

// Emit custom tracking record
context.Track(customRecord);
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="896e7-149">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="896e7-149">To use this sample</span></span>

1. <span data-ttu-id="896e7-150">Visual Studio 2010 を使用して、CustomTrackingSample .sln ソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="896e7-150">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="896e7-151">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="896e7-151">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="896e7-152">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="896e7-152">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="896e7-153">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="896e7-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="896e7-154">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="896e7-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="896e7-155">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="896e7-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="896e7-156">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="896e7-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="896e7-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="896e7-157">See also</span></span>

- <span data-ttu-id="896e7-158">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="896e7-158">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
