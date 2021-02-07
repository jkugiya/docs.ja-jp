---
description: '詳細については、「方法: ワークフローアプリケーションからサービスにアクセスする」を参照してください。'
title: '方法: ワークフロー アプリケーションからサービスにアクセスする'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: f8972bf7755c0103d164633d53d8d32508ce2efe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743097"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a><span data-ttu-id="eea6f-103">方法: ワークフロー アプリケーションからサービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="eea6f-103">How To: Access a Service From a Workflow Application</span></span>

<span data-ttu-id="eea6f-104">このトピックでは、ワークフロー コンソール アプリケーションからワークフロー サービスを呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-104">This topic describes how to call a workflow service from a workflow console application.</span></span> <span data-ttu-id="eea6f-105">これは、「 [方法: メッセージングアクティビティを使用してワークフローサービスを作成する](how-to-create-a-workflow-service-with-messaging-activities.md) 」トピックの完了に依存します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-105">It depends on completion of the [How to: Create a Workflow Service with Messaging Activities](how-to-create-a-workflow-service-with-messaging-activities.md) topic.</span></span> <span data-ttu-id="eea6f-106">このトピックでは、ワークフローアプリケーションからワークフローサービスを呼び出す方法について説明しますが、同じメソッドを使用して、ワークフローアプリケーションから任意の Windows Communication Foundation (WCF) サービスを呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-106">Although this topic describes how to call a workflow service from a workflow application, the same methods can be used to call any Windows Communication Foundation (WCF) service from a workflow application.</span></span>

### <a name="create-a-workflow-console-application-project"></a><span data-ttu-id="eea6f-107">ワークフロー コンソール アプリケーション プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="eea6f-107">Create a Workflow Console Application Project</span></span>

1. <span data-ttu-id="eea6f-108">Visual Studio 2012 を起動します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-108">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="eea6f-109">「 [方法: メッセージングアクティビティを使用してワークフローサービスを作成](how-to-create-a-workflow-service-with-messaging-activities.md) する」のトピックで作成した myのサービスプロジェクトを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-109">Load the MyWFService project you created in the [How to: Create a Workflow Service with Messaging Activities](how-to-create-a-workflow-service-with-messaging-activities.md) topic.</span></span>

3. <span data-ttu-id="eea6f-110">**ソリューションエクスプローラー** で **my[サービス**] ソリューションを右クリックし、[**追加**]、[**新しいプロジェクト**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-110">Right click the **MyWFService** solution in the **Solution Explorer** and select **Add**, **New Project**.</span></span> <span data-ttu-id="eea6f-111">プロジェクトの種類の一覧から、[**インストールされたテンプレート** と **ワークフローコンソールアプリケーション**] の [**ワークフロー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-111">Select **Workflow** in the **Installed Templates** and **Workflow Console Application** from the list of project types.</span></span> <span data-ttu-id="eea6f-112">次の図に示すように、プロジェクトに MyWFClient という名前を付け、既定の場所を使用します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-112">Name the project MyWFClient and use the default location as shown in the following illustration.</span></span>

     ![[新しいプロジェクトの追加] ダイアログ](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     <span data-ttu-id="eea6f-114">[ **OK** ] ボタンをクリックして、[ **新しいプロジェクトの追加] ダイアログボックス** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-114">Click the **OK** button to dismiss the **Add New Project Dialog**.</span></span>

4. <span data-ttu-id="eea6f-115">プロジェクトが作成されると、Workflow1.xaml ファイルがデザイナーで開かれます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-115">After the project is created, the Workflow1.xaml file is opened in the designer.</span></span> <span data-ttu-id="eea6f-116">まだ開いていない場合は [ **ツールボックス** ] タブをクリックしてツールボックスを開き、プッシュピンをクリックしてツールボックスウィンドウを開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="eea6f-116">Click the **Toolbox** tab to open the toolbox if it is not already open and click the pushpin to keep the toolbox window open.</span></span>

5. <span data-ttu-id="eea6f-117">**Ctrl** + **F5** キーを押して、サービスをビルドして起動します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-117">Press **Ctrl**+**F5** to build and launch the service.</span></span> <span data-ttu-id="eea6f-118">以前と同様に、ASP.NET 開発サーバーが起動され、Internet Explorer に WCF ヘルプ ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-118">As before, the ASP.NET Development Server is launched and Internet Explorer displays the WCF Help Page.</span></span> <span data-ttu-id="eea6f-119">このページの URI は、次の手順で使用する必要があるため、確認しておいてください。</span><span class="sxs-lookup"><span data-stu-id="eea6f-119">Notice the URI for this page as you must use it in the next step.</span></span>

     ![WCF ヘルプページと URI を表示している IE](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. <span data-ttu-id="eea6f-121">**ソリューションエクスプローラー** で **myのクライアント** プロジェクトを右クリックし、[   >  **サービス参照** の追加] を選択します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-121">Right click the **MyWFClient** project in the **Solution Explorer** and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="eea6f-122">[ **検出** ] ボタンをクリックして、現在のソリューションで任意のサービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-122">Click the **Discover** button to search the current solution for any services.</span></span> <span data-ttu-id="eea6f-123">[サービス] ボックスで、Service1.xamlx の横にある三角形をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eea6f-123">Click the triangle next to Service1.xamlx in the Services list.</span></span> <span data-ttu-id="eea6f-124">Service1 の横にある三角形をクリックして、Service1 サービスによって実装されるコントラクトの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-124">Click the triangle next to Service1 to list the contracts implemented by the Service1 service.</span></span> <span data-ttu-id="eea6f-125">**サービス** の一覧で [ **Service1** ] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-125">Expand the **Service1** node in the **Services** list.</span></span> <span data-ttu-id="eea6f-126">次の図に示すように、Echo 操作は **操作** の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-126">The Echo operation is displayed in the **Operations** list as shown in the following illustration.</span></span>

     ![[サービス参照の追加] ダイアログ](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     <span data-ttu-id="eea6f-128">既定の名前空間をそのままにし、[ **OK** ] をクリックして [ **サービス参照の追加** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-128">Keep the default namespace and click **OK** to dismiss the **Add Service Reference** dialog.</span></span> <span data-ttu-id="eea6f-129">次のダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-129">The following dialog is displayed.</span></span>

     ![サービス参照の追加通知ダイアログ](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     <span data-ttu-id="eea6f-131">[ **OK** ] をクリックしてダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-131">Click **OK** to dismiss the dialog.</span></span> <span data-ttu-id="eea6f-132">次に、Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="eea6f-132">Next, press CTRL+SHIFT+B to build the solution.</span></span> <span data-ttu-id="eea6f-133">ツールボックスに、 **[servicereference1]** という名前の新しいセクションが追加されました。</span><span class="sxs-lookup"><span data-stu-id="eea6f-133">Notice in the toolbox a new section has been added called **MyWFClient.ServiceReference1.Activities**.</span></span> <span data-ttu-id="eea6f-134">この選択肢を展開して、次の図のように、追加されている Echo アクティビティを確認します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-134">Expand this section and notice the Echo activity that has been added as shown in the following illustration.</span></span>

     ![ツールボックスの Echo アクティビティ](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. <span data-ttu-id="eea6f-136"><xref:System.Activities.Statements.Sequence> アクティビティをデザイナー画面にドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="eea6f-136">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the designer surface.</span></span> <span data-ttu-id="eea6f-137">これは、ツールボックスの [ **制御フロー** ] セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="eea6f-137">It is under the **Control Flow** section of the toolbox.</span></span>

8. <span data-ttu-id="eea6f-138">アクティビティがフォーカスされた状態で、 <xref:System.Activities.Statements.Sequence> [ **変数** ] リンクをクリックし、という名前の文字列変数を追加し `inString` ます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-138">With the <xref:System.Activities.Statements.Sequence> activity in focus, click the **Variables** link and add a string variable named `inString`.</span></span> <span data-ttu-id="eea6f-139">`"Hello, world"`次の図に示すように、変数にの既定値とという名前の文字列変数を指定し `outString` ます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-139">Give the variable a default value of `"Hello, world"` as well as a string variable named `outString` as shown in the following diagram.</span></span>

     ![InString 変数の追加](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. <span data-ttu-id="eea6f-141">**Echo** アクティビティをにドラッグアンドドロップし <xref:System.Activities.Statements.Sequence> ます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-141">Drag and drop an **Echo** activity into the <xref:System.Activities.Statements.Sequence>.</span></span> <span data-ttu-id="eea6f-142">`inMsg` `inString` `outMsg` 次の図に示すように、[プロパティ] ウィンドウで、引数を変数に、引数を変数にバインドし `outString` ます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-142">In the properties window bind the `inMsg` argument to the `inString` variable and the `outMsg` argument to the `outString` variable as shown in the following illustration.</span></span> <span data-ttu-id="eea6f-143">これにより、`inString` 変数の値を操作に渡し、戻り値を取得し、その戻り値を `outString` 変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-143">This passes in the value of the `inString` variable to the operation and then takes the return value and places it in the `outString` variable.</span></span>

     ![変数への引数のバインド](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. <span data-ttu-id="eea6f-145">**WriteLine** アクティビティを **Echo** アクティビティの下にドラッグアンドドロップして、サービス呼び出しによって返された文字列を表示します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-145">Drag and drop a **WriteLine** activity below the **Echo** activity to display the string returned by the service call.</span></span> <span data-ttu-id="eea6f-146">**WriteLine** アクティビティは、[ツールボックス] の [**プリミティブ**] ノードにあります。</span><span class="sxs-lookup"><span data-stu-id="eea6f-146">The **WriteLine** activity is located in the **Primitives** node in the toolbox.</span></span> <span data-ttu-id="eea6f-147">Writeline アクティビティのテキストボックスに「」と入力して、 **writeline** アクティビティの **text** 引数を変数にバインド `outString` `outString` します。 </span><span class="sxs-lookup"><span data-stu-id="eea6f-147">Bind the **Text** argument of the **WriteLine** activity to the `outString` variable by typing `outString` into the text box on the **WriteLine** activity.</span></span> <span data-ttu-id="eea6f-148">この時点で、ワークフローは次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="eea6f-148">The workflow should now look like the following illustration.</span></span>

     ![完全なクライアント ワークフロー](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. <span data-ttu-id="eea6f-150">My[サービス] ソリューションを右クリックし、[**スタートアッププロジェクトの設定**...] を選択します。[**マルチスタートアッププロジェクト**] オプションボタンを選択し、次の図に示すように、[**アクション**] 列の各プロジェクトに対して [**開始**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-150">Right-click the MyWFService solution and select **Set Startup Projects ...**. Select the **Multiple startup projects** radio button and select **Start** for each project in the **Action** column as shown in the following illustration.</span></span>

     ![スタートアップ プロジェクトのオプション](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. <span data-ttu-id="eea6f-152">Ctrl キーを押しながら F5 キーを押し、サービスとクライアントの両方を起動します。</span><span class="sxs-lookup"><span data-stu-id="eea6f-152">Press Ctrl + F5 to launch both the service and the client.</span></span> <span data-ttu-id="eea6f-153">ASP.NET 開発サーバーがサービスをホストし、Internet Explorer に WCF ヘルプページが表示され、クライアントワークフローアプリケーションがコンソールウィンドウで起動され、サービスから返された文字列 ("Hello, world") が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eea6f-153">The ASP.NET Development Server hosts the service, Internet Explorer displays the WCF help page, and the client workflow application is launched in a console window and displays the string returned from the service ("Hello, world").</span></span>

## <a name="see-also"></a><span data-ttu-id="eea6f-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="eea6f-154">See also</span></span>

- [<span data-ttu-id="eea6f-155">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="eea6f-155">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="eea6f-156">方法: メッセージング アクティビティを使用してワークフロー サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="eea6f-156">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="eea6f-157">Web プロジェクトでのワークフローからの WCF サービスの使用</span><span class="sxs-lookup"><span data-stu-id="eea6f-157">Consuming a WCF Service from a Workflow in a Web Project</span></span>](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
