---
title: 'チュートリアル: Windows サービス アプリを作成する'
description: このチュートリアルでは、イベント ログにメッセージを書き込む Windows サービス アプリを Visual Studio で作成します。 機能の追加、状態の設定、インストーラの追加などを行います。
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
ms.openlocfilehash: b6e4937b71c50f887a7eb784bc9106360a05fdc2
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259799"
---
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="06824-104">チュートリアル: Windows サービス アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="06824-104">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="06824-105">この記事では、イベント ログにメッセージを書き込む Windows サービス アプリを Visual Studio で作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="06824-105">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="06824-106">サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="06824-106">Create a service</span></span>

<span data-ttu-id="06824-107">最初に、プロジェクトを作成し、サービスが正しく機能するために必要な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="06824-107">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="06824-108">Visual Studio の **[ファイル]** メニューで **[新規]**  >  **[プロジェクト]** を選択して (または **Ctrl**+**Shift**+**N** キーを押して)、 **[新しいプロジェクト]** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="06824-108">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="06824-109">**[Windows サービス (.NET Framework)]** プロジェクト テンプレートに移動して選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-109">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="06824-110">これを見つけるには、 **[インストール済み]** の **[Visual C#]** または **[Visual Basic]** を展開し、 **[Windows デスクトップ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-110">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="06824-111">または、右上の検索ボックスに「*Windows サービス*」と入力して **Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="06824-111">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Visual Studio の [新しいプロジェクト] ダイアログの Windows サービス アプリ テンプレート](./media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="06824-113">**[Windows サービス]** テンプレートが表示されない場合は、 **.NET デスクトップ開発** ワークロードのインストールが必要である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="06824-113">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >
   > <span data-ttu-id="06824-114">**[新しいプロジェクト]** ダイアログの左側にある **[Visual Studio インストーラーを開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-114">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="06824-115">**[.NET デスクトップ開発]** ワークロードを選択し、 **[変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-115">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="06824-116">**[名前]** に「*MyNewService*」と入力し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-116">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="06824-117">**[デザイン]** タブが表示されます ( **[Service1.cs [デザイン]]** または **[Service1.vb [デザイン]]** )。</span><span class="sxs-lookup"><span data-stu-id="06824-117">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>

   <span data-ttu-id="06824-118">プロジェクト テンプレートには、<xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> から継承される `Service1` という名前のコンポーネント クラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="06824-118">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="06824-119">それは、サービスを開始するコードなどの多数の基本的なサービス コードを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="06824-119">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="06824-120">サービスの名前を変更する</span><span class="sxs-lookup"><span data-stu-id="06824-120">Rename the service</span></span>

<span data-ttu-id="06824-121">サービスの名前を **Service1** から **MyNewService** に変更します。</span><span class="sxs-lookup"><span data-stu-id="06824-121">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="06824-122">**ソリューション エクスプローラー** で **Service1.cs** または **Service1.vb** を選択し、ショートカット メニューから **[名前の変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-122">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="06824-123">ファイルの名前を **MyNewService.cs** または **MyNewService.vb** に変更し、**Enter** キーを押します</span><span class="sxs-lookup"><span data-stu-id="06824-123">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="06824-124">コード要素 *Service1* に対するすべての参照名を変更するかどうかを確認するポップアップ ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="06824-124">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="06824-125">ポップアップ ウィンドウで **[はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-125">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="06824-126">![名前の変更のプロンプト](./media/windows-service-rename.png "Windows サービスの名前の変更のプロンプト")</span><span class="sxs-lookup"><span data-stu-id="06824-126">![Rename prompt](./media/windows-service-rename.png "Windows service rename prompt")</span></span>

3. <span data-ttu-id="06824-127">**[デザイン]** タブで、ショートカット メニューから **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-127">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="06824-128">**[プロパティ]** ウィンドウで **ServiceName** の値を *MyNewService* に変更します。</span><span class="sxs-lookup"><span data-stu-id="06824-128">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="06824-129">![サービスのプロパティ](./media/windows-service-properties.png "Windows サービスのプロパティ")</span><span class="sxs-lookup"><span data-stu-id="06824-129">![Service properties](./media/windows-service-properties.png "Windows service properties")</span></span>

4. <span data-ttu-id="06824-130">**[ファイル]** メニューから **[すべて保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-130">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="06824-131">サービスに機能を追加する</span><span class="sxs-lookup"><span data-stu-id="06824-131">Add features to the service</span></span>

<span data-ttu-id="06824-132">このセクションでは、Windows サービスにカスタム イベント ログを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-132">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="06824-133">Windows サービスに追加できるコンポーネントの種類の例として、<xref:System.Diagnostics.EventLog> コンポーネントを使用しています。</span><span class="sxs-lookup"><span data-stu-id="06824-133">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="06824-134">サービスにカスタム イベント ログ機能を追加する</span><span class="sxs-lookup"><span data-stu-id="06824-134">Add custom event log functionality</span></span>

1. <span data-ttu-id="06824-135">**ソリューション エクスプローラー** で、**MyNewService.cs** または **MyNewService.vb** のショートカット メニューから **[デザイナーの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="06824-136">**[ツールボックス]** で **[コンポーネント]** を展開し、**EventLog** コンポーネントを **[Service1.cs [デザイン]]** タブまたは **[Service1.vb [デザイン]]** タブにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="06824-136">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="06824-137">**ソリューション エクスプローラー** で、**MyNewService.cs** または **MyNewService.vb** のショートカット メニューから **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-137">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="06824-138">カスタム イベント ログを定義します。</span><span class="sxs-lookup"><span data-stu-id="06824-138">Define a custom event log.</span></span> <span data-ttu-id="06824-139">C# の場合は、既存の `MyNewService()` コンストラクターを編集します。Visual Basic の場合は、`New()` コンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-139">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="06824-140"><xref:System.Diagnostics?displayProperty=nameWithType> 名前空間について、**MyNewService.cs** には `using` ステートメントを追加し (まだ存在しない場合)、**MyNewService.vb** には `Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-140">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="06824-141">**[ファイル]** メニューから **[すべて保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-141">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="06824-142">サービスの開始時の処理を定義する</span><span class="sxs-lookup"><span data-stu-id="06824-142">Define what occurs when the service starts</span></span>

<span data-ttu-id="06824-143">**MyNewService.cs** または **MyNewService.vb** のコード エディターで、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドを見つけます (プロジェクトの作成時に、Visual Studio によって空のメソッド定義が自動的に作成されます)。</span><span class="sxs-lookup"><span data-stu-id="06824-143">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="06824-144">サービスの開始時にイベント ログに対するエントリを記述するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-144">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="06824-145">ポーリング</span><span class="sxs-lookup"><span data-stu-id="06824-145">Polling</span></span>

<span data-ttu-id="06824-146">サービス アプリケーションは長期間実行するように設計されているため、通常は、(<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドの設定に従って) システムをポーリングまたは監視しています。</span><span class="sxs-lookup"><span data-stu-id="06824-146">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="06824-147">`OnStart` メソッドは、サービスの操作が開始された後にオペレーティング システムに戻る必要があります。そのため、システムはブロックされません。</span><span class="sxs-lookup"><span data-stu-id="06824-147">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span>

<span data-ttu-id="06824-148">単純なポーリング メカニズムを設定するには、<xref:System.Timers.Timer?displayProperty=nameWithType> コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="06824-148">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="06824-149">このタイマーによって、定期的な間隔で <xref:System.Timers.Timer.Elapsed> イベントが発生します。サービスは、イベントが発生するごとに監視を実行できます。</span><span class="sxs-lookup"><span data-stu-id="06824-149">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="06824-150"><xref:System.Timers.Timer> コンポーネントは次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="06824-150">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="06824-151">`MyNewService.OnStart` メソッドで <xref:System.Timers.Timer> コンポーネントのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="06824-151">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="06824-152"><xref:System.Timers.Timer.Start%2A> メソッドを呼び出して、タイマーを開始します。</span><span class="sxs-lookup"><span data-stu-id="06824-152">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="06824-153">ポーリング メカニズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="06824-153">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="06824-154">`MyNewService.OnStart` イベントに次のコードを追加して、ポーリング メカニズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="06824-154">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

   ```csharp
   // Set up a timer that triggers every minute.
   Timer timer = new Timer();
   timer.Interval = 60000; // 60 seconds
   timer.Elapsed += new ElapsedEventHandler(this.OnTimer);
   timer.Start();
   ```

   ```vb
   ' Set up a timer that triggers every minute.
   Dim timer As Timer = New Timer()
   timer.Interval = 60000 ' 60 seconds
   AddHandler timer.Elapsed, AddressOf Me.OnTimer
   timer.Start()
   ```

2. <span data-ttu-id="06824-155"><xref:System.Timers?displayProperty=nameWithType> 名前空間について、**MyNewService.cs** には `using` ステートメントを追加し、**MyNewService.vb** には `Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-155">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="06824-156">`MyNewService` クラスに <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> イベントを処理する `OnTimer` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-156">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

   ```csharp
   public void OnTimer(object sender, ElapsedEventArgs args)
   {
       // TODO: Insert monitoring activities here.
       eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);
   }
   ```

   ```vb
   Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)
      ' TODO: Insert monitoring activities here.
      eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)
      eventId = eventId + 1
   End Sub
   ```

4. <span data-ttu-id="06824-157">`MyNewService` クラスにメンバー変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-157">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="06824-158">それには、イベント ログに書き込まれる次のイベントの識別子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="06824-158">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="06824-159">すべての作業をメイン スレッド上で実行する代わりに、バックグラウンド ワーカー スレッドを使用してタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="06824-159">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="06824-160">詳細については、「<xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06824-160">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="06824-161">サービスの停止時の処理を定義する</span><span class="sxs-lookup"><span data-stu-id="06824-161">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="06824-162">サービスの停止時にイベント ログに対するエントリを追加するコード行を <xref:System.ServiceProcess.ServiceBase.OnStop%2A> に挿入します。</span><span class="sxs-lookup"><span data-stu-id="06824-162">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="06824-163">サービスに対して他の処理を定義する</span><span class="sxs-lookup"><span data-stu-id="06824-163">Define other actions for the service</span></span>

<span data-ttu-id="06824-164"><xref:System.ServiceProcess.ServiceBase.OnPause%2A>、<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>、および <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> の各メソッドをオーバーライドして、コンポーネントの処理をさらに定義できます。</span><span class="sxs-lookup"><span data-stu-id="06824-164">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>

<span data-ttu-id="06824-165">次のコードは、`MyNewService` クラスで <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> メソッドをオーバーライドする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="06824-165">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="06824-166">サービスの状態を設定する</span><span class="sxs-lookup"><span data-stu-id="06824-166">Set service status</span></span>

<span data-ttu-id="06824-167">サービスは、その状態を[サービス コントロール マネージャー](/windows/desktop/Services/service-control-manager)に報告します。これによりユーザーは、サービスが正常に機能しているかどうかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="06824-167">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="06824-168">既定では、<xref:System.ServiceProcess.ServiceBase> から継承したサービスは、SERVICE_STOPPED、SERVICE_PAUSED、および SERVICE_RUNNING など、限られたセットの状態設定を報告します。</span><span class="sxs-lookup"><span data-stu-id="06824-168">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="06824-169">サービスの開始に時間がかかる場合は、SERVICE_START_PENDING 状態を報告すると便利です。</span><span class="sxs-lookup"><span data-stu-id="06824-169">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span>

<span data-ttu-id="06824-170">Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) 関数を呼び出すコードを追加することで、SERVICE_START_PENDING および SERVICE_STOP_PENDING 状態設定を実装できます。</span><span class="sxs-lookup"><span data-stu-id="06824-170">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="06824-171">サービス保留の状態を実装する</span><span class="sxs-lookup"><span data-stu-id="06824-171">Implement service pending status</span></span>

1. <span data-ttu-id="06824-172"><xref:System.Runtime.InteropServices?displayProperty=nameWithType> 名前空間について、**MyNewService.cs** には `using` ステートメントを追加し、**MyNewService.vb** には `Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-172">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="06824-173">**MyNewService.cs** または **MyNewService.vb** に次のコードを追加して、`ServiceState` の値を宣言し、プラットフォーム呼び出しで使用する状態の構造を追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-173">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

    ```csharp
    public enum ServiceState
    {
        SERVICE_STOPPED = 0x00000001,
        SERVICE_START_PENDING = 0x00000002,
        SERVICE_STOP_PENDING = 0x00000003,
        SERVICE_RUNNING = 0x00000004,
        SERVICE_CONTINUE_PENDING = 0x00000005,
        SERVICE_PAUSE_PENDING = 0x00000006,
        SERVICE_PAUSED = 0x00000007,
    }

    [StructLayout(LayoutKind.Sequential)]
    public struct ServiceStatus
    {
        public int dwServiceType;
        public ServiceState dwCurrentState;
        public int dwControlsAccepted;
        public int dwWin32ExitCode;
        public int dwServiceSpecificExitCode;
        public int dwCheckPoint;
        public int dwWaitHint;
    };
    ```

    ```vb
    Public Enum ServiceState
        SERVICE_STOPPED = 1
        SERVICE_START_PENDING = 2
        SERVICE_STOP_PENDING = 3
        SERVICE_RUNNING = 4
        SERVICE_CONTINUE_PENDING = 5
        SERVICE_PAUSE_PENDING = 6
        SERVICE_PAUSED = 7
    End Enum

    <StructLayout(LayoutKind.Sequential)>
    Public Structure ServiceStatus
        Public dwServiceType As Long
        Public dwCurrentState As ServiceState
        Public dwControlsAccepted As Long
        Public dwWin32ExitCode As Long
        Public dwServiceSpecificExitCode As Long
        Public dwCheckPoint As Long
        Public dwWaitHint As Long
    End Structure
    ```

    > [!NOTE]
    > <span data-ttu-id="06824-174">サービス コントロール マネージャーは、[SERVICE_STATUS 構造体](/windows/win32/api/winsvc/ns-winsvc-service_status)の `dwWaitHint` メンバーと `dwCheckpoint` メンバーを使って、Windows サービスの開始やシャットダウンまでの待機時間を判断します。</span><span class="sxs-lookup"><span data-stu-id="06824-174">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/win32/api/winsvc/ns-winsvc-service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="06824-175">`OnStart` メソッドと `OnStop` メソッドが長時間実行している場合、サービスは、インクリメントした `dwCheckPoint` 値で `SetServiceStatus` をもう一度呼び出すことによって、追加の時間を要求できます。</span><span class="sxs-lookup"><span data-stu-id="06824-175">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="06824-176">`MyNewService` クラスで、[プラットフォーム呼び出し](../interop/consuming-unmanaged-dll-functions.md)を使用して、[SetServiceStatus 関数](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)を宣言します。</span><span class="sxs-lookup"><span data-stu-id="06824-176">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="06824-177">SERVICE_START_PENDING 状態を実装するには、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドの先頭に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-177">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

    ```csharp
    // Update the service state to Start Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Start Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

5. <span data-ttu-id="06824-178">`OnStart` メソッドの末尾に、状態を SERVICE_RUNNING に設定するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-178">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

    ```csharp
    // Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

6. <span data-ttu-id="06824-179">(省略可能) <xref:System.ServiceProcess.ServiceBase.OnStop%2A> が長時間実行されるメソッドの場合は、`OnStop` メソッドでこの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="06824-179">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="06824-180">SERVICE_STOP_PENDING 状態を実装し、`OnStop` メソッドが終了する前に SERVICE_STOPPED 状態を返します。</span><span class="sxs-lookup"><span data-stu-id="06824-180">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="06824-181">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="06824-181">For example:</span></span>

    ```csharp
    // Update the service state to Stop Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);

    // Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Stop Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)

    ' Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

## <a name="add-installers-to-the-service"></a><span data-ttu-id="06824-182">サービスにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="06824-182">Add installers to the service</span></span>

<span data-ttu-id="06824-183">Windows サービスを実行するには、まず、サービスをインストールする必要があります。これにより、サービスがサービス コントロール マネージャーに登録されます。</span><span class="sxs-lookup"><span data-stu-id="06824-183">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="06824-184">登録の詳細を処理するインストーラーをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-184">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="06824-185">**ソリューション エクスプローラー** で、**MyNewService.cs** または **MyNewService.vb** のショートカット メニューから **[デザイナーの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-185">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="06824-186">**[デザイン]** ビューでバックグラウンド領域を選択し、ショートカット メニューから **[インストーラーの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-186">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="06824-187">Visual Studio の既定では、2 つのインストーラーを含む `ProjectInstaller` というコンポーネント クラスがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="06824-187">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="06824-188">これらのインストーラーはサービス用とサービスの関連プロセス用です。</span><span class="sxs-lookup"><span data-stu-id="06824-188">These installers are for your service and for the service's associated process.</span></span>

3. <span data-ttu-id="06824-189">**[ProjectInstaller]** の **[デザイン]** ビューで、 **[serviceInstaller1]** (Visual C# プロジェクトの場合) または **[ServiceInstaller1]** (Visual Basic プロジェクトの場合) を選択してから、ショートカット メニューから **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-189">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="06824-190">**[プロパティ]** ウィンドウで、<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> プロパティが **MyNewService** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="06824-190">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

5. <span data-ttu-id="06824-191">*サンプル サービス* などのテキストを <xref:System.ServiceProcess.ServiceInstaller.Description%2A> プロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-191">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span>

     <span data-ttu-id="06824-192">このテキストは **[サービス]** ウィンドウの **[説明]** 列に表示され、サービスに関する説明をユーザーに示します。</span><span class="sxs-lookup"><span data-stu-id="06824-192">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="06824-193">![[サービス] ウィンドウのサービスの説明](./media/windows-service-description.png "サービスの説明")</span><span class="sxs-lookup"><span data-stu-id="06824-193">![Service description in the Services window.](./media/windows-service-description.png "Service description")</span></span>

6. <span data-ttu-id="06824-194"><xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> プロパティにテキストを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-194">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="06824-195">たとえば、*MyNewService Display Name* です。</span><span class="sxs-lookup"><span data-stu-id="06824-195">For example, *MyNewService Display Name*.</span></span>

     <span data-ttu-id="06824-196">このテキストは、 **[サービス]** ウィンドウの **[表示名]** 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="06824-196">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="06824-197">この名前は、システムによって使用される (たとえば、<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> コマンドを使用してサービスを開始する場合) 名前である `net start` プロパティとは異なる名前にすることができます。</span><span class="sxs-lookup"><span data-stu-id="06824-197">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

7. <span data-ttu-id="06824-198">ドロップダウン リストから <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> プロパティを <xref:System.ServiceProcess.ServiceStartMode.Automatic> に設定します。</span><span class="sxs-lookup"><span data-stu-id="06824-198">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

8. <span data-ttu-id="06824-199">完了すると、 **[プロパティ]** ウィンドウは次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="06824-199">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="06824-200">![Windows サービスのインストーラ プロパティ](./media/windows-service-installer-properties.png "Windows サービスのインストーラ プロパティ")</span><span class="sxs-lookup"><span data-stu-id="06824-200">![Installer Properties for a Windows service](./media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="06824-201">**[ProjectInstaller]** の **[デザイン]** ビューで、 **[serviceProcessInstaller1]** (Visual C# プロジェクトの場合) または **[ServiceProcessInstaller1]** (Visual Basic プロジェクトの場合) を選択してから、ショートカット メニューから **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-201">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="06824-202">ドロップダウン リストから <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> プロパティを <xref:System.ServiceProcess.ServiceAccount.LocalSystem> に設定します。</span><span class="sxs-lookup"><span data-stu-id="06824-202">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span>

     <span data-ttu-id="06824-203">この設定で、ローカル システム アカウントを使用してサービスがインストールされ、実行されます。</span><span class="sxs-lookup"><span data-stu-id="06824-203">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="06824-204"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> アカウントには、イベント ログへの書き込みを含む、幅広いアクセス許可が設定されています。</span><span class="sxs-lookup"><span data-stu-id="06824-204">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="06824-205">このアカウントは悪意のあるソフトウェアから攻撃されるリスクが高いため、使用する場合は注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="06824-205">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="06824-206">その他のタスクについては、ローカル コンピューターで非特権ユーザーとして機能し、リモート サーバーには匿名の資格情報を渡す <xref:System.ServiceProcess.ServiceAccount.LocalService> アカウントの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="06824-206">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="06824-207">この例は、 <xref:System.ServiceProcess.ServiceAccount.LocalService> アカウントを使用しようとすると失敗します。これは、イベント ログに書き込むアクセス許可が必要になるためです。</span><span class="sxs-lookup"><span data-stu-id="06824-207">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="06824-208">インストーラーについて詳しくは、「[方法: サービス アプリケーションにインストーラーを追加する](how-to-add-installers-to-your-service-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06824-208">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="06824-209">(省略可能) スタートアップ パラメーターを設定する</span><span class="sxs-lookup"><span data-stu-id="06824-209">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="06824-210">スタートアップ パラメーターを追加するよう決定する前に、これがサービスに情報を渡す最適な方法であるかどうかを検討してください。</span><span class="sxs-lookup"><span data-stu-id="06824-210">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="06824-211">使用や解析は簡単であり、ユーザーが簡単にオーバーライドできますが、ドキュメントなしでは検索や使用が困難である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="06824-211">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="06824-212">一般的に、サービスに必要なスタートアップ パラメーターが複数ある場合は、代わりにレジストリまたは構成ファイルの使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="06824-212">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span>

<span data-ttu-id="06824-213">Windows サービスは、コマンド ライン引数 (スタートアップ パラメーター) を受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="06824-213">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="06824-214">スタートアップ パラメーターを処理するコードを追加すると、ユーザーは、サービス プロパティ ウィンドウでカスタムのスタートアップ パラメーターを使用してサービスを開始できます。</span><span class="sxs-lookup"><span data-stu-id="06824-214">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="06824-215">ただし、これらのスタートアップ パラメーターは、次回のサービスの開始時には保持されません。</span><span class="sxs-lookup"><span data-stu-id="06824-215">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="06824-216">スタートアップ パラメーターを永続的に設定するには、レジストリに設定します。</span><span class="sxs-lookup"><span data-stu-id="06824-216">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="06824-217">各 Windows サービスには、**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** サブキー以下にレジストリ エントリがあります。</span><span class="sxs-lookup"><span data-stu-id="06824-217">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="06824-218">各サービスのサブキーで、**Parameters** サブキーを使用してサービスがアクセスできる情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="06824-218">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="06824-219">その他の種類のプログラムの場合と同じ方法で、Windows サービスに対してアプリケーション構成ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="06824-219">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="06824-220">サンプル コードについては、「<xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06824-220">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="06824-221">スタートアップ パラメーターを追加するには</span><span class="sxs-lookup"><span data-stu-id="06824-221">To add startup parameters</span></span>

1. <span data-ttu-id="06824-222">**Program.cs** または **MyNewService.Designer.vb** を選択してから、ショートカット メニューから **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-222">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="06824-223">`Main` メソッドで、入力パラメーターを追加してサービス コンストラクターに渡すようにコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="06824-223">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="06824-224">**MyNewService.cs** または **MyNewService.vb** で、次のように入力パラメーターを処理するように `MyNewService` コンストラクターを変更します。</span><span class="sxs-lookup"><span data-stu-id="06824-224">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

   ```csharp
   using System.Diagnostics;

   public MyNewService(string[] args)
   {
       InitializeComponent();

       string eventSourceName = "MySource";
       string logName = "MyNewLog";

       if (args.Length > 0)
       {
          eventSourceName = args[0];
       }

       if (args.Length > 1)
       {
           logName = args[1];
       }

       eventLog1 = new EventLog();

       if (!EventLog.SourceExists(eventSourceName))
       {
           EventLog.CreateEventSource(eventSourceName, logName);
       }

       eventLog1.Source = eventSourceName;
       eventLog1.Log = logName;
   }
   ```

   ```vb
   Imports System.Diagnostics

   Public Sub New(ByVal cmdArgs() As String)
       InitializeComponent()
       Dim eventSourceName As String = "MySource"
       Dim logName As String = "MyNewLog"
       If (cmdArgs.Count() > 0) Then
           eventSourceName = cmdArgs(0)
       End If
       If (cmdArgs.Count() > 1) Then
           logName = cmdArgs(1)
       End If
       eventLog1 = New EventLog()
       If (Not EventLog.SourceExists(eventSourceName)) Then
           EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   <span data-ttu-id="06824-225">このコードでは、ユーザーが指定したスタートアップ パラメーターに従ってイベント ソースとログ名を設定します。</span><span class="sxs-lookup"><span data-stu-id="06824-225">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="06824-226">引数が指定されていない場合は、既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="06824-226">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="06824-227">コマンド ライン引数を指定するには、**ProjectInstaller.cs** または **ProjectInstaller.vb** の `ProjectInstaller` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="06824-227">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

   ```csharp
   protected override void OnBeforeInstall(IDictionary savedState)
   {
       string parameter = "MySource1\" \"MyLogFile1";
       Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
       base.OnBeforeInstall(savedState);
   }
   ```

   ```vb
   Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
       Dim parameter As String = "MySource1"" ""MyLogFile1"
       Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
       MyBase.OnBeforeInstall(savedState)
   End Sub
   ```

   <span data-ttu-id="06824-228">通常、この値には Windows サービスの実行可能ファイルの完全なパスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="06824-228">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="06824-229">サービスが正しく開始されるには、ユーザーはパスと各パラメーターに引用符を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="06824-229">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="06824-230">ユーザーは **ImagePath** レジストリ エントリのパラメーターを変更して、Windows サービスのスタートアップ パラメーターを変更できます。</span><span class="sxs-lookup"><span data-stu-id="06824-230">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="06824-231">ただし、管理や構成のユーティリティを使用するなどして、プログラムで値を変更し、わかりやすい方法で機能を公開することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="06824-231">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="06824-232">サービスをビルドする</span><span class="sxs-lookup"><span data-stu-id="06824-232">Build the service</span></span>

1. <span data-ttu-id="06824-233">**ソリューション エクスプローラー** で、**MyNewService** プロジェクトのショートカット メニューから **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-233">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="06824-234">プロジェクトのプロパティ ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="06824-234">The property pages for your project appear.</span></span>

2. <span data-ttu-id="06824-235">**[アプリケーション]** タブの **[スタートアップ オブジェクト]** 一覧で **MyNewService.Program** (Visual Basic プロジェクトの場合は **Sub Main**) を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-235">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="06824-236">プロジェクトをビルドするには、**ソリューション エクスプローラー** で、プロジェクトのショートカット メニューから **[ビルド]** を選択します (または **Ctrl**+**Shift**+**B** キーを押します)。</span><span class="sxs-lookup"><span data-stu-id="06824-236">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="06824-237">サービスをインストールする</span><span class="sxs-lookup"><span data-stu-id="06824-237">Install the service</span></span>

<span data-ttu-id="06824-238">Windows サービスを構築済みであるため、サービスをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="06824-238">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="06824-239">Windows サービスをインストールするには、インストール先のコンピューター上の管理者資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="06824-239">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="06824-240">管理者資格情報を使用して、[Visual Studio 用開発者コマンド プロンプト](/visualstudio/ide/reference/command-prompt-powershell)を開きます。</span><span class="sxs-lookup"><span data-stu-id="06824-240">Open [Developer Command Prompt for Visual Studio](/visualstudio/ide/reference/command-prompt-powershell) with administrative credentials.</span></span>

2. <span data-ttu-id="06824-241">**[開発者コマンド プロンプト for Visual Studio]** で、プロジェクトの出力を含むフォルダーに移動します (既定では、プロジェクトの *\bin\Debug* サブディレクトリです)。</span><span class="sxs-lookup"><span data-stu-id="06824-241">In **Developer Command Prompt for Visual Studio**, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="06824-242">次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="06824-242">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="06824-243">サービスが正常にインストールされると、正常に実行されたことが報告されます。</span><span class="sxs-lookup"><span data-stu-id="06824-243">If the service installs successfully, the command reports success.</span></span>

    <span data-ttu-id="06824-244">システムで *installutil.exe* を見付けることができない場合は、コンピューター上に存在することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="06824-244">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="06824-245">このツールは、.NET Framework と共に *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;* フォルダーにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="06824-245">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="06824-246">たとえば、64 ビット バージョンでの既定のパスは *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe* です。</span><span class="sxs-lookup"><span data-stu-id="06824-246">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="06824-247">**installutil.exe** プロセスが失敗する場合は、インストール ログを調べて理由を確認します。</span><span class="sxs-lookup"><span data-stu-id="06824-247">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="06824-248">既定で、ログはサービスの実行可能ファイルと同じフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="06824-248">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="06824-249">インストールは次の場合に失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="06824-249">The installation can fail if:</span></span>
    - <span data-ttu-id="06824-250"><xref:System.ComponentModel.RunInstallerAttribute> クラスが `ProjectInstaller` クラスに存在しない。</span><span class="sxs-lookup"><span data-stu-id="06824-250">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    - <span data-ttu-id="06824-251">属性が `true` に設定されていない。</span><span class="sxs-lookup"><span data-stu-id="06824-251">The attribute isn't set to `true`.</span></span>
    - <span data-ttu-id="06824-252">`ProjectInstaller` クラスが `public` として定義されていない。</span><span class="sxs-lookup"><span data-stu-id="06824-252">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="06824-253">詳細については、[サービスをインストールおよびアンインストールする](how-to-install-and-uninstall-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06824-253">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="06824-254">サービスを開始して実行する</span><span class="sxs-lookup"><span data-stu-id="06824-254">Start and run the service</span></span>

1. <span data-ttu-id="06824-255">Windows で、 **[サービス]** デスクトップ アプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="06824-255">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="06824-256">**Windows**+**R** キーを押して **[ファイル名を指定して実行]** ボックスを開き、「*services.msc*」と入力して、**Enter** キーを押すか **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-256">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="06824-257">**[サービス]** 内にサービスが一覧表示されます。サービスは、サービスに対して設定した表示名でアルファベット順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="06824-257">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![[サービス] ウィンドウの MyNewService。](./media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="06824-259">サービスを開始するには、サービスのショートカット メニューから **[開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-259">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="06824-260">サービスを停止するには、サービスのショートカット メニューから **[停止]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-260">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="06824-261">(省略可能) コマンド ラインから、コマンド **net start &lt;service name&gt;** と **net stop &lt;service name&gt;** を使用して、サービスを開始または停止します。</span><span class="sxs-lookup"><span data-stu-id="06824-261">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="06824-262">サービスのイベント ログ出力を確認する</span><span class="sxs-lookup"><span data-stu-id="06824-262">Verify the event log output of your service</span></span>

1. <span data-ttu-id="06824-263">Windows で、 **[イベント ビューアー]** デスクトップ アプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="06824-263">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="06824-264">Windows 検索バーに「*イベント ビューアー*」と入力し、検索結果から **[イベント ビューアー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="06824-264">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="06824-265">Visual Studio でイベント ログにアクセスするには、 **[表示]** メニューから **サーバー エクスプローラー** を開き (または **Ctrl**+**Alt**+**S** キーを押し)、ローカル コンピューターの **[イベント ログ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="06824-265">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="06824-266">**[イベント ビューアー]** で、 **[アプリケーションとサービス ログ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="06824-266">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="06824-267">**MyNewLog** (または、手順に従ってコマンド ライン引数を追加した場合は **MyLogFile1**) の一覧を見つけて展開します。</span><span class="sxs-lookup"><span data-stu-id="06824-267">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="06824-268">サービスが実行した 2 つの操作 (開始および停止) のエントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="06824-268">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![イベント ビューアーを使用してイベント ログの項目を表示する](./media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="06824-270">リソースをクリーンアップする</span><span class="sxs-lookup"><span data-stu-id="06824-270">Clean up resources</span></span>

<span data-ttu-id="06824-271">Windows サービス アプリが不要になったら、削除することができます。</span><span class="sxs-lookup"><span data-stu-id="06824-271">If you no longer need the Windows service app, you can remove it.</span></span>

1. <span data-ttu-id="06824-272">管理者資格情報を使用して、**Visual Studio 用開発者コマンド プロンプト** を開きます。</span><span class="sxs-lookup"><span data-stu-id="06824-272">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="06824-273">**[開発者コマンド プロンプト for Visual Studio]** ウィンドウで、プロジェクトの出力を含むフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="06824-273">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="06824-274">次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="06824-274">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="06824-275">サービスが正常にアンインストールされると、サービスが正常に削除されたことが報告されます。</span><span class="sxs-lookup"><span data-stu-id="06824-275">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="06824-276">詳細については、[サービスをインストールおよびアンインストールする](how-to-install-and-uninstall-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06824-276">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="06824-277">次の手順</span><span class="sxs-lookup"><span data-stu-id="06824-277">Next steps</span></span>

<span data-ttu-id="06824-278">サービスを作成したので、以下を実行できます。</span><span class="sxs-lookup"><span data-stu-id="06824-278">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="06824-279">他のユーザーが Windows サービスのインストールに使用できるスタンドアロン セットアップ プログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="06824-279">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="06824-280">[WiX ツールセット](https://wixtoolset.org/)を使用して、Windows サービスのインストーラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="06824-280">Use the [WiX Toolset](https://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="06824-281">その他のアイデアについては、[インストーラー パッケージの作成](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06824-281">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="06824-282">インストールしたサービスにコマンドを送信できる <xref:System.ServiceProcess.ServiceController> コンポーネントの使用法を調べます。</span><span class="sxs-lookup"><span data-stu-id="06824-282">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="06824-283">アプリケーションの実行時にイベント ログを作成するのではなく、アプリケーションのインストール時にインストーラーを使用してイベント ログを作成します。</span><span class="sxs-lookup"><span data-stu-id="06824-283">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="06824-284">アプリケーションをアンインストールすると、イベント ログはインストーラーによって削除されます。</span><span class="sxs-lookup"><span data-stu-id="06824-284">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="06824-285">詳細については、「<xref:System.Diagnostics.EventLogInstaller>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06824-285">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="06824-286">関連項目</span><span class="sxs-lookup"><span data-stu-id="06824-286">See also</span></span>

- [<span data-ttu-id="06824-287">Windows サービス アプリケーション</span><span class="sxs-lookup"><span data-stu-id="06824-287">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="06824-288">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="06824-288">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="06824-289">方法: Windows サービス アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="06824-289">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="06824-290">サービス (Windows)</span><span class="sxs-lookup"><span data-stu-id="06824-290">Services (Windows)</span></span>](/windows/desktop/Services/services)
