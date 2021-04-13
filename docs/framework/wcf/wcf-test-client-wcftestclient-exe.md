---
title: WCF のテスト用クライアント (WcfTestClient.exe)
description: WCF サービス ホストと組み合わせた場合にシームレスにサービスをテストできるようになる WCF テスト クライアントについて説明します。 クライアント テストの値を送信し、サービスの応答を表示します。
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: f583d20edf7eeea87ae1dbf63a3cadef05912833
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264128"
---
# <a name="wcf-test-client-wcftestclientexe"></a><span data-ttu-id="75e91-104">WCF のテスト用クライアント (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="75e91-104">WCF Test Client (WcfTestClient.exe)</span></span>

<span data-ttu-id="75e91-105">Windows Communication Foundation (WCF) のテスト クライアント (WcfTestClient.exe) は、テスト パラメーターを入力し、その入力をサービスに送信して、サービスから返される応答を表示できる GUI ツールです。</span><span class="sxs-lookup"><span data-stu-id="75e91-105">Windows Communication Foundation (WCF) Test Client (WcfTestClient.exe) is a GUI tool that enables users to input test parameters, submit that input to the service, and view the response that the service sends back.</span></span> <span data-ttu-id="75e91-106">WCF サービス ホストと組み合わせて使用すると、サービスをシームレスにテストできるようになります。</span><span class="sxs-lookup"><span data-stu-id="75e91-106">It provides a seamless service testing experience when combined with WCF Service Host.</span></span>

<span data-ttu-id="75e91-107">通常、WCF テスト クライアント (WcfTestClient.exe) は次の場所にあります: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` - Community は、インストールされている Visual Studio のレベルに応じて、"Enterprise"、"Professional"、または "Community" のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="75e91-107">You can typically find the WCF Test Client (WcfTestClient.exe) in the following location: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` - Community may be one of "Enterprise", "Professional" or "Community" depending on which level of Visual Studio is installed.</span></span>

## <a name="scenarios-for-using-test-client"></a><span data-ttu-id="75e91-108">テスト用クライアントを使用するシナリオ</span><span class="sxs-lookup"><span data-stu-id="75e91-108">Scenarios for Using Test Client</span></span>

<span data-ttu-id="75e91-109">以下のセクションで、WCF テスト クライアントを使用して開発プロセスを効率化できる最も一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="75e91-109">The following sections discuss the most common scenarios in which you can use WCF Test Client to streamline your development process.</span></span>

### <a name="inside-visual-studio"></a><span data-ttu-id="75e91-110">Visual Studio 内</span><span class="sxs-lookup"><span data-stu-id="75e91-110">Inside Visual Studio</span></span>

#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a><span data-ttu-id="75e91-111">WCF サービス ホストが、1 つのサービスを使用する WCF のテスト用クライアントを開始する</span><span class="sxs-lookup"><span data-stu-id="75e91-111">WCF Service Host Starts WCF Test Client with a Single Service</span></span>

<span data-ttu-id="75e91-112">新しい WCF サービス プロジェクトを作成し、F5 キーを押してデバッガーを起動すると、WCF サービス ホストがプロジェクトのサービスのホストを開始します。</span><span class="sxs-lookup"><span data-stu-id="75e91-112">After you create a new WCF service project and press F5 to start the debugger, the WCF Service Host begins to host the service in your project.</span></span> <span data-ttu-id="75e91-113">その後、WCF テスト クライアントが開き、構成ファイルに定義されているサービス エンドポイントの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-113">Then, WCF Test Client opens and displays a list of service endpoints defined in the configuration file.</span></span> <span data-ttu-id="75e91-114">ユーザーは、パラメーターをテストしてサービスを呼び出すことができ、このプロセスを繰り返して、サービスのテストおよび検証を継続的に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="75e91-114">You can test the parameters and invoke the service, and repeat this process to continuously test and validate your service.</span></span>

#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a><span data-ttu-id="75e91-115">WCF サービス ホストが、複数のサービスを使用する WCF のテスト用クライアントを開始する</span><span class="sxs-lookup"><span data-stu-id="75e91-115">WCF Service Host Starts WCF Test Client with Multiple Services</span></span>

<span data-ttu-id="75e91-116">WCF テスト クライアントは、複数のサービスを含むサービス プロジェクトをデバッグするためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="75e91-116">You can also use WCF Test Client to help debug a service project that contains multiple services.</span></span> <span data-ttu-id="75e91-117">WCF テスト クライアントは、開始されると、プロジェクトのサービスのリストを自動的に反復処理し、テストするためにそれらを開きます。</span><span class="sxs-lookup"><span data-stu-id="75e91-117">When WCF Test Client opens, it automatically iterates the list of services in your project and opens them for testing.</span></span>

### <a name="outside-visual-studio"></a><span data-ttu-id="75e91-118">Visual Studio の外部</span><span class="sxs-lookup"><span data-stu-id="75e91-118">Outside Visual Studio</span></span>

<span data-ttu-id="75e91-119">WCF テスト クライアント (WcfTestClient.exe) を Visual Studio の外部で呼び出して、インターネット上の任意のサービスをテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="75e91-119">You can also invoke the WCF Test Client (WcfTestClient.exe) outside Visual Studio to test an arbitrary service on the Internet.</span></span> <span data-ttu-id="75e91-120">このツールを見つけるには、次の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="75e91-120">To locate the tool, go to the following location:</span></span>

<span data-ttu-id="75e91-121">`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (Community は、マシンにインストールされている Visual Studio のレベルに応じて、"Enterprise"、"Professional"、または "Community" のいずれかになります)</span><span class="sxs-lookup"><span data-stu-id="75e91-121">`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (where community can be one of "Enterprise", "Professional" or "Community" depending on which level of Visual Studio is installed on the machine)</span></span>

<span data-ttu-id="75e91-122">ツールを使用するには、ファイル名をダブルクリックしてこの場所からツールを開くか、コマンド ラインからツールを起動します。</span><span class="sxs-lookup"><span data-stu-id="75e91-122">To use the tool, double-click the file name to open it from this location, or launch it from a command line.</span></span>

<span data-ttu-id="75e91-123">WCF テスト クライアントは、任意の数の URI をコマンド ライン引数として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="75e91-123">WCF Test Client takes an arbitrary number of URIs as command line arguments.</span></span>  <span data-ttu-id="75e91-124">これらの引数には、テストできるサービスの URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="75e91-124">These are the URIs of services that can be tested.</span></span>

`wcfTestClient.exe URI1 URI2 …`

<span data-ttu-id="75e91-125">[WCF テスト クライアント] ウィンドウが開いたら、 **[ファイル]** -> **[サービスの追加]** をクリックし、開くサービスのエンドポイント アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="75e91-125">After the WCF Test Client window is opened, click **File**->**Add Service**, and enter the endpoint address of the service you want to open.</span></span>

## <a name="wcf-test-client-user-interface"></a><span data-ttu-id="75e91-126">WCF のテスト用クライアントのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75e91-126">WCF Test Client User Interface</span></span>

<span data-ttu-id="75e91-127">1 つのサービスまたは複数のサービスを使用する WCF テスト クライアントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="75e91-127">You can use WCF Test Client with a single service or multiple services.</span></span>

### <a name="service-operations"></a><span data-ttu-id="75e91-128">サービス操作</span><span class="sxs-lookup"><span data-stu-id="75e91-128">Service Operations</span></span>

<span data-ttu-id="75e91-129">WCF テスト クライアントのメイン ウィンドウの左ペインには、使用できるすべてのサービスが、それぞれのエンドポイントおよび操作と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-129">The left pane of the WCF Test Client main window lists all the available services, along with their respective endpoints and operations.</span></span>

<span data-ttu-id="75e91-130">操作をダブルクリックすると、その操作の名前が付いた新しいタブ内の右ペインで、操作の内容を表示できます。</span><span class="sxs-lookup"><span data-stu-id="75e91-130">When you double-click an operation, you can view its content in the right pane inside a new tab with the operation's name.</span></span>

<span data-ttu-id="75e91-131">左ペインには、クライアントの構成ファイルも表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-131">The left pane also lists client configuration files.</span></span> <span data-ttu-id="75e91-132">いずれかの項目をダブルクリックすると、右ペインの新しいタブ付きウィンドウにファイルの内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-132">Double-click any of the items to display the content of the file in a new tabbed window in the right pane.</span></span>

### <a name="entering-test-parameters"></a><span data-ttu-id="75e91-133">テスト パラメーターの入力</span><span class="sxs-lookup"><span data-stu-id="75e91-133">Entering Test Parameters</span></span>

<span data-ttu-id="75e91-134">テスト パラメーターを表示するには、右ペインで操作をダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="75e91-134">To view the test parameters, double-click an operation to open it in the right pane.</span></span> <span data-ttu-id="75e91-135">既定では、パラメーターは **[書式付き]** ビューで表示されます。サービスをテストするためのパラメーターに任意の値を入力できます。</span><span class="sxs-lookup"><span data-stu-id="75e91-135">The parameters are showed in **Formatted** view by default, and you can enter arbitrary values for the parameters to test the service.</span></span>

<span data-ttu-id="75e91-136">メッセージの XML を表示するには、 **[XML]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75e91-136">To view the message's XML, click **XML**.</span></span> <span data-ttu-id="75e91-137">それらをサービスに送信するには、 **[起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75e91-137">To send them to the service, click **Invoke**.</span></span>

<span data-ttu-id="75e91-138">DataSet パラメーターの場合は、 **[...]**</span><span class="sxs-lookup"><span data-stu-id="75e91-138">For a DataSet parameter, click the **…**</span></span> <span data-ttu-id="75e91-139">ボタン ( **[編集]** の横にあります)</span><span class="sxs-lookup"><span data-stu-id="75e91-139">button next to **Edit…**</span></span> <span data-ttu-id="75e91-140">をクリックして、DataGrid を表示する新しいウィンドウ内で編集します。</span><span class="sxs-lookup"><span data-stu-id="75e91-140">to edit it in a new window showing the DataGrid.</span></span> <span data-ttu-id="75e91-141">**[DataSet のコピー]** ボタンおよび **[DataSet の貼り付け]** ボタンが表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="75e91-141">Notice the appearance of the **Copy DataSet** and **Paste DataSet** buttons.</span></span> <span data-ttu-id="75e91-142">最初の編集時に DataSet オブジェクトのスキーマが不明の場合、DataGrid は空になります。</span><span class="sxs-lookup"><span data-stu-id="75e91-142">If the schema of the DataSet object is unknown upon the first edit, the DataGrid is empty.</span></span> <span data-ttu-id="75e91-143">スキーマが同じ DataSet オブジェクトを DataGrid の現在のオブジェクトに貼り付ける必要があります </span><span class="sxs-lookup"><span data-stu-id="75e91-143">You have to paste a DataSet object with the same schema into the current object in the DataGrid.</span></span> <span data-ttu-id="75e91-144">(スキーマは、貼り付け操作の前に別の場所からコピーする必要があることに注意してください。) **[DataSet のコピー]** ボタンをクリックすることでも、将来使用する Dataset オブジェクトをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="75e91-144">(Notice that you need to copy the schema from somewhere else before the paste operation.) You can also copy a Dataset object for future usage by clicking the **Copy DataSet** button.</span></span>

<span data-ttu-id="75e91-145">サービスの応答がテスト パラメーターの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-145">The service's response appears below the test parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="75e91-146">想定される戻り値が文字列の場合、入力が引用符で囲まれていなくても、結果は引用符で囲まれた文字列として表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-146">If the expected return value is a string, the result will be displayed as a quoted string even though the input provided was not in quotes.</span></span>

<span data-ttu-id="75e91-147">サービスのコントラクトの作成時に特定の操作を一方向として指定した場合は、サービスの応答は表示されません。</span><span class="sxs-lookup"><span data-stu-id="75e91-147">If you specified a particular operation as one-way when you created the contract for the service, no service response is displayed.</span></span> <span data-ttu-id="75e91-148">メッセージが配信のキューに置かれると、メッセージが正常に送信されたことを通知するダイアログ ボックスがすぐに表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-148">As soon as the message is queued for delivery, a dialog box pops up to notify you that the message was successfully sent.</span></span>

### <a name="session-support"></a><span data-ttu-id="75e91-149">セッション サポート</span><span class="sxs-lookup"><span data-stu-id="75e91-149">Session Support</span></span>

<span data-ttu-id="75e91-150">サービス操作のタブにある **[新しいプロキシを開始する]** チェック ボックスを使用すると、セッション サポートを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="75e91-150">The **Start a new proxy** check box in a service operation's tab enables you to toggle session support.</span></span> <span data-ttu-id="75e91-151">既定では、このチェック ボックスはオフになります。</span><span class="sxs-lookup"><span data-stu-id="75e91-151">This box is cleared by default.</span></span>

<span data-ttu-id="75e91-152">特定の操作 (または同じサービス エンドポイントの別の操作) に対するテスト パラメーターを入力し、チェック ボックスがオフの状態で **[起動]** を 2 回以上クリックした場合、これらの操作は単一のプロキシを共有し、サービスの状態は複数の操作にわたって保持されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-152">When you enter test parameters for a specific operation (or another operation in the same service endpoint) and click **Invoke** multiple times with the check box cleared, these operations share one proxy and the service status is persisted across multiple operations.</span></span>

<span data-ttu-id="75e91-153">**[新しいプロキシを開始する]** チェック ボックスをオンにした場合は、 **[起動]** をクリックするたびに新しいプロキシが開始され、前のセッション シナリオが終了し、サービスの状態がリセットされます。</span><span class="sxs-lookup"><span data-stu-id="75e91-153">If the **Start a new proxy** check box is checked, a new proxy is started for each **Invoke**, the previous session scenario is ended, and the service status is reset.</span></span>

### <a name="editing-client-configuration"></a><span data-ttu-id="75e91-154">クライアント構成の編集</span><span class="sxs-lookup"><span data-stu-id="75e91-154">Editing Client Configuration</span></span>

<span data-ttu-id="75e91-155">WCF テスト クライアントのメイン ウィンドウの左ペインには、クライアントの構成ファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-155">The left pane of the WCF Test Client main window lists client configuration files.</span></span> <span data-ttu-id="75e91-156">いずれかの項目をダブルクリックすると、右ペインにファイルの内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-156">Double-click any of the items to display the contents of the file in the right pane.</span></span>

#### <a name="edit-with-service-configuration-editor"></a><span data-ttu-id="75e91-157">サービス構成エディターを使用した編集</span><span class="sxs-lookup"><span data-stu-id="75e91-157">Edit with Service Configuration Editor</span></span>

<span data-ttu-id="75e91-158">左ペインで **[構成ファイル]** を右クリックし、コンテキスト メニューの **[SvcConfigEditor での編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75e91-158">Right-click **Config File** in the left pane and select the context menu **Edit with SvcConfigEditor**.</span></span> <span data-ttu-id="75e91-159">サービス構成エディターが起動し、クライアント構成の内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-159">Service Configuration Editor is launched with the client configuration content.</span></span> <span data-ttu-id="75e91-160">このツール内で構成を編集して保存できます。</span><span class="sxs-lookup"><span data-stu-id="75e91-160">You can edit the configuration and save it within the tool.</span></span>

<span data-ttu-id="75e91-161">サービス構成エディターでファイルを保存すると、WCF テスト クライアントにより、ファイルが外部で変更されたことを通知する警告メッセージが表示され、ファイルをもう一度読み込むかどうかをたずねられます。</span><span class="sxs-lookup"><span data-stu-id="75e91-161">After saving the file in Service Configuration Editor, WCF Test Client displays a warning message to inform you that the file has been modified outside and asks whether you would like to reload it.</span></span>

<span data-ttu-id="75e91-162">**[はい]** を選択すると、[Client.dll.config] タブの構成の内容に、エディターで行った変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-162">If you select **Yes**, the configuration content in the "Client.dll.config" tab reflects the changes you made in the editor.</span></span>

<span data-ttu-id="75e91-163">**[いいえ]** を選択すると、[Client.dll.config] タブの構成の内容は変更されず、変更内容はソース ファイルに自動的に保存されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-163">If you select **No**, the configuration content in the "Client.dll.config" tab remains unchanged and the modified content is automatically saved to the source file.</span></span>

#### <a name="restore-to-default-configuration"></a><span data-ttu-id="75e91-164">既定の構成への復元</span><span class="sxs-lookup"><span data-stu-id="75e91-164">Restore to Default Configuration</span></span>

<span data-ttu-id="75e91-165">すべての変更をキャンセルし、既定のクライアント構成に戻すには、左ペインで **[構成ファイル]** を右クリックし、コンテキスト メニューの **[既定の構成に復元]** をクリックします。既定の構成値が読み込まれ、[Client.dll.config] タブの内容が復元されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-165">If you want to cancel all the changes and restore to the default client configuration, right-click **Config File** in the left pane and select the context menu **Restore to Default Config**. The default configuration value is loaded and content in "Client.dll.config" tab is restored.</span></span>

#### <a name="validate-changes"></a><span data-ttu-id="75e91-166">変更の検証</span><span class="sxs-lookup"><span data-stu-id="75e91-166">Validate Changes</span></span>

<span data-ttu-id="75e91-167">保存した変更が WCF テスト クライアントに読み込まれると、WCF スキーマに対して構成の有効性のチェックが行われます。</span><span class="sxs-lookup"><span data-stu-id="75e91-167">When saved changes are being loaded in WCF Test Client, the configuration is checked for validity against WCF schema.</span></span> <span data-ttu-id="75e91-168">エラーが見つかった場合は、エラーの詳細を示すダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-168">If errors are found, a dialog box is displayed to show error details.</span></span>

<span data-ttu-id="75e91-169">プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し中は、編集をサポートするメニュー項目 ([...の編集]、[...の復元] など) が無効になります。</span><span class="sxs-lookup"><span data-stu-id="75e91-169">During proxy generation, binary compiling, or service invoking, menu items that support editing (that is, "Edit …", "Restore …", and so on) are disabled.</span></span> <span data-ttu-id="75e91-170">更新された構成が WCF テスト クライアントに読み込まれるときは、サービスの呼び出しも無効になります。</span><span class="sxs-lookup"><span data-stu-id="75e91-170">Service invocation is also disabled when loading updated configuration to WCF Test Client.</span></span>

#### <a name="persist-client-configuration"></a><span data-ttu-id="75e91-171">クライアント構成の保持</span><span class="sxs-lookup"><span data-stu-id="75e91-171">Persist Client Configuration</span></span>

<span data-ttu-id="75e91-172">**[ツール]** -> **[オプション]** -> **[クライアント構成]** タブには、 **[サービスの起動時に常に構成を再生成する]** チェック ボックスがあり、既定でオンになっています。</span><span class="sxs-lookup"><span data-stu-id="75e91-172">The **Tools**->**Options**->**Client Configuration** tab contains an **Always Regenerate Config When Launching Services** option, which is enabled by default.</span></span> <span data-ttu-id="75e91-173">このオプションでは、WCF テスト クライアントによってサービスが読み込まれるたびに、最新のサービス コントラクトとサービスの App.config ファイルに基づいて構成ファイルが再生成されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="75e91-173">This option specifies that every time WCF Test Client loads a service, it regenerates a configuration file based on the latest service contract and service App.config files.</span></span>

<span data-ttu-id="75e91-174">WCF サービスのクライアント構成を編集した場合、その更新されたファイルを常に使用してサービスをデバッグするには、 **[再生成]** オプションをオフにします。</span><span class="sxs-lookup"><span data-stu-id="75e91-174">If you have edited the client configuration for your WCF service and want to always use this updated file to debug your service, you can uncheck the **Regenerate** option.</span></span> <span data-ttu-id="75e91-175">このようにすると、サービスを更新して WCF テスト クライアントを再び開いた場合でも、Client.dll.config ファイルとして使用されるのは、更新されたサービスに基づいて再生成されたものではなく、以前に更新したものになります。</span><span class="sxs-lookup"><span data-stu-id="75e91-175">By doing so, even when you update the service and reopen WCF Test Client, the Client.dll.config file is the one you updated previously instead of a regenerated one based on the updated service.</span></span>

<span data-ttu-id="75e91-176">ただし、再生成されたプロキシとの一貫性を保つために、構成ファイルの編集が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="75e91-176">However, you might need to edit the configuration file to make it consistent with the regenerated proxy.</span></span> <span data-ttu-id="75e91-177">サービスを更新したことが原因で、再生成されたプロキシと構成ファイルが一致しなくなると、サービスを呼び出したときにエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="75e91-177">If the regenerated proxy and configuration file are mismatched due to an updated service, errors will occur when the service is invoked.</span></span>

> [!CAUTION]
> <span data-ttu-id="75e91-178">変更したクライアント構成ファイルを後で再利用することにした場合、該当するファイルは次の場所で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="75e91-178">If you have modified the client configuration file and select to reuse it in the future, you can find the file in the following location:</span></span>
>
> <span data-ttu-id="75e91-179">\Documents and Settings\\[ユーザー アカウント]\My Documents\Test Client Projects。</span><span class="sxs-lookup"><span data-stu-id="75e91-179">\Documents and Settings\\[User Account]\My Documents\Test Client Projects.</span></span>
>
> <span data-ttu-id="75e91-180">クライアント構成ファイルに格納されている更新された資格情報は、このフォルダーのアクセス制御リスト (ACL) によって保護されています。</span><span class="sxs-lookup"><span data-stu-id="75e91-180">Any updated credential information stored to the client configuration file is protected by the Access Control List (ACL) of this folder.</span></span>

### <a name="adding-removing-and-refreshing-services"></a><span data-ttu-id="75e91-181">サービスの追加、削除、および更新</span><span class="sxs-lookup"><span data-stu-id="75e91-181">Adding, Removing and Refreshing Services</span></span>

#### <a name="add-service"></a><span data-ttu-id="75e91-182">Add Service (サービスの追加)</span><span class="sxs-lookup"><span data-stu-id="75e91-182">Add Service</span></span>

<span data-ttu-id="75e91-183">WCF テスト クライアントにサービスを追加するには、 **[ファイル]** -> **[サービスの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75e91-183">Click **File**->**Add Service** to add a service to WCF Test Client.</span></span> <span data-ttu-id="75e91-184">次に、追加するサービスの URI (エンドポイント アドレス) を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75e91-184">You are then required to type the URI (endpoint address) of the service to be added.</span></span> <span data-ttu-id="75e91-185">サービスのアドレスには、MEX アドレスまたは WSDL アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="75e91-185">The service’s address can be a mex address or WSDL address.</span></span>

<span data-ttu-id="75e91-186">**[最近のサービス]** サブメニューには、最近追加されたサービスのエンドポイントが 10 個まで一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-186">You can also find a list of 10 recently added services' endpoints in the **Recent Services** submenu.</span></span> <span data-ttu-id="75e91-187">いずれかをクリックすると、指定したサービスが WCF テスト クライアントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-187">If you select one of them, the specified service is added to WCF Test Client.</span></span>

<span data-ttu-id="75e91-188">サービスのツリーで、ルートの **[マイ サービス プロジェクト]** を右クリックし、 **[サービスの追加]** をクリックする方法でも、同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="75e91-188">You can also right-click the root of service tree **My Service Projects**, and select **Add Service** to achieve the same result.</span></span>

<span data-ttu-id="75e91-189">プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し中は、サービスの追加をサポートするメニュー項目が無効になります。</span><span class="sxs-lookup"><span data-stu-id="75e91-189">During proxy generation, binary compiling, or service invocation, menu items that support adding a service are disabled.</span></span> <span data-ttu-id="75e91-190">また、サービスの呼び出しも無効になります。</span><span class="sxs-lookup"><span data-stu-id="75e91-190">Service invocation is also disabled.</span></span>

#### <a name="remove-service"></a><span data-ttu-id="75e91-191">サービスの削除</span><span class="sxs-lookup"><span data-stu-id="75e91-191">Remove Service</span></span>

<span data-ttu-id="75e91-192">WCF テスト クライアントからサービスを削除するには、削除するサービスのサービス ルートを右クリックし、 **[サービスの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75e91-192">Right-click the service root of the service to be removed, and select **Remove Service** to remove a service from WCF Test Client.</span></span>

<span data-ttu-id="75e91-193">プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し中は、サービスの削除をサポートするメニュー項目が無効になります。</span><span class="sxs-lookup"><span data-stu-id="75e91-193">During proxy generation, binary compiling, or service invocation, menu items that support removing a service are disabled.</span></span> <span data-ttu-id="75e91-194">また、サービスの呼び出しも無効になります。</span><span class="sxs-lookup"><span data-stu-id="75e91-194">Service invocation is also disabled.</span></span>

#### <a name="refresh-service"></a><span data-ttu-id="75e91-195">サービスの更新</span><span class="sxs-lookup"><span data-stu-id="75e91-195">Refresh Service</span></span>

<span data-ttu-id="75e91-196">WCF テスト クライアントの実行中にサービスに変更を加えた場合、そのサービスに対する WCF テスト クライアントの実装を最新の状態に保つには、サービスのサービス ルートを右クリックし、 **[サービスを最新の情報に更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75e91-196">If a change is made to the service while WCF Test Client is running and you want to ensure that the WCF Test Client implementation for that service is up-to-date, right-click the service root of the service, and select **Refresh Service**.</span></span> <span data-ttu-id="75e91-197">更新後、サービスの状態はリセットされます。</span><span class="sxs-lookup"><span data-stu-id="75e91-197">Note that after refreshing, the service status is reset.</span></span>

<span data-ttu-id="75e91-198">プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し中は、サービスの更新をサポートするメニュー項目が無効になります。</span><span class="sxs-lookup"><span data-stu-id="75e91-198">During proxy generation, binary compiling, or service invocation, menu items that support refreshing a service are disabled.</span></span> <span data-ttu-id="75e91-199">また、サービスの呼び出しも無効になります。</span><span class="sxs-lookup"><span data-stu-id="75e91-199">Service invocation is also disabled.</span></span>

## <a name="location-of-files-generated-by-the-test-client"></a><span data-ttu-id="75e91-200">テスト クライアントが生成するファイルの場所</span><span class="sxs-lookup"><span data-stu-id="75e91-200">Location of Files Generated by the Test Client</span></span>

<span data-ttu-id="75e91-201">既定では、WCF テスト クライアントによって、生成されたクライアント コードと構成ファイルが "%appdata%\Local\temp\Test Client Projects" フォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-201">By default, WCF Test Client stores generated client code and configuration files in the "%appdata%\Local\temp\Test Client Projects" folder.</span></span> <span data-ttu-id="75e91-202">このフォルダーは、WCF テスト クライアントの終了後に削除されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-202">This folder is deleted after WCF Test Client exits.</span></span> <span data-ttu-id="75e91-203">構成ファイルが WCF テスト クライアントで変更された場合、 **[サービスの起動時に常に構成を再生成する]** オプションが無効になっていると、変更されたファイルは、マッピング (メタデータ アドレスとファイル名のマッピング) XML ファイルをインデックスとして、"My Documents\Test Client Projects" の "CachedConfig" フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="75e91-203">If a configuration file is modified in WCF Test Client and the **Always Regenerate Config When Launching Services** option is disabled, the modified file is copied to the "CachedConfig" folder under "My Documents\Test Client Projects" with a mapping (metadata-address-to-file-name) XML file as an index.</span></span>

<span data-ttu-id="75e91-204">コマンド ラインから WCF テスト クライアントを起動し、`/ProjectPath` スイッチを使用して、生成されたファイルを格納する新しいパスを指定することもできます。また、`/RestoreProjectPath` スイッチを使用して、既定の場所を復元することもできます。</span><span class="sxs-lookup"><span data-stu-id="75e91-204">You can also start WCF Test Client in a command line, use the `/ProjectPath` switch to specify a new desired path for storing generated files, or use the `/RestoreProjectPath` switch to restore the default location.</span></span> <span data-ttu-id="75e91-205">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="75e91-205">The syntax is as follows:</span></span>

`wcfTestClient.exe /ProjectPath [desired location]`

<span data-ttu-id="75e91-206">このコマンドを実行しても、WCF テスト クライアントは開きません。</span><span class="sxs-lookup"><span data-stu-id="75e91-206">Running this command does not open WCF Test Client.</span></span> <span data-ttu-id="75e91-207">フォルダーの場所が変更されるだけです。</span><span class="sxs-lookup"><span data-stu-id="75e91-207">Only the folder location is changed.</span></span> <span data-ttu-id="75e91-208">このコマンドは、WCF テスト クライアントが実行されているかどうかにかかわらず実行できます。</span><span class="sxs-lookup"><span data-stu-id="75e91-208">You can run this command whether WCF Test Client is running or not.</span></span> <span data-ttu-id="75e91-209">新しい場所は、WCF テスト クライアントが再起動したときに適用されます。</span><span class="sxs-lookup"><span data-stu-id="75e91-209">The new location is applied when WCF Test Client is restarted.</span></span> <span data-ttu-id="75e91-210">場所に関する情報は、レジストリか、"%appdata%\Local\temp\Test Client Projects" フォルダーの WcfTestClient.exe.option ファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="75e91-210">The location information can be saved in registry, or in the WcfTestClient.exe.option file in the "%appdata%\Local\temp\Test Client Projects" folder.</span></span>

## <a name="features-supported-by-wcf-test-client"></a><span data-ttu-id="75e91-211">WCF のテスト用クライアントでサポートされる機能</span><span class="sxs-lookup"><span data-stu-id="75e91-211">Features supported by WCF Test Client</span></span>

<span data-ttu-id="75e91-212">WCF テスト クライアントがサポートする機能の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="75e91-212">The following is a list of features supported by WCF Test Client:</span></span>

- <span data-ttu-id="75e91-213">サービスの呼び出し : 要求/応答メッセージおよび一方向メッセージ</span><span class="sxs-lookup"><span data-stu-id="75e91-213">Service Invocation: Request/Response and One-way message.</span></span>

- <span data-ttu-id="75e91-214">バインディング : Svcutil.exe でサポートされるすべてのバインディング</span><span class="sxs-lookup"><span data-stu-id="75e91-214">Bindings: all bindings supported by Svcutil.exe.</span></span>

- <span data-ttu-id="75e91-215">セッションの制御</span><span class="sxs-lookup"><span data-stu-id="75e91-215">Controlling Session.</span></span>

- <span data-ttu-id="75e91-216">メッセージ コントラクト</span><span class="sxs-lookup"><span data-stu-id="75e91-216">Message Contract.</span></span>

- <span data-ttu-id="75e91-217">XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="75e91-217">XML serialization.</span></span>

<span data-ttu-id="75e91-218">WCF テスト クライアントでサポートされない機能を次に示します。</span><span class="sxs-lookup"><span data-stu-id="75e91-218">The following is a list of features not supported by WCF Test Client:</span></span>

- <span data-ttu-id="75e91-219">型: <xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message>、<xref:System.Xml.XmlElement>、<xref:System.Xml.XmlAttribute>、<xref:System.Xml.XmlNode>、<xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装する型 (関連する <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 属性を含む)、<xref:System.Xml.Linq.XDocument> 型と <xref:System.Xml.Linq.XElement> 型、および ADO.NET <xref:System.Data.DataTable> 型。</span><span class="sxs-lookup"><span data-stu-id="75e91-219">Types: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, types that implement the <xref:System.Xml.Serialization.IXmlSerializable> interface, including the related <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> attribute, and the <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> types and the ADO.NET <xref:System.Data.DataTable> type.</span></span>

- <span data-ttu-id="75e91-220">双方向コントラクト</span><span class="sxs-lookup"><span data-stu-id="75e91-220">Duplex contract.</span></span>

- <span data-ttu-id="75e91-221">トランザクション</span><span class="sxs-lookup"><span data-stu-id="75e91-221">Transaction.</span></span>

- <span data-ttu-id="75e91-222">セキュリティ: CardSpace、証明書、およびユーザー名/パスワード。</span><span class="sxs-lookup"><span data-stu-id="75e91-222">Security: CardSpace , Certificate, and Username/Password.</span></span>

- <span data-ttu-id="75e91-223">バインディング : WSFederationBinding、任意のコンテキスト バインディングおよび HTTPS バインディング、WebHttpBinding (JSON 応答メッセージ サポート)</span><span class="sxs-lookup"><span data-stu-id="75e91-223">Bindings: WSFederationbinding, any Context bindings and Https binding, WebHttpbinding (Json response message support).</span></span>

## <a name="closing-wcf-test-client"></a><span data-ttu-id="75e91-224">WCF のテスト用クライアントの終了</span><span class="sxs-lookup"><span data-stu-id="75e91-224">Closing WCF Test Client</span></span>

<span data-ttu-id="75e91-225">WCF テスト クライアントは、次の方法で閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="75e91-225">You can close WCF Test Client in the following ways:</span></span>

- <span data-ttu-id="75e91-226">**[ファイル]** メニューの **[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75e91-226">On the **File** menu, click **Exit**.</span></span> <span data-ttu-id="75e91-227">または、WCF テスト クライアントのメイン ウィンドウで、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75e91-227">Alternatively, in the WCF Test Client main window, click **Close**.</span></span> <span data-ttu-id="75e91-228">WCF テスト クライアントが Visual Studio によって起動された場合は、どちらの手順でも WCF サービスの自動ホストがシャットダウンし、Visual Studio のデバッグ処理が停止します。</span><span class="sxs-lookup"><span data-stu-id="75e91-228">Both of these actions also shut down WCF Service Auto Host and stop the Visual Studio debugging process if WCF Test Client was launched by Visual Studio.</span></span>

- <span data-ttu-id="75e91-229">通知領域の **[WCF サービス ホスト]** アイコンを右クリックし、 **[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75e91-229">Right-click the **WCF Service Host** icon in the notification area, and then click **Exit.**</span></span> <span data-ttu-id="75e91-230">これにより、WCF サービスの自動ホストと WCF テスト クライアントの両方がシャットダウンし、Visual Studio のデバッグ処理が停止します。</span><span class="sxs-lookup"><span data-stu-id="75e91-230">This shuts down both WCF Service Auto Host and WCF Test Client and stops the Visual Studio debugging process.</span></span>

## <a name="see-also"></a><span data-ttu-id="75e91-231">関連項目</span><span class="sxs-lookup"><span data-stu-id="75e91-231">See also</span></span>

- [<span data-ttu-id="75e91-232">WCF サービス ホスト (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="75e91-232">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
