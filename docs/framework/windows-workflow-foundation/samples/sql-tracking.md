---
description: '詳細情報: SQL 追跡'
title: SQL 追跡
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 2b336839b9c63c0b7bde8b6451add00cb353fec6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741745"
---
# <a name="sql-tracking"></a><span data-ttu-id="e05cc-103">SQL 追跡</span><span class="sxs-lookup"><span data-stu-id="e05cc-103">SQL tracking</span></span>

<span data-ttu-id="e05cc-104">このサンプルでは、SQL データベースに追跡レコードを書き込むカスタム SQL 追跡参加要素を記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e05cc-104">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="e05cc-105">Windows Workflow Foundation (WF) は、ワークフローインスタンスの実行の可視性を得るためのワークフロー追跡機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="e05cc-105">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="e05cc-106">追跡ランタイムでは、ワークフローの実行中にワークフロー追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-106">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="e05cc-107">ワークフロー追跡の詳細については、「 [ワークフローの追跡とトレース](../workflow-tracking-and-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e05cc-107">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="e05cc-108">サンプルを使用する</span><span class="sxs-lookup"><span data-stu-id="e05cc-108">Use the sample</span></span>

1. <span data-ttu-id="e05cc-109">SQL Server 2008、SQL Server 2008 Express、またはそれ以降のバージョンがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e05cc-109">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="e05cc-110">サンプルと共にパッケージ化されているスクリプトは、SQL Express インスタンスをローカル コンピューターで使用していることが前提になります。</span><span class="sxs-lookup"><span data-stu-id="e05cc-110">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="e05cc-111">別のインスタンスがある場合は、データベース関連のスクリプトを変更してからサンプルを実行してください。</span><span class="sxs-lookup"><span data-stu-id="e05cc-111">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="e05cc-112">Scripts ディレクトリ (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 内で Trackingsetup.cmd を実行して SQL Server 追跡データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="e05cc-112">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="e05cc-113">これによって、TrackingSample という名前のデータベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-113">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e05cc-114">このスクリプトでは、SQL Express の既定のインスタンスにデータベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-114">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="e05cc-115">別のデータベース インスタンスにインストールする場合は、Trackingsetup.cmd スクリプトを編集してください。</span><span class="sxs-lookup"><span data-stu-id="e05cc-115">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="e05cc-116">Visual Studio 2010 で SqlTrackingSample .sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-116">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="e05cc-117">**Ctrl** + **Shift** + **B** キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="e05cc-117">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="e05cc-118">**F5** キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e05cc-118">Press **F5** to run the application.</span></span>

   <span data-ttu-id="e05cc-119">ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-119">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="e05cc-120">ブラウザーで、StockPriceService.xamlx をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e05cc-120">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="e05cc-121">ブラウザーに、[StockPriceService] ページが表示され、ローカル サービスの WSDL アドレスが示されます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-121">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="e05cc-122">このアドレスをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e05cc-122">Copy this address.</span></span>

   <span data-ttu-id="e05cc-123">ローカルサービスの WSDL アドレスの例は、 `http://localhost:65193/StockPriceService.xamlx?wsdl` です。</span><span class="sxs-lookup"><span data-stu-id="e05cc-123">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="e05cc-124">エクスプローラーを使用して、WCF テストクライアント (WcfTestClient.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="e05cc-124">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="e05cc-125">これは、 *Microsoft Visual Studio 10.0 \ Common7\IDE ディレクトリ* にあります。</span><span class="sxs-lookup"><span data-stu-id="e05cc-125">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="e05cc-126">WCF テストクライアントで、[ **ファイル** ] メニューをクリックし、[ **サービスの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e05cc-126">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="e05cc-127">テキスト ボックスにローカル サービスのアドレスを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-127">Paste the local service address in the textbox.</span></span> <span data-ttu-id="e05cc-128">[**OK**] をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-128">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="e05cc-129">WCF テストクライアントで、[ **Getstockprice**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e05cc-129">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="e05cc-130">これにより、 `GetStockPrice` 1 つのパラメーターを受け取る操作が開き、値を入力 `Contoso` して、[ **呼び出し**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e05cc-130">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="e05cc-131">出力された追跡レコードが SQL データベースに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-131">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="e05cc-132">追跡レコードを表示するには、SQL Management Studio で TrackingSample データベースを開き、テーブルに移動します。</span><span class="sxs-lookup"><span data-stu-id="e05cc-132">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="e05cc-133">テーブルで選択クエリを実行すると、それぞれのテーブルに格納されている追跡レコード内のデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-133">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="e05cc-134">SQL Server Management Studio の詳細については、「 [SQL Server Management Studio の概要](/sql/ssms/sql-server-management-studio-ssms)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e05cc-134">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="e05cc-135">SQL Server Management Studio [こちら](https://aka.ms/ssmsfullsetup)からダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="e05cc-135">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="e05cc-136">サンプルをアンインストールする</span><span class="sxs-lookup"><span data-stu-id="e05cc-136">Uninstall the sample</span></span>

1. <span data-ttu-id="e05cc-137">サンプル *ディレクトリ (-*----------/) で、スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="e05cc-137">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="e05cc-138">Trackingcleanup.cmd は、ローカル コンピューターの SQL Express 内にあるデータベースを削除しようとします。</span><span class="sxs-lookup"><span data-stu-id="e05cc-138">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="e05cc-139">別の SQL Server インスタンスを使用している場合は、Trackingcleanup.cmd を編集します。</span><span class="sxs-lookup"><span data-stu-id="e05cc-139">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e05cc-140">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e05cc-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e05cc-141">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e05cc-141">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e05cc-142">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="e05cc-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e05cc-143">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e05cc-143">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="e05cc-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="e05cc-144">See also</span></span>

- <span data-ttu-id="e05cc-145">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e05cc-145">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
