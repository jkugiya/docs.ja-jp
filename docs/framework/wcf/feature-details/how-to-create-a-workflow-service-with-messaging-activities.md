---
description: '詳細については、「方法: メッセージングアクティビティを使用してワークフローサービスを作成する」を参照してください。'
title: '方法: メッセージング アクティビティを使用してワークフロー サービスを作成する'
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: c8f01574c2880e3a75a4db8edea949648d49426c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734543"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a><span data-ttu-id="bf3cc-103">方法: メッセージング アクティビティを使用してワークフロー サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="bf3cc-103">How to: Create a Workflow Service with Messaging Activities</span></span>

<span data-ttu-id="bf3cc-104">このトピックでは、メッセージング アクティビティを使用して単純なワークフロー サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-104">This topic describes how to create a simple workflow service using messaging activities.</span></span> <span data-ttu-id="bf3cc-105">ここでは、メッセージング アクティビティだけで構成されるサービスのワークフロー サービスを作成する機構に重点を置きます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-105">This topic focuses on the mechanics of creating a workflow service where the service consists solely of messaging activities.</span></span> <span data-ttu-id="bf3cc-106">実際のサービスでは、ワークフローに他の多くのアクティビティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-106">In a real-world service, the workflow contains many other activities.</span></span> <span data-ttu-id="bf3cc-107">このサービスは、文字列を取得して、それを呼び出し元に返す、Echo という 1 つの操作を実装します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-107">The service implements one operation called Echo, which takes a string and returns the string to the caller.</span></span> <span data-ttu-id="bf3cc-108">このトピックは、一連の 2 つのトピックの最初のものです。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-108">This topic is the first in a series of two topics.</span></span> <span data-ttu-id="bf3cc-109">次のトピック「 [方法: ワークフローアプリケーションからサービスにアクセス](how-to-access-a-service-from-a-workflow-application.md) する」では、このトピックで作成したサービスを呼び出すことができるワークフローアプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-109">The next topic [How To: Access a Service From a Workflow Application](how-to-access-a-service-from-a-workflow-application.md) discusses how to create a workflow application that can call the service created in this topic.</span></span>  
  
### <a name="to-create-a-workflow-service-project"></a><span data-ttu-id="bf3cc-110">ワークフロー サービス プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="bf3cc-110">To create a workflow service project</span></span>  
  
1. <span data-ttu-id="bf3cc-111">Visual Studio 2012 を起動します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-111">Start Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="bf3cc-112">[ **ファイル** ] メニューの [ **新規作成**] をポイントし、[ **プロジェクト** ] をクリックして [ **新しいプロジェクト] ダイアログ** を表示します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-112">Click the **File** menu, select **New**, and then **Project** to display the **New Project Dialog**.</span></span> <span data-ttu-id="bf3cc-113">プロジェクトの種類の一覧から、インストールされているテンプレートと **WCF ワークフローサービスアプリケーション** の一覧から [**ワークフロー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-113">Select **Workflow** from the list of installed templates and **WCF Workflow Service Application** from the list of project types.</span></span> <span data-ttu-id="bf3cc-114">次の図に示すように、プロジェクトにという名前 `MyWFService` を付け、既定の場所を使用します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-114">Name the project `MyWFService` and use the default location as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="bf3cc-115">[ **OK** ] ボタンをクリックして、[ **新しいプロジェクト] ダイアログボックス** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-115">Click the **OK** button to dismiss the **New Project Dialog**.</span></span>  
  
3. <span data-ttu-id="bf3cc-116">プロジェクトが作成されると、次の図に示すように、Service1.xamlx ファイルがデザイナーで開かれます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-116">When the project is created, the Service1.xamlx file is opened in the designer as shown in the following illustration.</span></span>  
  
     ![スクリーンショットは、デザイナーで開かれている Service1 .xamlx ファイルを示しています。](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     <span data-ttu-id="bf3cc-118">[ **シーケンシャルサービス** ] というラベルの付いたアクティビティを右クリックし、[ **削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-118">Right-click the activity labeled **Sequential Service** and select **Delete**.</span></span>  
  
### <a name="to-implement-the-workflow-service"></a><span data-ttu-id="bf3cc-119">ワークフロー サービスを実装するには</span><span class="sxs-lookup"><span data-stu-id="bf3cc-119">To implement the workflow service</span></span>  
  
1. <span data-ttu-id="bf3cc-120">画面の左側にある [ **ツールボックス** ] タブを選択してツールボックスを表示し、プッシュピンをクリックしてウィンドウを開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-120">Select the **Toolbox** tab on the left side of the screen to display the toolbox and click the pushpin to keep the window open.</span></span> <span data-ttu-id="bf3cc-121">次の図に示すように、[ツールボックス] の [ **メッセージング** ] セクションを展開して、メッセージングアクティビティとメッセージングアクティビティテンプレートを表示します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-121">Expand the **Messaging** section of the toolbox to display the messaging activities and the messaging activity templates as shown in the following illustration.</span></span>  
  
     ![メッセージングセクションが展開されたツールボックスを示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2. <span data-ttu-id="bf3cc-123">**Receiveandsendreply** テンプレートをワークフローデザイナーにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-123">Drag and drop a **ReceiveAndSendReply** template to the workflow designer.</span></span> <span data-ttu-id="bf3cc-124">これに <xref:System.Activities.Statements.Sequence> より、次の図に示すように、 **Receive** アクティビティの後にアクティビティが作成さ <xref:System.ServiceModel.Activities.SendReply> れます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-124">This creates a <xref:System.Activities.Statements.Sequence> activity with a **Receive** activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity as shown in the following illustration.</span></span>  
  
     ![ReceiveAndSendReply テンプレートを示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     <span data-ttu-id="bf3cc-126"><xref:System.ServiceModel.Activities.SendReply> アクティビティの <xref:System.ServiceModel.Activities.SendReply.Request%2A> プロパティは `Receive` に設定されています。これは、<xref:System.ServiceModel.Activities.Receive> アクティビティが応答する <xref:System.ServiceModel.Activities.SendReply> アクティビティの名前です。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-126">Notice that the <xref:System.ServiceModel.Activities.SendReply> activity’s <xref:System.ServiceModel.Activities.SendReply.Request%2A> property is set to `Receive`, the name of the <xref:System.ServiceModel.Activities.Receive> activity to which the <xref:System.ServiceModel.Activities.SendReply> activity is replying.</span></span>  
  
3. <span data-ttu-id="bf3cc-127">アクティビティの <xref:System.ServiceModel.Activities.Receive> 種類で、 `Echo` **OperationName** という名前のテキストボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-127">In the <xref:System.ServiceModel.Activities.Receive> activity type `Echo` into the textbox labeled **OperationName**.</span></span> <span data-ttu-id="bf3cc-128">これにより、サービスが実装する操作の名前が定義されます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-128">This defines the name of the operation the service implements.</span></span>  
  
     ![操作名を指定する場所を示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4. <span data-ttu-id="bf3cc-130">アクティビティを選択した状態で、 <xref:System.ServiceModel.Activities.Receive> まだ開いていない場合は [ **表示** ] メニューの [ **プロパティウィンドウ]** をクリックして、[プロパティ] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-130">With the <xref:System.ServiceModel.Activities.Receive> activity selected, open the properties window if not already open by clicking the **View** menu and selecting **Properties Window**.</span></span> <span data-ttu-id="bf3cc-131">[ **プロパティ] ウィンドウ** で、次の図に示すように、 **CanCreateInstance** が表示されるまで下にスクロールし、チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-131">In the **Properties Window** scroll down until you see **CanCreateInstance** and click the checkbox as shown in the following illustration.</span></span> <span data-ttu-id="bf3cc-132">この設定によって、ワークフロー サービス ホストはメッセージが受信されると (必要に応じて) サービスの新しいインスタンスを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-132">This setting enables the workflow service host to create a new instance of the service (if needed) when a message is received.</span></span>  
  
     ![CanCreateInstance プロパティを示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5. <span data-ttu-id="bf3cc-134">アクティビティを選択し、 <xref:System.Activities.Statements.Sequence> デザイナーの左下隅にある [ **変数** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-134">Select the <xref:System.Activities.Statements.Sequence> activity and click the **Variables** button in the lower left corner of the designer.</span></span> <span data-ttu-id="bf3cc-135">これにより、変数エディターが開かれます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-135">This displays the variables editor.</span></span> <span data-ttu-id="bf3cc-136">[ **変数の作成** ] リンクをクリックして、操作に送信される文字列を格納する変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-136">Click the **Create Variable** link to add a variable to store the string sent to the operation.</span></span> <span data-ttu-id="bf3cc-137">次の図に示すように、変数にという名前 `msg` を付け、その **変数** の型を String に設定します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-137">Name the variable `msg` and set its **Variable** type to String as shown in the following illustration.</span></span>  
  
     ![変数を追加する方法を示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     <span data-ttu-id="bf3cc-139">[ **変数** ] ボタンをもう一度クリックして、変数エディターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-139">Click the **Variables** button again to close the variables editor.</span></span>  
  
6. <span data-ttu-id="bf3cc-140">[定義] をクリックし **ます**。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-140">Click the **Define..**</span></span> <span data-ttu-id="bf3cc-141">[コンテンツ定義] ダイアログボックスを表示するには、アクティビティの [**コンテンツ**] テキストボックス内のリンクを選択し <xref:System.ServiceModel.Activities.Receive> ます。 </span><span class="sxs-lookup"><span data-stu-id="bf3cc-141">link in the **Content** text box in the <xref:System.ServiceModel.Activities.Receive> activity to display the **Content Definition** dialog.</span></span> <span data-ttu-id="bf3cc-142">[**パラメーター** ] オプションボタンを選択し、[**新しいパラメーターの追加**] リンクをクリックし、[名前] テキストボックスに「」と入力し `inMsg` ます。次の図に示すように、[**型**] ボックスで [**文字列**] を選択し、[ `msg` **割り当て先**] テキストボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-142">Select the **Parameters** radio button, click the **Add new Parameter** link, type `inMsg` in the **name** text box, select **String** in the **Type** drop down list box, and type `msg` in the **Assign To** text box as shown in the following illustration.</span></span>  
  
     ![パラメーターの内容の追加を示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     <span data-ttu-id="bf3cc-144">これにより、Receive アクティビティが文字列パラメーターを受け取り、そのデータが `msg` 変数にバインドされるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-144">This specifies that the Receive activity receives string parameter and that data is bound to the `msg` variable.</span></span> <span data-ttu-id="bf3cc-145">[ **OK** ] をクリックして、[ **コンテンツ定義** ] ダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-145">Click **OK** to close the **Content Definition** dialog.</span></span>  
  
7. <span data-ttu-id="bf3cc-146">アクティビティの [**コンテンツ**] ボックスの [**定義...** ] リンクをクリックして <xref:System.ServiceModel.Activities.SendReply> 、[**コンテンツ定義**] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-146">Click the **Define...** link in the **Content** box in the <xref:System.ServiceModel.Activities.SendReply> activity to display the **Content Definition** dialog.</span></span> <span data-ttu-id="bf3cc-147">[**パラメーター** ] オプションボタンを選択し、[**新しいパラメーターの追加**] リンクをクリックします。次の図に示すように、[名前] ボックスに「」と入力し、[ `outMsg` **型**] ドロップダウンリストボックスで [**文字列**] を選択し、[  `msg` **値**] テキストボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-147">Select the **Parameters** radio button, click the **Add new Parameter** link, type `outMsg` in the **name** textbox, select **String** in the **Type** dropdown list box, and `msg` in the **Value** text box as shown in the following illustration.</span></span>  
  
     ![OutMsg パラメーターを追加する方法を示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     <span data-ttu-id="bf3cc-149">これにより、<xref:System.ServiceModel.Activities.SendReply> アクティビティがメッセージまたはメッセージ コントラクト型を送信し、そのデータが `msg` 変数にバインドされるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-149">This specifies that the <xref:System.ServiceModel.Activities.SendReply> activity sends a message or message contract type and that data is bound to the `msg` variable.</span></span> <span data-ttu-id="bf3cc-150">これは <xref:System.ServiceModel.Activities.SendReply> アクティビティであるため、`msg` のデータは、アクティビティがクライアントに送り返すメッセージの設定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-150">Because this is a <xref:System.ServiceModel.Activities.SendReply> activity, this means the data in `msg` is used to populate the message the activity sends back to the client.</span></span> <span data-ttu-id="bf3cc-151">[ **OK** ] をクリックして、[ **コンテンツ定義** ] ダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-151">Click **OK** to close the **Content Definition** dialog.</span></span>  
  
8. <span data-ttu-id="bf3cc-152">[ **ビルド** ] メニューの [ **ソリューションのビルド**] をクリックして、ソリューションを保存してビルドします。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-152">Save and build the solution by clicking the **Build** menu and selecting **Build Solution**.</span></span>  
  
## <a name="configure-the-workflow-service-project"></a><span data-ttu-id="bf3cc-153">ワークフロー サービス プロジェクトの構成</span><span class="sxs-lookup"><span data-stu-id="bf3cc-153">Configure the Workflow Service Project</span></span>  

 <span data-ttu-id="bf3cc-154">ワークフロー サービスは完成しました。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-154">The workflow service is complete.</span></span> <span data-ttu-id="bf3cc-155">ここでは、ホストと実行を容易にするように、ワークフロー サービス ソリューションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-155">This section explains how to configure the workflow service solution to make it easy to host and run.</span></span> <span data-ttu-id="bf3cc-156">このソリューションでは、ASP.NET 開発サーバーを使用してサービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-156">This solution uses the ASP.NET Development Server to host the service.</span></span>  
  
#### <a name="to-set-project-start-up-options"></a><span data-ttu-id="bf3cc-157">プロジェクトのスタートアップ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="bf3cc-157">To set project start up options</span></span>  
  
1. <span data-ttu-id="bf3cc-158">**ソリューションエクスプローラー** で、[ **myのサービス**] を右クリックし、[**プロパティ**] をクリックして、[**プロジェクトのプロパティ**] ダイアログボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-158">In the **Solution Explorer**, right-click **MyWFService** and select **Properties** to display the **Project Properties** dialog.</span></span>  
  
2. <span data-ttu-id="bf3cc-159">[ **Web** ] タブを選択し、[**開始動作**] で [**特定のページ**] を選択し、 `Service1.xamlx` 次の図に示すように、テキストボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-159">Select the **Web** tab and select **Specific Page** under **Start Action** and type `Service1.xamlx` in the text box as shown in the following illustration.</span></span>  
  
     ![[プロジェクトのプロパティ] ダイアログボックスが表示されるスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     <span data-ttu-id="bf3cc-161">これにより、ASP.NET 開発サーバーの Service1.xamlx で定義されたサービスがホストされます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-161">This hosts the service defined in Service1.xamlx in the ASP.NET Development Server.</span></span>  
  
3. <span data-ttu-id="bf3cc-162">Ctrl キーを押しながら F5 キーを押して、サービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-162">Press Ctrl + F5 to launch the service.</span></span> <span data-ttu-id="bf3cc-163">次の図に示すように、ASP.NET 開発サーバーのアイコンが、デスクトップの右下側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-163">The ASP.NET Development Server icon is displayed in the lower right side of the desktop as shown in the following image.</span></span>  
  
     ![ASP.NET Developer サーバーアイコンを示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     <span data-ttu-id="bf3cc-165">また、Internet Explorer に、サービスの WCF サービス ヘルプ ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-165">In addition, Internet Explorer displays the WCF Service Help Page for the service.</span></span>  
  
     ![WCF サービスのヘルプページを示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4. <span data-ttu-id="bf3cc-167">「 [方法: ワークフローアプリケーションからサービスにアクセス](how-to-access-a-service-from-a-workflow-application.md) する」のトピックに進み、このサービスを呼び出すワークフロークライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="bf3cc-167">Continue on to the [How To: Access a Service From a Workflow Application](how-to-access-a-service-from-a-workflow-application.md) topic to create a workflow client that calls this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf3cc-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf3cc-168">See also</span></span>

- [<span data-ttu-id="bf3cc-169">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="bf3cc-169">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="bf3cc-170">ワークフロー サービスのホストの概要</span><span class="sxs-lookup"><span data-stu-id="bf3cc-170">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)
- [<span data-ttu-id="bf3cc-171">メッセージング アクティビティ</span><span class="sxs-lookup"><span data-stu-id="bf3cc-171">Messaging Activities</span></span>](messaging-activities.md)
