---
description: '詳細情報: 方法:IIS 上で実行する WCF Data Service を開発する'
title: '方法: IIS 上で実行する WCF Data Service を開発する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: b4d7b322a00e3c9c43005a416c608e1b98f1ce51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765478"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="be7b7-103">方法: IIS 上で実行する WCF Data Service を開発する</span><span class="sxs-lookup"><span data-stu-id="be7b7-103">How to: Develop a WCF data service running on IIS</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="be7b7-104">この記事では、WCF Data Services を使用して、Northwind サンプル データベースに基づいてデータ サービスを作成する方法を示します。このサンプル データベースは、インターネット インフォメーション サービス (IIS) 上で実行されている ASP.NET Web アプリによってホストされます。</span><span class="sxs-lookup"><span data-stu-id="be7b7-104">This article shows how to use WCF Data Services to create a data service that's based on the Northwind sample database that's hosted by an ASP.NET Web app running on Internet Information Services (IIS).</span></span> <span data-ttu-id="be7b7-105">同じ Northwind データ サービスを ASP.NET 開発サーバーで実行する ASP.NET Web アプリとして作成する方法の例については、[WCF Data Services のクイックスタート](quickstart-wcf-data-services.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be7b7-105">For an example of how to create the same Northwind data service as an ASP.NET Web app that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="be7b7-106">Northwind データ サービスを作成するには、まず、ローカル コンピューターに Northwind サンプル データベースをインストールします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-106">To create the Northwind data service, first install the Northwind sample database on the local computer.</span></span> <span data-ttu-id="be7b7-107">データベースをインストールするには、[Microsoft SQL Serverの Northwind および pubs サンプル データベース](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)から Transact-SQL スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-107">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

<span data-ttu-id="be7b7-108">この記事では、Entity Framework プロバイダーを使用してデータ サービスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-108">This article shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="be7b7-109">その他のデータ サービス プロバイダーを利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="be7b7-109">Other data services providers are available.</span></span> <span data-ttu-id="be7b7-110">詳細については、「[Data Services プロバイダー](data-services-providers-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be7b7-110">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="be7b7-111">サービスを作成した後に、データ サービス リソースへのアクセスを明示的に提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be7b7-111">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="be7b7-112">詳細については、[データ サービスへのアクセスを有効にする](how-to-enable-access-to-the-data-service-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be7b7-112">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="be7b7-113">IIS 上で実行する ASP.NET Web アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="be7b7-113">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="be7b7-114">Visual Studio の **[ファイル]** メニューで､ **[新規作成]**  >  **[プロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-114">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="be7b7-115">**[新しいプロジェクト]** ダイアログ ボックスで、 **[インストール済み]** > [**Visual C#** または **Visual Basic**] > **[Web]** カテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-115">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="be7b7-116">**[ASP.NET Web アプリケーション]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-116">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="be7b7-117">プロジェクトの名前として「`NorthwindService`」を入力します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-117">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="be7b7-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-118">Click **OK**.</span></span>

6. <span data-ttu-id="be7b7-119">**[プロジェクト]** メニューで **[NorthwindService のプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-119">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="be7b7-120">**[Web]** タブで **[ローカル IIS Web サーバーを使用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-120">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="be7b7-121">**[仮想ディレクトリの作成]** 、 **[OK]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-121">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="be7b7-122">管理特権を持つコマンド プロンプトから、次のコマンドを実行します (オペレーティング システムによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="be7b7-122">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="be7b7-123">32 ビット システム:</span><span class="sxs-lookup"><span data-stu-id="be7b7-123">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="be7b7-124">64 ビット システム:</span><span class="sxs-lookup"><span data-stu-id="be7b7-124">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="be7b7-125">これにより、コンピューターに Windows Communication Foundation (WCF) が登録されます。</span><span class="sxs-lookup"><span data-stu-id="be7b7-125">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="be7b7-126">管理特権を持つコマンド プロンプトから、次のコマンドを実行します (オペレーティング システムによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="be7b7-126">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="be7b7-127">32 ビット システム:</span><span class="sxs-lookup"><span data-stu-id="be7b7-127">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="be7b7-128">64 ビット システム:</span><span class="sxs-lookup"><span data-stu-id="be7b7-128">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="be7b7-129">これにより、WCF がコンピューターにインストールされた後、IIS は正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="be7b7-129">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="be7b7-130">IIS の再起動が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="be7b7-130">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="be7b7-131">ASP.NET アプリケーションが IIS7 で実行されると、次の手順も実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be7b7-131">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="be7b7-132">IIS マネージャーを開いて **[既定の Web サイト]** の下にある PhotoService アプリケーションに移動します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-132">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="be7b7-133">**[機能ビュー]** で、 **[認証]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-133">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="be7b7-134">**[認証]** ページで、 **[匿名認証]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-134">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="be7b7-135">**[操作]** ペインで **[編集]** をクリックして、匿名ユーザーがサイトに接続するときのセキュリティ プリンシパルを設定します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-135">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="be7b7-136">**[匿名認証資格情報の編集]** ダイアログ ボックスで、 **[アプリケーション プール ID]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-136">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="be7b7-137">ネットワーク サービス アカウントを使用する際、そのアカウントに関連するすべての内部ネットワーク アクセス権を匿名ユーザーに付与します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-137">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="be7b7-138">SQL Server Management Studio、sqlcmd.exe ユーティリティ、または Visual Studio の Transact-SQL エディターを使用して、Northwind データベースがアタッチされた SQL Server のインスタンスに対して次の Transact-SQL コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-138">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="be7b7-139">これにより、IIS の実行に使用される Windows アカウントに対して、SQL Server インスタンスのログインが作成されます。</span><span class="sxs-lookup"><span data-stu-id="be7b7-139">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="be7b7-140">IIS は、これを使用して SQL Server インスタンスに接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="be7b7-140">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="be7b7-141">Northwind データベースをアタッチして、次の Transact-SQL コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-141">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

    ```sql
    USE Northwind
    GO
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];
    GO
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]
    WITH DEFAULT_DATABASE=[Northwind];
    GO
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    ```

    <span data-ttu-id="be7b7-142">これにより、新しいログインに権限が付与され、IIS は Northwind データベースに対してデータの読み取りおよび書き込みを行うことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="be7b7-142">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="be7b7-143">データ モデルを定義する</span><span class="sxs-lookup"><span data-stu-id="be7b7-143">Define the data model</span></span>

1. <span data-ttu-id="be7b7-144">**ソリューション エクスプローラー** で、ASP.NET プロジェクトの名前を右クリックし、 **[追加]**  >  **[新しい項目]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-144">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="be7b7-145">**[新しい項目の追加]** ダイアログ ボックスで **[ADO.NET エンティティ データ モデル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-145">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="be7b7-146">データ モデルの名前として「`Northwind.edmx`」を入力します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-146">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="be7b7-147">Entity Data Model ウィザードで **[データベースから生成する]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-147">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="be7b7-148">次のいずれかの手順を実行してデータ モデルをデータベースに接続してから **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-148">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="be7b7-149">データベース接続がまだ構成されていない場合は、 **[新しい接続]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-149">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="be7b7-150">詳細については、[SQL Server データベースへの接続を作成する](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be7b7-150">For more information, see [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="be7b7-151">この SQL Server インスタンスには、Northwind サンプル データベースがアタッチされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="be7b7-151">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="be7b7-152">\- または</span><span class="sxs-lookup"><span data-stu-id="be7b7-152">\- or -</span></span>

    - <span data-ttu-id="be7b7-153">Northwind データベースに接続するようにデータベース接続が既に構成されている場合は、一覧からその接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-153">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="be7b7-154">ウィザードの最終ページで、データベース内のすべてのテーブルのチェック ボックスをオンにし、ビューおよびストアド プロシージャのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-154">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="be7b7-155">**[完了]** をクリックして、ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-155">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="be7b7-156">データ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="be7b7-156">Create the data service</span></span>

1. <span data-ttu-id="be7b7-157">**ソリューション エクスプローラー** で、ASP.NET プロジェクトの名前を右クリックし、 **[追加]**  >  **[新しい項目]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-157">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="be7b7-158">**[新しい項目の追加]** ダイアログ ボックスで、 **[WCF Data Service]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be7b7-158">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Visual Studio 2015 の WCF Data Service 項目テンプレート](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="be7b7-160">**WCF Data Service** テンプレートは Visual Studio 2015 で使用できますが、Visual Studio 2017 以降では使用できません。</span><span class="sxs-lookup"><span data-stu-id="be7b7-160">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="be7b7-161">サービスの名前として、「`Northwind`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="be7b7-161">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="be7b7-162">Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="be7b7-162">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="be7b7-163">既定では、コード エディターのウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="be7b7-163">By default, the code-editor window opens.</span></span> <span data-ttu-id="be7b7-164">**ソリューション エクスプローラー** では、このサービスに Northwind という名前が付き、拡張子は .svc.cs または .svc.vb になります。</span><span class="sxs-lookup"><span data-stu-id="be7b7-164">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="be7b7-165">データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindEntities`) で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="be7b7-165">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="be7b7-166">クラス定義は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="be7b7-166">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="be7b7-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="be7b7-167">See also</span></span>

- [<span data-ttu-id="be7b7-168">サービスとしてのデータの公開</span><span class="sxs-lookup"><span data-stu-id="be7b7-168">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
