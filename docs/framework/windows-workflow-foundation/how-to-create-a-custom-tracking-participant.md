---
description: '詳細については、「方法: カスタム追跡参加要素を作成する」を参照してください。'
title: '方法: カスタム追跡参加要素を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 8b435ac110d286d0582700289079459cca3cf979
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777841"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="60de6-103">方法: カスタム追跡参加要素を作成する</span><span class="sxs-lookup"><span data-stu-id="60de6-103">How to: Create a Custom Tracking Participant</span></span>

<span data-ttu-id="60de6-104">ワークフロー追跡により、ワークフロー実行の状態が視覚的に示されます。</span><span class="sxs-lookup"><span data-stu-id="60de6-104">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="60de6-105">ワークフロー ランタイムによって、ワークフローのライフサイクル イベント、アクティビティのライフサイクル イベント、ブックマークの再開、およびエラーについて説明する追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="60de6-105">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="60de6-106">これらの追跡レコードは、追跡参加要素によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="60de6-106">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="60de6-107">Windows Workflow Foundation (WF) には、追跡レコードを Windows イベントトレーシング (ETW) イベントとして書き込む標準の追跡参加要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="60de6-107">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="60de6-108">これで要件が満たされない場合は、カスタムの追跡参加要素を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="60de6-108">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="60de6-109">チュートリアルのこの手順では、`WriteLine` アクティビティの出力をキャプチャするカスタム追跡参加要素と追跡プロファイルを作成して、ユーザーに表示できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="60de6-109">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="60de6-110">カスタム追跡参加要素を作成するには</span><span class="sxs-lookup"><span data-stu-id="60de6-110">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="60de6-111">**ソリューションエクスプローラー** で [ **NumberGuessWorkflowHost** ] を右クリックし、[**追加**]、[**クラス**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="60de6-111">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="60de6-112">`StatusTrackingParticipant`[**名前**] ボックスに「」と入力し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60de6-112">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="60de6-113">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="60de6-113">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="60de6-114">`StatusTrackingParticipant` クラスを変更して、`TrackingParticipant` から継承されるようにします。</span><span class="sxs-lookup"><span data-stu-id="60de6-114">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4. <span data-ttu-id="60de6-115">次の `Track` メソッド オーバーライドを追加します。</span><span class="sxs-lookup"><span data-stu-id="60de6-115">Add the following `Track` method override.</span></span> <span data-ttu-id="60de6-116">追跡レコードには、いくつかの種類があります。</span><span class="sxs-lookup"><span data-stu-id="60de6-116">There are several different types of tracking records.</span></span> <span data-ttu-id="60de6-117">ここでは、アクティビティ追跡レコードに含まれる `WriteLine` アクティビティの出力に注目します。</span><span class="sxs-lookup"><span data-stu-id="60de6-117">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="60de6-118">`TrackingRecord` が `ActivityTrackingRecord` アクティビティの `WriteLine` である場合は、ワークフローの `Text` に基づいた名前の付いたファイルに `WriteLine` の `InstanceId` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="60de6-118">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="60de6-119">このチュートリアルでは、ファイルはホスト アプリケーションの現在のフォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="60de6-119">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="60de6-120">追跡プロファイルを指定しない場合は、既定の追跡プロファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="60de6-120">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="60de6-121">既定の追跡プロファイルを使用する場合は、すべての `ActivityStates` に関する追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="60de6-121">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="60de6-122">ここでは、`WriteLine` アクティビティのライフサイクル中に 1 回だけテキストをキャプチャする必要があるため、`ActivityStates.Executing` 状態からテキストを抽出するだけです。</span><span class="sxs-lookup"><span data-stu-id="60de6-122">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="60de6-123">追跡 [プロファイルを作成して追跡参加要素を登録するに](#to-create-the-tracking-profile-and-register-the-tracking-participant)は、追跡 `WriteLine` レコードのみが出力されることを指定する追跡プロファイルを作成し `ActivityStates.Executing` ます。</span><span class="sxs-lookup"><span data-stu-id="60de6-123">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="60de6-124">追跡プロファイルを作成して追跡参加要素を登録するには</span><span class="sxs-lookup"><span data-stu-id="60de6-124">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="60de6-125">**ソリューションエクスプローラー** で [ **WorkflowHostForm** ] を右クリックし、[**コードの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="60de6-125">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="60de6-126">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="60de6-126">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="60de6-127">ワークフロー拡張機能に `ConfigureWorkflowApplication` を追加するコードの直後で、ワークフロー ライフサイクル ハンドラーの前に、`StringWriter` に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="60de6-127">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     <span data-ttu-id="60de6-128">この追跡プロファイルでは、`WriteLine` 状態の `Executing` アクティビティのアクティビティ状態レコードのみがカスタム追跡参加要素に出力されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="60de6-128">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="60de6-129">このコードを追加した後、`ConfigureWorkflowApplication` の先頭は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="60de6-129">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="60de6-130">追跡情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="60de6-130">To display the tracking information</span></span>  
  
1. <span data-ttu-id="60de6-131">**ソリューションエクスプローラー** で [ **WorkflowHostForm** ] を右クリックし、[**コードの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="60de6-131">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="60de6-132">`InstanceId_SelectedIndexChanged` ハンドラーで、ステータス ウィンドウをクリアするコードの直後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="60de6-132">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     <span data-ttu-id="60de6-133">ワークフローの一覧で新しいワークフローを選択すると、そのワークフローの追跡レコードがステータス ウィンドウに読み込まれて表示されます。</span><span class="sxs-lookup"><span data-stu-id="60de6-133">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="60de6-134">完成した `InstanceId_SelectedIndexChanged` ハンドラーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="60de6-134">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="60de6-135">アプリケーションをビルドして実行するには</span><span class="sxs-lookup"><span data-stu-id="60de6-135">To build and run the application</span></span>  
  
1. <span data-ttu-id="60de6-136">Ctrl キーと Shift キーを押しながら B キーを押してアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="60de6-136">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="60de6-137">Ctrl キーを押しながら F5 キーを押してアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="60de6-137">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="60de6-138">推測ゲームの範囲と開始するワークフローの種類を選択し、[ **新しいゲーム**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60de6-138">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="60de6-139">[ **推定** ] ボックスに推測を入力し、[ **ジャンプ** ] をクリックして推測を送信します。</span><span class="sxs-lookup"><span data-stu-id="60de6-139">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="60de6-140">ワークフローの状態がステータス ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="60de6-140">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="60de6-141">この出力は、`WriteLine` アクティビティからキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="60de6-141">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="60de6-142">[ **ワークフローインスタンス Id** ] コンボボックスから別のワークフローに切り替え、現在のワークフローの状態が削除されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="60de6-142">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="60de6-143">以前のワークフローに戻して、次の例のように、状態が復元されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="60de6-143">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="60de6-144">追跡が有効になる前に開始されたワークフローに切り替えた場合、状態は表示されません。</span><span class="sxs-lookup"><span data-stu-id="60de6-144">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="60de6-145">ただし、推定値を追加すると、この時点では追跡が有効になっているため、その状態が保存されます。</span><span class="sxs-lookup"><span data-stu-id="60de6-145">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    > [!NOTE]
    > <span data-ttu-id="60de6-146">この情報は、乱数の範囲を決定する場合に役立ちますが、これまでに作成された推定値に関する情報を含んでいません。</span><span class="sxs-lookup"><span data-stu-id="60de6-146">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="60de6-147">この情報については、次の手順「 [方法: ワークフローの複数のバージョンを side-by-side でホストする](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60de6-147">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="60de6-148">ワークフロー インスタンス ID を書き留め、ゲームを最後まで実行します。</span><span class="sxs-lookup"><span data-stu-id="60de6-148">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="60de6-149">エクスプローラーを開き、 **NumberGuessWorkflowHost\bin\debug** フォルダー (またはプロジェクトの設定によっては **bin\release** ) に移動します。</span><span class="sxs-lookup"><span data-stu-id="60de6-149">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="60de6-150">プロジェクトの実行可能ファイルに加え、GUID ファイル名が付いたファイルがあることに注意します。</span><span class="sxs-lookup"><span data-stu-id="60de6-150">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="60de6-151">前の手順で完了したワークフローのワークフロー インスタンス ID に対応するファイルを特定してメモ帳で開きます。</span><span class="sxs-lookup"><span data-stu-id="60de6-151">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="60de6-152">追跡情報は、次のような情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="60de6-152">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="60de6-153">この追跡データには、ユーザーの推定値だけでなく、ワークフローの最後の推定値に関する情報も含まれていません。</span><span class="sxs-lookup"><span data-stu-id="60de6-153">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="60de6-154">これは、追跡情報がワークフローからの `WriteLine` 出力のみで構成されており、表示される最後のメッセージがワークフロー完了後に `Completed` ハンドラーから表示されるためです。</span><span class="sxs-lookup"><span data-stu-id="60de6-154">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="60de6-155">チュートリアルの次の手順「 [方法: ワークフローの複数のバージョンを side-by-side にホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)する」では、 `WriteLine` ユーザーの推定を表示するように既存のアクティビティを変更し、 `WriteLine` 最終結果を表示する追加のアクティビティを追加します。</span><span class="sxs-lookup"><span data-stu-id="60de6-155">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="60de6-156">これらの変更を統合した後は、「 [方法: ワークフローの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) する」では、ワークフローの複数のバージョンを同時にホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="60de6-156">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
