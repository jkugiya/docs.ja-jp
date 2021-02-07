---
description: '詳細情報: 実行時間の長いワークフローサービスの作成'
title: 長時間のワークフロー サービスの作成
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 9d26e763e2515f9e9ec2b61201512f02eeaeb1bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756904"
---
# <a name="create-a-long-running-workflow-service"></a><span data-ttu-id="65829-103">実行時間の長いワークフローサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="65829-103">Create a Long-running Workflow Service</span></span>

<span data-ttu-id="65829-104">ここでは、実行時間の長いワークフロー サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="65829-104">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="65829-105">実行時間の長いワークフロー サービスは、長期間にわたって実行できます。</span><span class="sxs-lookup"><span data-stu-id="65829-105">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="65829-106">ワークフローでは、いくつかの追加情報を待つ間アイドル状態になることがあります。</span><span class="sxs-lookup"><span data-stu-id="65829-106">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="65829-107">アイドル状態になると、ワークフローは SQL データベースに永続化され、メモリから削除されます。</span><span class="sxs-lookup"><span data-stu-id="65829-107">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="65829-108">追加情報が使用可能になると、ワークフロー インスタンスがメモリに読み込み直されて、実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="65829-108">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="65829-109">このシナリオでは、非常に簡略化された注文システムを実装します。</span><span class="sxs-lookup"><span data-stu-id="65829-109">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="65829-110">クライアントは、最初のメッセージをワークフロー サービスに送信して注文を開始します。</span><span class="sxs-lookup"><span data-stu-id="65829-110">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="65829-111">ワークフロー サービスは、注文 ID をクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="65829-111">It returns an order ID to the client.</span></span> <span data-ttu-id="65829-112">この時点で、ワークフロー サービスは、クライアントからの別のメッセージを待機しており、アイドル状態に入って、SQL Server データベースに永続化されます。</span><span class="sxs-lookup"><span data-stu-id="65829-112">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="65829-113">クライアントが次のメッセージを送信して項目を注文すると、ワークフロー サービスはメモリに読み込み直されて、注文の処理を終了します。</span><span class="sxs-lookup"><span data-stu-id="65829-113">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="65829-114">次のコード例では、項目が注文に追加されたことを示す文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="65829-114">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="65829-115">このコード例は、テクノロジの実際の適用を意図するものではなく、実行時間の長いワークフロー サービスを示す簡単な例です。</span><span class="sxs-lookup"><span data-stu-id="65829-115">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="65829-116">このトピックでは、Visual Studio 2012 のプロジェクトとソリューションの作成方法を理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="65829-116">This topic assumes you know how to create Visual Studio 2012 projects and solutions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65829-117">前提条件</span><span class="sxs-lookup"><span data-stu-id="65829-117">Prerequisites</span></span>

<span data-ttu-id="65829-118">このチュートリアルを使用するには、次のソフトウェアがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="65829-118">You must have the following software installed to use this walkthrough:</span></span>

1. <span data-ttu-id="65829-119">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="65829-119">Microsoft SQL Server 2008</span></span>

2. <span data-ttu-id="65829-120">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="65829-120">Visual Studio 2012</span></span>

3. <span data-ttu-id="65829-121">Microsoft [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65829-121">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>

4. <span data-ttu-id="65829-122">WCF および Visual Studio 2012 に精通しており、プロジェクト/ソリューションの作成方法を理解していること。</span><span class="sxs-lookup"><span data-stu-id="65829-122">You are familiar with WCF and Visual Studio 2012 and know how to create projects/solutions.</span></span>

## <a name="set-up-the-sql-database"></a><span data-ttu-id="65829-123">SQL Database を設定する</span><span class="sxs-lookup"><span data-stu-id="65829-123">Set up the SQL Database</span></span>

1. <span data-ttu-id="65829-124">ワークフロー サービス インスタンスが永続化されるようにするには、Microsoft SQL Server をインストールして、永続化ワークフロー インスタンスを保存するようにデータベースを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65829-124">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="65829-125">[ **スタート** ] ボタンをクリックし、[すべての **プログラム**]、[ **Microsoft SQL Server 2008**]、[ **microsoft sql Management Studio**] の順に選択して、microsoft sql Management Studio を実行します。</span><span class="sxs-lookup"><span data-stu-id="65829-125">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>

2. <span data-ttu-id="65829-126">[ **接続** ] ボタンをクリックして、SQL Server インスタンスにログオンします。</span><span class="sxs-lookup"><span data-stu-id="65829-126">Click the **Connect** button to log on to the SQL Server instance</span></span>

3. <span data-ttu-id="65829-127">ツリービューで [**データベース**] を右クリックし、[**新しいデータベース**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65829-127">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="65829-128">という名前の新しいデータベースを作成し `SQLPersistenceStore` ます。</span><span class="sxs-lookup"><span data-stu-id="65829-128">to create a new database called `SQLPersistenceStore`.</span></span>

4. <span data-ttu-id="65829-129">SQLPersistenceStore データベースの C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en ディレクトリにある SqlWorkflowInstanceStoreSchema.sql スクリプト ファイルを実行して、必要なデータベース スキーマを設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-129">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>

5. <span data-ttu-id="65829-130">SQLPersistenceStore データベースの C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en ディレクトリにある SqlWorkflowInstanceStoreLogic.sql スクリプト ファイルを実行して、必要なデータベース ロジックを設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-130">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>

## <a name="create-the-web-hosted-workflow-service"></a><span data-ttu-id="65829-131">Web ホストワークフローサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="65829-131">Create the Web Hosted Workflow Service</span></span>

1. <span data-ttu-id="65829-132">空の Visual Studio 2012 ソリューションを作成し、という名前を指定 `OrderProcessing` します。</span><span class="sxs-lookup"><span data-stu-id="65829-132">Create an empty Visual Studio 2012 solution, name it `OrderProcessing`.</span></span>

2. <span data-ttu-id="65829-133">`OrderService` という新しい WCF ワークフロー サービス アプリケーション プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="65829-133">Add a new WCF Workflow Service Application project called `OrderService` to the solution.</span></span>

3. <span data-ttu-id="65829-134">[プロジェクトのプロパティ] ダイアログボックスで、[ **Web** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="65829-134">In the project properties dialog, select the **Web** tab.</span></span>

    1. <span data-ttu-id="65829-135">[ **開始アクション** ] で **特定のページ** を選択し、を指定し `Service1.xamlx` ます。</span><span class="sxs-lookup"><span data-stu-id="65829-135">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>

        <span data-ttu-id="65829-136">![ワークフロー サービス プロジェクトの Web プロパティ](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Web ホステッドワークフローサービス固有のページオプションを作成する")</span><span class="sxs-lookup"><span data-stu-id="65829-136">![Workflow Service Project Web Properties](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Create the web hosted workflow service - Specific Page option")</span></span>

    2. <span data-ttu-id="65829-137">[ **サーバー** ] で、[ **ローカル IIS Web サーバーを使用する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="65829-137">Under **Servers** select **Use Local IIS Web server**.</span></span>

        <span data-ttu-id="65829-138">![ローカル Web サーバーの設定](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Web ホストワークフローサービスの作成-[ローカル IIS Web サーバーを使用する] オプション")</span><span class="sxs-lookup"><span data-stu-id="65829-138">![Local Web Server Settings](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Create the web hosted workflow service - Use Local IIS Web Server option")</span></span>

        > [!WARNING]
        > <span data-ttu-id="65829-139">この設定を行うには、Visual Studio 2012 を管理者モードで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65829-139">You must run Visual Studio 2012 in administrator mode to make this setting.</span></span>

        <span data-ttu-id="65829-140">次の 2 つの手順で、ワークフロー サービス プロジェクトが IIS でホストされるように設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-140">These two steps configure the workflow service project to be hosted by IIS.</span></span>

4. <span data-ttu-id="65829-141">`Service1.xamlx`まだ開いていない場合はを開き、既存の **receiverequest アクティビティ** アクティビティと **sendresponse** アクティビティを削除します。</span><span class="sxs-lookup"><span data-stu-id="65829-141">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>

5. <span data-ttu-id="65829-142">[ **シーケンシャルサービス** ] アクティビティを選択し、[ **変数** ] リンクをクリックして、次の図に示す変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="65829-142">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="65829-143">こうするといくつかの変数が追加され、後でワークフロー サービスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="65829-143">Doing this adds some variables that will be used later on in the workflow service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="65829-144">[変数の種類] ボックスの一覧に [CorrelationHandle] が表示されない場合は、ドロップダウンから [ **型の参照** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="65829-144">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="65829-145">[ **型名** ] ボックスに「CorrelationHandle」と入力し、Listbox から CorrelationHandle を選択して、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65829-145">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>

    <span data-ttu-id="65829-146">![変数の追加](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "シーケンシャルサービスアクティビティに変数を追加します。")</span><span class="sxs-lookup"><span data-stu-id="65829-146">![Add Variables](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Add variables to the Sequential Service activity.")</span></span>

6. <span data-ttu-id="65829-147">**Receiveandsendreply** アクティビティテンプレートを [**シーケンシャルサービス**] アクティビティにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="65829-147">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="65829-148">このアクティビティのセットは、クライアントからメッセージを受信して、返信を送信します。</span><span class="sxs-lookup"><span data-stu-id="65829-148">This set of activities will receive a message from a client and send a reply back.</span></span>

    1. <span data-ttu-id="65829-149">Receive アクティビティを選択し、次の図で強調表示 **さ** れているプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-149">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>

        <span data-ttu-id="65829-150">![Receive アクティビティのプロパティの設定](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Receive アクティビティのプロパティを設定します。")</span><span class="sxs-lookup"><span data-stu-id="65829-150">![Set Receive Activity Properties](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Set the Receive activity properties.")</span></span>

        <span data-ttu-id="65829-151">DisplayName プロパティは、デザイナーに表示される Receive アクティビティの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-151">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="65829-152">ServiceContractName プロパティと OperationName プロパティは、Receive アクティビティで実装されるサービス コントラクトおよび操作の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="65829-152">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> <span data-ttu-id="65829-153">ワークフローサービスでのコントラクトの使用方法の詳細については、「 [ワークフローでのコントラクトの使用](using-contracts-in-workflow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65829-153">For more information about how contracts are used in Workflow services see [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>

    2. <span data-ttu-id="65829-154">**Receivestartorder** アクティビティの [**定義...** ] リンクをクリックし、次の図に示されているプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-154">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="65829-155">[ **パラメーター** ] オプションボタンが選択され、という名前のパラメーター `p_customerName` が変数にバインドされていることに注意して `customerName` ください。</span><span class="sxs-lookup"><span data-stu-id="65829-155">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="65829-156">これにより、Receive アクティビティがデータを受信し、そのデータをローカル変数にバインドするように構成 **さ** れます。</span><span class="sxs-lookup"><span data-stu-id="65829-156">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>

        <span data-ttu-id="65829-157">![Receive アクティビティが受信するデータの設定](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Receive アクティビティによって受信されるデータのプロパティを設定します。")</span><span class="sxs-lookup"><span data-stu-id="65829-157">![Setting the data received by the Receive activity](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Set the properties for data received by the Receive activity.")</span></span>

    3. <span data-ttu-id="65829-158">**SendReplyToReceive** アクティビティを選択し、次の図に示すように、強調表示されているプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-158">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>

        <span data-ttu-id="65829-159">![SendReply アクティビティのプロパティの設定](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span><span class="sxs-lookup"><span data-stu-id="65829-159">![Setting the properties of the SendReply activity](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span></span>

    4. <span data-ttu-id="65829-160">**SendReplyToStartOrder** アクティビティの [**定義...** ] リンクをクリックし、次の図に示すプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-160">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="65829-161">[ **パラメーター** ] オプションボタンが選択されていることに注意してください。という名前のパラメーター `p_orderId` が変数にバインドされてい `orderId` ます。</span><span class="sxs-lookup"><span data-stu-id="65829-161">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="65829-162">この設定により、SendReplyToStartOrder アクティビティが型文字列の値を呼び出し元に返すように指定されます。</span><span class="sxs-lookup"><span data-stu-id="65829-162">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>

        <span data-ttu-id="65829-163">![SendReply アクティビティのコンテンツ データの構成](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "SetReplyToStartOrder アクティビティの設定を構成します。")</span><span class="sxs-lookup"><span data-stu-id="65829-163">![Configuring the SendReply activity content data](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Configure setting for SetReplyToStartOrder activity.")</span></span>

    5. <span data-ttu-id="65829-164">**Receive** アクティビティと **SendReply** アクティビティの間に Assign アクティビティをドラッグアンドドロップし、次の図に示すようにプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-164">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>

        <span data-ttu-id="65829-165">![Assign アクティビティの追加](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Assign アクティビティを追加します。")</span><span class="sxs-lookup"><span data-stu-id="65829-165">![Adding an assign activity](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Add an assign activity.")</span></span>

        <span data-ttu-id="65829-166">これにより、新しい注文 ID が作成され、orderId 変数に値が配置されます。</span><span class="sxs-lookup"><span data-stu-id="65829-166">This creates a new order ID and places the value in the orderId variable.</span></span>

    6. <span data-ttu-id="65829-167">**ReplyToStartOrder** アクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="65829-167">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="65829-168">[プロパティ] ウィンドウで、[ **Correlationinitializers**] の省略記号ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="65829-168">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="65829-169">[ **初期化子の追加** ] リンクを選択し、[ `orderIdHandle` 初期化子] テキストボックスに「」と入力します。 [関連付けの種類] で [クエリ関連付け初期化子] を選択し、[XPATH クエリ] ボックスの下の p_orderId を選択します。</span><span class="sxs-lookup"><span data-stu-id="65829-169">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="65829-170">これらの設定を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="65829-170">These settings are shown in the following illustration.</span></span> <span data-ttu-id="65829-171">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65829-171">Click **OK**.</span></span>  <span data-ttu-id="65829-172">これにより、クライアントとワークフロー サービスのこのインスタンス間の相関関係が初期化されます。</span><span class="sxs-lookup"><span data-stu-id="65829-172">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="65829-173">この注文 ID を含むメッセージが受信されると、ワークフロー サービスのこのインスタンスにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="65829-173">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>

        <span data-ttu-id="65829-174">![関連付け初期化子の追加](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "関連付け初期化子を追加します。")</span><span class="sxs-lookup"><span data-stu-id="65829-174">![Adding a correlation initializer](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Add a correlation initializer.")</span></span>

7. <span data-ttu-id="65829-175">別の **Receiveandsendreply** アクティビティをワークフローの最後 (最初の **Receive** アクティビティと **SendReply** アクティビティを含む **シーケンス** の外側) にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="65829-175">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="65829-176">これで、クライアントで送信された 2 つ目のメッセージを受信し、それに応答します。</span><span class="sxs-lookup"><span data-stu-id="65829-176">This will receive the second message sent by the client and respond to it.</span></span>

    1. <span data-ttu-id="65829-177">新しく追加された **Receive** アクティビティと **SendReply** アクティビティを含む **シーケンス** を選択し、[**変数**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="65829-177">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="65829-178">次の図で強調表示されている変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="65829-178">Add the variable highlighted in the following illustration:</span></span>

        <span data-ttu-id="65829-179">![新しい変数の追加](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "ItemId 変数を追加します。")</span><span class="sxs-lookup"><span data-stu-id="65829-179">![Adding new variables](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Add the ItemId variable.")</span></span>

        <span data-ttu-id="65829-180">また `orderResult` 、スコープに **文字列** としてを追加し `Sequence` ます。</span><span class="sxs-lookup"><span data-stu-id="65829-180">Also add `orderResult` as **String** in the `Sequence` scope.</span></span>

    2. <span data-ttu-id="65829-181">**Receive** アクティビティを選択し、次の図に示すプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-181">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>

        <span data-ttu-id="65829-182">![Receive アクティビティのプロパティを設定する](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Receive アクティビティのプロパティを設定します。")</span><span class="sxs-lookup"><span data-stu-id="65829-182">![Set the Receive activity properties](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Set the Receive activities properties.")</span></span>

        > [!NOTE]
        > <span data-ttu-id="65829-183">必ず、 **ServiceContractName** フィールドをに変更 `../IAddItem` してください。</span><span class="sxs-lookup"><span data-stu-id="65829-183">Don't forget to change **ServiceContractName** field with `../IAddItem`.</span></span>

    3. <span data-ttu-id="65829-184">**Receiveadditem** アクティビティの [**定義...** ] リンクをクリックし、次の図に示すパラメーターを追加します。これにより、receive アクティビティで2つのパラメーター、注文 ID、および順序付けされている項目の id が受け入れられるように構成されます。</span><span class="sxs-lookup"><span data-stu-id="65829-184">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>

        <span data-ttu-id="65829-185">![2 番目の受信のパラメーターの指定](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "2つのパラメーターを受け取るように receive アクティビティを構成します。")</span><span class="sxs-lookup"><span data-stu-id="65829-185">![Specifying parameters for the second receive](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Configure the receive activity to receive two parameters.")</span></span>

    4. <span data-ttu-id="65829-186">**CorrelateOn** の省略記号ボタンをクリックし、「」と入力し `orderIdHandle` ます。</span><span class="sxs-lookup"><span data-stu-id="65829-186">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="65829-187">[ **XPath クエリ**] の下にあるドロップダウン矢印をクリックし、を選択し `p_orderId` ます。</span><span class="sxs-lookup"><span data-stu-id="65829-187">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="65829-188">これにより、2 つ目の Receive アクティビティに相関関係が設定されます。</span><span class="sxs-lookup"><span data-stu-id="65829-188">This configures the correlation on the second receive activity.</span></span> <span data-ttu-id="65829-189">相関関係の詳細については、「 [関連付け](correlation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65829-189">For more information about correlation see [Correlation](correlation.md).</span></span>

        <span data-ttu-id="65829-190">![CorrelatesOn プロパティの設定](./media/creating-a-long-running-workflow-service/correlateson-setting.png "[Correlateson プロパティを設定します。")</span><span class="sxs-lookup"><span data-stu-id="65829-190">![Setting the CorrelatesOn property](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Set the CorrelatesOn property.")</span></span>

    5. <span data-ttu-id="65829-191">**If** アクティビティを、 **receiveadditem** アクティビティの直後にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="65829-191">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="65829-192">このアクティビティは、if ステートメントと同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="65829-192">This activity acts just like an if statement.</span></span>

        1. <span data-ttu-id="65829-193">**Condition** プロパティをに設定します。`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="65829-193">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>

        2. <span data-ttu-id="65829-194">次の図に示すように、 **assign アクティビティを** **[Then** ] セクションと [ **Else** ] セクションにドラッグアンドドロップして、 **assign** アクティビティのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-194">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>

            <span data-ttu-id="65829-195">![サービス呼び出しの結果の割り当て](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "サービス呼び出しの結果を割り当てます。")</span><span class="sxs-lookup"><span data-stu-id="65829-195">![Assigning the result of the service call](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Assign the result of the service call.")</span></span>

            <span data-ttu-id="65829-196">条件がの場合 `true` 、 **Then** セクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="65829-196">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="65829-197">条件がの場合は `false` 、 **Else** セクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="65829-197">If the condition is `false` the **Else** section is executed.</span></span>

        3. <span data-ttu-id="65829-198">**SendReplyToReceive** アクティビティを選択し、次の図に示す **DisplayName** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="65829-198">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>

            <span data-ttu-id="65829-199">![SendReply アクティビティのプロパティの設定](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "SendReply アクティビティのプロパティを設定します。")</span><span class="sxs-lookup"><span data-stu-id="65829-199">![Setting the SendReply activity properties](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Set the SendReply activity property.")</span></span>

        4. <span data-ttu-id="65829-200">**SetReplyToAddItem** アクティビティの [**定義...** ] リンクをクリックし、次の図に示すように構成します。</span><span class="sxs-lookup"><span data-stu-id="65829-200">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="65829-201">これにより、変数の値を返すように **SendReplyToAddItem** アクティビティが構成され `orderResult` ます。</span><span class="sxs-lookup"><span data-stu-id="65829-201">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>

            <span data-ttu-id="65829-202">![SendReply アクティビティのデータバインディングの設定](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "SendReplyToAddItem アクティビティのプロパティを設定します。")</span><span class="sxs-lookup"><span data-stu-id="65829-202">![Setting the data binding for the SendReply activity](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Set property for SendReplyToAddItem activity.")</span></span>

8. <span data-ttu-id="65829-203">web.config ファイルを開き、セクションに次の要素を追加して、 \<behavior> ワークフローの永続化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="65829-203">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    > <span data-ttu-id="65829-204">前のコード スニペットでホストと SQL Server インスタンス名を置換するようにします。</span><span class="sxs-lookup"><span data-stu-id="65829-204">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>

9. <span data-ttu-id="65829-205">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="65829-205">Build the solution.</span></span>

## <a name="create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="65829-206">ワークフローサービスを呼び出すクライアントアプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="65829-206">Create a Client Application to Call the Workflow Service</span></span>

1. <span data-ttu-id="65829-207">`OrderClient` という新しいコンソール アプリケーション プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="65829-207">Add a new Console application project called `OrderClient` to the solution.</span></span>

2. <span data-ttu-id="65829-208">次のアセンブリへの参照を `OrderClient` プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="65829-208">Add references to the following assemblies to the `OrderClient` project</span></span>

    1. <span data-ttu-id="65829-209">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="65829-209">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="65829-210">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="65829-210">System.ServiceModel.Activities.dll</span></span>

3. <span data-ttu-id="65829-211">サービス参照をワークフロー サービスに追加し、`OrderService` を名前空間として指定します。</span><span class="sxs-lookup"><span data-stu-id="65829-211">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>

4. <span data-ttu-id="65829-212">クライアント プロジェクトの `Main()` メソッド内に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="65829-212">In the `Main()` method of the client project add the following code:</span></span>

    ```csharp
    static void Main(string[] args)
    {
       // Send initial message to start the workflow service
       Console.WriteLine("Sending start message");
       StartOrderClient startProxy = new StartOrderClient();
       string orderId = startProxy.StartOrder("Kim Abercrombie");

       // The workflow service is now waiting for the second message to be sent
       Console.WriteLine("Workflow service is idle...");
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");
       Console.ReadLine();

       // Send the second message
       Console.WriteLine("Sending add item message");
       AddItemClient addProxy = new AddItemClient();
       AddItem item = new AddItem();
       item.p_itemId = "Zune HD";
       item.p_orderId = orderId;

       string orderResult = addProxy.AddItem(item);
       Console.WriteLine("Service returned: " + orderResult);
    }
    ```

5. <span data-ttu-id="65829-213">ソリューションをビルドし、`OrderClient` アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="65829-213">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="65829-214">クライアントに次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="65829-214">The client will display the following text:</span></span>

    ```output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. <span data-ttu-id="65829-215">ワークフローサービスが永続化されていることを確認するには、[ **スタート** ] メニューに移動し、[ **すべてのプログラム**]、 **Microsoft SQL Server 2008**、 **SQL Server Management Studio**] の順に選択して SQL Server Management Studio を開始します。</span><span class="sxs-lookup"><span data-stu-id="65829-215">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>

    1. <span data-ttu-id="65829-216">左側のウィンドウで、[ **データベース**]、[ **SQLPersistenceStore**]、[ **ビュー** ] の順に展開し、 **system.activities.durableinstancing.instances** を右クリックして、[ **上位1000行の選択]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="65829-216">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="65829-217">**結果** ウィンドウで、少なくとも1つのインスタンスが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="65829-217">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="65829-218">実行中に例外が発生した場合は、前の実行のその他のインスタンスがある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65829-218">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="65829-219">既存の行を削除するには、 **system.activities.durableinstancing.instances** を右クリックして [ **上位200行の編集**] を選択し、[ **実行** ] ボタンを押して、結果ペインのすべての行を選択し、[ **削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="65829-219">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="65829-220">データベースに表示されているインスタンスが、アプリケーションで作成されたインスタンスであることを確認するには、クライアントを実行する前に、Instances ビューが空であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="65829-220">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="65829-221">クライアントが実行されると、クエリ ([上位 1000 行を選択]) を再実行し、新しいインスタンスが追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="65829-221">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>

7. <span data-ttu-id="65829-222">Enter キーを押して、項目の追加メッセージをワークフロー サービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="65829-222">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="65829-223">クライアントに次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="65829-223">The client will display the following text:</span></span>

    ```output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a><span data-ttu-id="65829-224">関連項目</span><span class="sxs-lookup"><span data-stu-id="65829-224">See also</span></span>

- [<span data-ttu-id="65829-225">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="65829-225">Workflow Services</span></span>](workflow-services.md)
