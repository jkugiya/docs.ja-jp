---
title: Visual Studio で WCF のデータ サービスを作成する
description: WCF Data Services を使用するサンプル データ サービスを作成し、サンプル データベースに基づいて OData フィードを公開する方法について説明します。
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: 04c91483587c8976e40584474ced2f5474ab89f4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805767"
---
# <a name="create-the-data-service"></a><span data-ttu-id="8eb1d-103">データ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="8eb1d-103">Create the data service</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="8eb1d-104">このトピックでは、WCF Data Services を使用して、Northwind サンプル データベースに基づく Open Data Protocol (OData) フィードを公開するサンプル データ サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-104">In this topic, you create a sample data service that uses WCF Data Services to expose an Open Data Protocol (OData) feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="8eb1d-105">この作業に必要な基本手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-105">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="8eb1d-106">ASP.NET Web アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-106">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="8eb1d-107">Entity Data Model ツールを使用して、データ モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-107">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="8eb1d-108">データ サービスを Web アプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-108">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="8eb1d-109">データ サービスへのアクセスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-109">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="8eb1d-110">ASP.NET Web アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="8eb1d-110">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="8eb1d-111">Visual Studio の **[ファイル]** メニューで､ **[新規作成]**  >  **[プロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-111">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="8eb1d-112">**[新しいプロジェクト]** ダイアログ ボックスで、Visual Basic または Visual C# の **[Web]** カテゴリを選択し、 **[ASP.NET Web アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-112">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="8eb1d-113">プロジェクトの名前として「`NorthwindService`」と入力し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-113">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="8eb1d-114">**[新しい ASP.NET Web アプリケーション]** ダイアログで、 **[空]** を選択し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-114">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="8eb1d-115">(省略可能) Web アプリケーションに対して特定のポート番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-115">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="8eb1d-116">注: この一連のクイックスタート トピックでは、ポート番号 `12345` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-116">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="8eb1d-117">**ソリューション エクスプローラー** で、作成した ASP.NET プロジェクトを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-117">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="8eb1d-118">**[Web]** タブを選択し、 **[ポートを指定する]** ボックスの値を `12345` に設定します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-118">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="8eb1d-119">データ モデルを定義する</span><span class="sxs-lookup"><span data-stu-id="8eb1d-119">Define the data model</span></span>

1. <span data-ttu-id="8eb1d-120">**ソリューション エクスプローラー** で、ASP.NET プロジェクトの名前を右クリックし、 **[追加]**  >  **[新しい項目]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-120">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="8eb1d-121">**[新しい項目の追加]** ダイアログ ボックスで **[データ]** カテゴリを選択し、 **[ADO.NET Entity Data Model]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-121">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="8eb1d-122">データ モデルの名前として「`Northwind.edmx`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-122">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="8eb1d-123">**Entity Data Model ウィザード** で **[データベースの EF デザイナー]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-123">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="8eb1d-124">次のいずれかの手順を実行してデータ モデルをデータベースに接続してから **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-124">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="8eb1d-125">データベース接続がまだ構成されていない場合は、 **[新しい接続]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-125">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="8eb1d-126">詳細については、[SQL Server データベースへの接続を作成する](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-126">For more information, see [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="8eb1d-127">この SQL Server インスタンスには、Northwind サンプル データベースがアタッチされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-127">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="8eb1d-128">\- または</span><span class="sxs-lookup"><span data-stu-id="8eb1d-128">\- or -</span></span>

    - <span data-ttu-id="8eb1d-129">Northwind データベースに接続するようにデータベース接続が既に構成されている場合は、一覧からその接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-129">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="8eb1d-130">ウィザードの最終ページで、データベース内のすべてのテーブルのチェック ボックスをオンにし、ビューおよびストアド プロシージャのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-130">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="8eb1d-131">**[完了]** をクリックして、ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-131">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="8eb1d-132">WCF データ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="8eb1d-132">Create the WCF data service</span></span>

1. <span data-ttu-id="8eb1d-133">**ソリューション エクスプローラー** で、ASP.NET プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-133">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="8eb1d-134">**[新しい項目の追加]** ダイアログ ボックスで、 **[Web]** カテゴリの **[WCF Data Service]** 項目テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-134">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Visual Studio 2015 の WCF Data Service 項目テンプレート](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="8eb1d-136">**WCF Data Service** テンプレートは Visual Studio 2015 で使用できますが、Visual Studio 2017 以降では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-136">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="8eb1d-137">サービスの名前として、「`Northwind`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-137">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="8eb1d-138">Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-138">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="8eb1d-139">既定では、コード エディターのウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-139">By default, the code-editor window opens.</span></span> <span data-ttu-id="8eb1d-140">**ソリューション エクスプローラー** では、このサービスに Northwind という名前が付き、拡張子は *.svc.cs* または *.svc.vb* になります。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-140">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="8eb1d-141">データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindEntities`) で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-141">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="8eb1d-142">クラス定義は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-142">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="8eb1d-143">データ サービス リソースへのアクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="8eb1d-143">Enable access to data service resources</span></span>

1. <span data-ttu-id="8eb1d-144">データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-144">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="8eb1d-145">これにより、承認されたクライアントは、指定したエンティティ セットのリソースに読み取りおよび書き込みアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-145">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8eb1d-146">ASP.NET アプリケーションにアクセスできるクライアントは、データ サービスによって公開されるリソースにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-146">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="8eb1d-147">運用データ サービスで、リソースへの承認されていないアクセスを防止するために、アプリケーション自身もセキュリティで保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-147">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="8eb1d-148">詳細については、「 [Securing WCF Data Services](securing-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-148">For more information, see [Securing WCF Data Services](securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8eb1d-149">次の手順</span><span class="sxs-lookup"><span data-stu-id="8eb1d-149">Next steps</span></span>

<span data-ttu-id="8eb1d-150">ここでは、Northwind サンプル データベースに基づいて、OData フィードを公開する新しいデータ サービスを作成し、ASP.NET Web アプリケーションへのアクセス許可を持つクライアントからフィードへのアクセスを有効にしました。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-150">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="8eb1d-151">次は、Visual Studio からデータ サービスを開始して、Web ブラウザーから HTTP GET 要求を送信して OData フィードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="8eb1d-151">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8eb1d-152">Web ブラウザーからサービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="8eb1d-152">Access the service from a web browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="8eb1d-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="8eb1d-153">See also</span></span>

- <span data-ttu-id="8eb1d-154">[ADO.NET Entity Data Model ツール](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8eb1d-154">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
