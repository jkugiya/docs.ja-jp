---
description: '詳細については、「方法: 複数のバージョンのワークフローをサイドバイサイドでホストする」を参照してください。'
title: '方法: ワークフローの複数のバージョンを同時にホストする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 7662aa6375467e6bc283e1e743488439c8bf087a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777672"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="b76a8-103">方法: ワークフローの複数のバージョンを同時にホストする</span><span class="sxs-lookup"><span data-stu-id="b76a8-103">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>

<span data-ttu-id="b76a8-104">`WorkflowIdentity` を使用すると、ワークフロー アプリケーションの開発者は、名前とバージョンをワークフロー定義に関連付け、永続化されたワークフロー インスタンスにこの情報を関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-104">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="b76a8-105">この ID 情報は、ワークフロー アプリケーションの開発者がワークフロー定義の複数のバージョンの side-by-side 実行などのシナリオを有効にするために使用できます。また、動的更新などの他の機能の基礎となります。</span><span class="sxs-lookup"><span data-stu-id="b76a8-105">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="b76a8-106">チュートリアルのこの手順では、`WorkflowIdentity` を使用してワークフローの複数のバージョンを同時にホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-106">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="b76a8-107">このトピックの内容</span><span class="sxs-lookup"><span data-stu-id="b76a8-107">In this topic</span></span>

<span data-ttu-id="b76a8-108">チュートリアルのこの手順では、追加情報を提供するようにワークフローの `WriteLine` アクティビティが変更され、新しい `WriteLine` アクティビティが追加されます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="b76a8-109">元のワークフロー アセンブリのコピーが格納され、ホスト アプリケーションは、元のワークフローと更新されたワークフローの両方を同時に実行できるように更新されます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>

- [<span data-ttu-id="b76a8-110">NumberGuessWorkflowActivities プロジェクトのコピーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [<span data-ttu-id="b76a8-111">ワークフローを更新するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-111">To update the workflows</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [<span data-ttu-id="b76a8-112">StateMachine ワークフローを更新するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-112">To update the StateMachine workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [<span data-ttu-id="b76a8-113">フローチャート ワークフローを更新するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-113">To update the Flowchart workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [<span data-ttu-id="b76a8-114">シーケンシャル ワークフローを更新するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-114">To update the Sequential workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [<span data-ttu-id="b76a8-115">以前のワークフロー バージョンを含むように WorkflowVersionMap を更新するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="b76a8-116">アプリケーションをビルドして実行するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-116">To build and run the application</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> <span data-ttu-id="b76a8-117">このトピックの手順を実行する前に、アプリケーションを実行し、各種類のワークフローをいくつか開始して、ワークフローごとに 1 つまたは 2 つの推定値を作成します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="b76a8-118">これらの永続化されたワークフローは、この手順で使用します。次の手順では、 [実行中のワークフローインスタンスの定義を更新](how-to-update-the-definition-of-a-running-workflow-instance.md)します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

### <a name="to-make-a-copy-of-the-numberguessworkflowactivities-project"></a><a name="BKMK_BackupCopy"></a> <span data-ttu-id="b76a8-119">NumberGuessWorkflowActivities プロジェクトのコピーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-119">To make a copy of the NumberGuessWorkflowActivities project</span></span>

1. <span data-ttu-id="b76a8-120">**WF45GettingStartedTutorial** ソリューションが開いていない場合は、Visual Studio 2012 で開きます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-120">Open the **WF45GettingStartedTutorial** solution in Visual Studio 2012 if it is not open.</span></span>

2. <span data-ttu-id="b76a8-121">Ctrl + Shift + B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b76a8-121">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="b76a8-122">**WF45GettingStartedTutorial** ソリューションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-122">Close the **WF45GettingStartedTutorial** solution.</span></span>

4. <span data-ttu-id="b76a8-123">エクスプローラーを開き、チュートリアルのソリューション ファイルおよびプロジェクト フォルダーが格納されているフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-123">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>

5. <span data-ttu-id="b76a8-124">**NumberGuessWorkflowHost** および **NumberGuessWorkflowActivities** と同じフォルダーに、**以前のバージョン** という名前の新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-124">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="b76a8-125">このフォルダーは、チュートリアルの以降の手順で使用されるワークフローの異なるバージョンを含むアセンブリを格納するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-125">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>

6. <span data-ttu-id="b76a8-126">**NumberGuessWorkflowActivities\bin\debug** フォルダー (または、プロジェクトの設定によっては **bin\release** ) に移動します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-126">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="b76a8-127">**NumberGuessWorkflowActivities.dll** をコピーして、[**以前のバージョン**] フォルダーに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-127">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>

7. <span data-ttu-id="b76a8-128">[**以前のバージョン**] フォルダー内の **NumberGuessWorkflowActivities.dll** の名前を **NumberGuessWorkflowActivities_v1.dll** に変更します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-128">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b76a8-129">このトピックの手順では、ワークフローの複数のバージョンを格納するためのアセンブリを管理する 1 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-129">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="b76a8-130">アセンブリに厳密な名前を付けてグローバル アセンブリ キャッシュに登録するなど、他の方法も使用できます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-130">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>

8. <span data-ttu-id="b76a8-131">**NumberGuessWorkflowHost**、 **NumberGuessWorkflowActivities**、および新しく追加した **以前のバージョン** のフォルダーと同じフォルダーに、 **NumberGuessWorkflowActivities_du** という名前の新しいフォルダーを作成し、 **NumberGuessWorkflowActivities** フォルダーのすべてのファイルとサブフォルダーを新しい **NumberGuessWorkflowActivities_du** フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b76a8-131">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="b76a8-132">アクティビティの初期バージョンのプロジェクトのこのバックアップコピーは、 [「方法: 実行中のワークフローインスタンスの定義を更新する](how-to-update-the-definition-of-a-running-workflow-instance.md)」で使用されています。</span><span class="sxs-lookup"><span data-stu-id="b76a8-132">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

9. <span data-ttu-id="b76a8-133">Visual Studio 2012 で **WF45GettingStartedTutorial** ソリューションを再度開きます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-133">Re-open the **WF45GettingStartedTutorial** solution in Visual Studio 2012.</span></span>

### <a name="to-update-the-workflows"></a><a name="BKMK_UpdateWorkflows"></a> <span data-ttu-id="b76a8-134">ワークフローを更新するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-134">To update the workflows</span></span>

<span data-ttu-id="b76a8-135">ここでは、ワークフロー定義が更新されます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-135">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="b76a8-136">ユーザーの推定値についてフィードバックを返す 2 つの `WriteLine` アクティビティが更新され、新しい `WriteLine` アクティビティが追加されます。新しいアクティビティは、数値が推定されるとゲームに関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-136">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>

#### <a name="to-update-the-statemachine-workflow"></a><a name="BKMK_UpdateStateMachine"></a> <span data-ttu-id="b76a8-137">StateMachine ワークフローを更新するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-137">To update the StateMachine workflow</span></span>

1. <span data-ttu-id="b76a8-138">**ソリューションエクスプローラー** の **NumberGuessWorkflowActivities** プロジェクトで、 **statemachinenumberguessworkflow.xaml** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b76a8-138">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="b76a8-139">ステートマシンで、[推測された **不適切** な切り替え] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b76a8-139">Double-click the **Guess Incorrect** transition on the state machine.</span></span>

3. <span data-ttu-id="b76a8-140">`Text` アクティビティで、左端の `WriteLine` の `If` を更新します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-140">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. <span data-ttu-id="b76a8-141">`Text` アクティビティで、右端の `WriteLine` の `If` を更新します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-141">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. <span data-ttu-id="b76a8-142">ワークフローデザイナーの上部にある階層リンク表示で [ **StateMachine** ] をクリックして、ワークフローデザイナーの全体的なステートマシンビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="b76a8-142">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>

6. <span data-ttu-id="b76a8-143">ステートマシンの [ **推定** ] の [正しい切り替え] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b76a8-143">Double-click the **Guess Correct** transition on the state machine.</span></span>

7. <span data-ttu-id="b76a8-144">**ツールボックス** の [**プリミティブ**] セクションから **WriteLine** アクティビティをドラッグし、遷移の [**ここにアクションアクティビティをドロップ** します] ラベルの上にドロップします。</span><span class="sxs-lookup"><span data-stu-id="b76a8-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>

8. <span data-ttu-id="b76a8-145">`Text` プロパティ ボックスに、次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-145">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="to-update-the-flowchart-workflow"></a><a name="BKMK_UpdateFlowchart"></a> <span data-ttu-id="b76a8-146">フローチャートワークフローを更新するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-146">To update the Flowchart workflow</span></span>

1. <span data-ttu-id="b76a8-147">**ソリューションエクスプローラー** の **NumberGuessWorkflowActivities** プロジェクトで、 **flowchartnumberguessworkflow.xaml** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b76a8-147">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="b76a8-148">左端の `Text` アクティビティの `WriteLine` を更新します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-148">Update the `Text` of the left-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="b76a8-149">右端の `Text` アクティビティの `WriteLine` を更新します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-149">Update the `Text` of the right-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="b76a8-150">**ツールボックス** の [**プリミティブ**] セクションから **WriteLine** アクティビティをドラッグし、最上位のアクションのドロップポイントにドロップし `True` `FlowDecision` ます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-150">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="b76a8-151">`WriteLine` アクティビティがフローチャートに追加され、`True` の `FlowDecision` アクションにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-151">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>

5. <span data-ttu-id="b76a8-152">`Text` プロパティ ボックスに、次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-152">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="to-update-the-sequential-workflow"></a><a name="BKMK_UpdateSequential"></a> <span data-ttu-id="b76a8-153">シーケンシャルワークフローを更新するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-153">To update the Sequential workflow</span></span>

1. <span data-ttu-id="b76a8-154">**ソリューションエクスプローラー** の **NumberGuessWorkflowActivities** プロジェクトで、 **sequentialnumberguessworkflow.xaml** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="b76a8-154">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="b76a8-155">`Text` アクティビティで、左端の `WriteLine` の `If` を更新します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-155">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="b76a8-156">`Text` アクティビティで、右端の `WriteLine` アクティビティの `If` を更新します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-156">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="b76a8-157">**ツールボックス** の [**プリミティブ**] セクションから **writeline** アクティビティをドラッグし、 **dowhile** アクティビティの後にドロップして、 **writeline** がルートアクティビティの最後のアクティビティになるようにし `Sequence` ます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-157">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>

5. <span data-ttu-id="b76a8-158">`Text` プロパティ ボックスに、次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-158">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="to-update-workflowversionmap-to-include-the-previous-workflow-versions"></a><a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="b76a8-159">以前のワークフローバージョンを含むように WorkflowVersionMap を更新するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-159">To update WorkflowVersionMap to include the previous workflow versions</span></span>

1. <span data-ttu-id="b76a8-160">**NumberGuessWorkflowHost** プロジェクトの下にある **WorkflowVersionMap.cs** (または **workflowversionmap .vb**) をダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-160">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

2. <span data-ttu-id="b76a8-161">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-161">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. <span data-ttu-id="b76a8-162">既存の 3 つのワークフロー ID 宣言の直後に、新しいワークフロー ID を 3 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-162">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="b76a8-163">これらの新しい `v1` ワークフロー ID は、更新が行われる前に開始されたワークフローに対して正しいワークフロー定義を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-163">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 Identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;
    ```

4. <span data-ttu-id="b76a8-164">`WorkflowVersionMap` コンストラクターで、3 つの現在のワークフロー ID の `Version` プロパティを `2.0.0.0` に更新します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-164">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>

    ```vb
    'Add the current workflow version identities.
    StateMachineNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    SequentialNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
    ```

    ```csharp
    // Add the current workflow version identities.
    StateMachineNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    SequentialNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
    ```

    <span data-ttu-id="b76a8-165">ワークフローの現在のバージョンをディクショナリに追加するコードでは、プロジェクトで参照されている現在のバージョンを使用しているため、ワークフロー定義を初期化するコードを更新する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b76a8-165">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>

5. <span data-ttu-id="b76a8-166">コンストラクターで、現在のバージョンをディクショナリに追加するコードの直後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-166">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>

    ```vb
    'Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }
    ```

    ```csharp
    // Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };
    ```

    <span data-ttu-id="b76a8-167">これらのワークフロー ID は、対応するワークフロー定義の最初のバージョンに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-167">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>

6. <span data-ttu-id="b76a8-168">次に、ワークフロー定義の最初のバージョンを含むアセンブリを読み込み、対応するワークフロー定義を作成してそのディクショナリに追加します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-168">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>

    ```vb
    'Add the previous version workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v1 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Add the previous version workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v1 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

    <span data-ttu-id="b76a8-169">次の例では、更新された `WorkflowVersionMap` クラス全体を示します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-169">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 Identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
        }
    }
    ```

### <a name="to-build-and-run-the-application"></a><a name="BKMK_BuildAndRun"></a> <span data-ttu-id="b76a8-170">アプリケーションをビルドして実行するには</span><span class="sxs-lookup"><span data-stu-id="b76a8-170">To build and run the application</span></span>

1. <span data-ttu-id="b76a8-171">Ctrl キーと Shift キーを押しながら B キーを押してアプリケーションをビルドし、Ctrl キーを押しながら F5 キーを押して起動します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-171">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>

2. <span data-ttu-id="b76a8-172">[ **新しいゲーム**] をクリックして、新しいワークフローを開始します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-172">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="b76a8-173">ワークフローのバージョンは、ステータス ウィンドウの下に表示され、関連付けられた `WorkflowIdentity` から更新後のバージョンを反映します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-173">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="b76a8-174">完了時にワークフローの追跡ファイルを確認できるように `InstanceId` を書き留めておき、ゲームが完了するまで推定値を入力します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-174">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="b76a8-175">`WriteLine` アクティビティに対する更新に基づき、ステータス ウィンドウに示される情報に、ユーザーの推定値がどのように表示されるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-175">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    Congratulations, you guessed the number in 4 turns.
    ```

    > [!NOTE]
    > <span data-ttu-id="b76a8-176">`WriteLine` アクティビティから更新されたテキストは表示されますが、このトピックで追加された最後の `WriteLine` アクティビティの出力は表示されません。</span><span class="sxs-lookup"><span data-stu-id="b76a8-176">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="b76a8-177">これは、ステータス ウィンドウが `PersistableIdle` ハンドラーによって更新されるためです。</span><span class="sxs-lookup"><span data-stu-id="b76a8-177">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="b76a8-178">ワークフローは完了し、最後のアクティビティの後にアイドル状態にならないため、`PersistableIdle` ハンドラーは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="b76a8-178">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="b76a8-179">ただし、`Completed` ハンドラーによって同様のメッセージがステータス ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-179">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="b76a8-180">必要に応じて、コードを `Completed` ハンドラーに追加し、`StringWriter` からテキストを抽出してステータス ウィンドウに表示できます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-180">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>

3. <span data-ttu-id="b76a8-181">エクスプローラーを開き、 **NumberGuessWorkflowHost\bin\debug** フォルダー (プロジェクトの設定によっては **bin\release** ) に移動し、完了したワークフローに対応するメモ帳を使用して追跡ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-181">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="b76a8-182">をメモしていない場合は、 `InstanceId` Windows エクスプローラーの [ **更新日時** ] 情報を使用して、正しい追跡ファイルを特定できます。</span><span class="sxs-lookup"><span data-stu-id="b76a8-182">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    <span data-ttu-id="b76a8-183">更新された `WriteLine` の出力は、このトピックで追加した `WriteLine` の出力を含む追跡ファイル内に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b76a8-183">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>

4. <span data-ttu-id="b76a8-184">数値推測アプリケーションに戻り、更新が行われる前に開始したワークフローのうち 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-184">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="b76a8-185">現在選択されているワークフローのバージョンを特定するには、ステータス ウィンドウの下に表示されるバージョン情報を確認します。</span><span class="sxs-lookup"><span data-stu-id="b76a8-185">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="b76a8-186">いくつかの推定値を入力し、ステータスの更新が前のバージョンからの `WriteLine` アクティビティの出力と一致しており、ユーザーの推定値が含まれていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b76a8-186">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="b76a8-187">これらのワークフローでは、`WriteLine` の更新を含まない以前のワークフロー定義を使用しているためです。</span><span class="sxs-lookup"><span data-stu-id="b76a8-187">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>

    <span data-ttu-id="b76a8-188">次の手順「 [方法: 実行中のワークフローインスタンスの定義を更新する](how-to-update-the-definition-of-a-running-workflow-instance.md)」では、実行中のワークフローインスタンスが `v1` 更新され、インスタンスとして新しい機能が含まれるようになりました `v2` 。</span><span class="sxs-lookup"><span data-stu-id="b76a8-188">In the next step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
