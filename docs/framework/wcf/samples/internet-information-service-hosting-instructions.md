---
description: 詳細については、インターネットインフォメーションサービスのホスト手順に関するページを参照してください。
title: インターネット インフォメーション サービスのホスティング手順
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 51f5230ecbb8eaf4a909c5c09366680b8c555165
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726378"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="6521d-103">インターネット インフォメーション サービスのホスティング手順</span><span class="sxs-lookup"><span data-stu-id="6521d-103">Internet Information Service Hosting Instructions</span></span>

<span data-ttu-id="6521d-104">インターネット インフォメーション サービス (IIS) によってホストされているこのサンプルを実行するには、IIS が適切にインストールされて実行されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6521d-104">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="6521d-105">Windows Server 2008 R2 に IIS バージョン 7.5 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="6521d-105">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="6521d-106">**サーバーマネージャー** から、[ロール] を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="6521d-106">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="6521d-107">[ **役割の概要**] で、[ **役割の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-107">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="6521d-108">[ **次へ** ] をクリックして、[ **サーバーの役割の選択** ] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="6521d-108">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="6521d-109">[**役割**] ボックスの一覧から [**アプリケーションサーバー** ] を選択し、[**次へ**] を2回クリックして、アプリケーションサーバーの役割の **[役割サービスの選択**] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="6521d-109">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="6521d-110">[ **Web サーバー (IIS)** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6521d-110">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="6521d-111">追加の役割サービスと機能をインストールするように求めるメッセージが表示されたら、[ **必要な機能の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-111">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="6521d-112">[ **次へ** ] を2回クリックして、Web サーバー (IIS) の役割の **[役割サービスの選択** ] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="6521d-112">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="6521d-113">[ **管理ツール**]、[ **IIS 6 管理互換**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-113">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="6521d-114">[ **IIS 6 スクリプトツール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6521d-114">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="6521d-115">追加の役割サービスと機能をインストールするように求めるメッセージが表示されたら、[ **必要な役割サービスの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-115">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="6521d-116">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-116">Click **Next**.</span></span>  
  
6. <span data-ttu-id="6521d-117">選択の概要が正しい場合は、[ **インストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-117">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="6521d-118">インストールが完了したら、[ **閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-118">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="6521d-119">Windows 7 に IIS バージョン 7.5 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="6521d-119">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="6521d-120">**[スタート]** ボタン、**[コントロール パネル]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-120">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="6521d-121">**プログラム** グループを開きます。</span><span class="sxs-lookup"><span data-stu-id="6521d-121">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="6521d-122">[ **プログラムと機能**] の [ **Windows の機能の有効化または無効化**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-122">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="6521d-123">[ **ユーザーアカウント制御** ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6521d-123">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="6521d-124">**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-124">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="6521d-125">[ **Windows の機能** ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6521d-125">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="6521d-126">**インターネットインフォメーションサービス** というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-126">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="6521d-127">[ **World Wide Web Services**] というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-127">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="6521d-128">[ **アプリケーション開発機能**] というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-128">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="6521d-129">次の項目が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6521d-129">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="6521d-130">**.NET 拡張機能**</span><span class="sxs-lookup"><span data-stu-id="6521d-130">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="6521d-131">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="6521d-131">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="6521d-132">**ISAPI 拡張機能**</span><span class="sxs-lookup"><span data-stu-id="6521d-132">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="6521d-133">**ISAPI フィルター**</span><span class="sxs-lookup"><span data-stu-id="6521d-133">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="6521d-134">[ **World Wide Web Services**] というラベルの付いた項目の下で、[ **共通の Http 機能**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-134">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="6521d-135">**静的なコンテンツ** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6521d-135">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="6521d-136">[ **World Wide Web Services**] というラベルの付いた項目の下にある [ **セキュリティ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-136">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="6521d-137">**Windows 認証** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6521d-137">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="6521d-138">**インターネットインフォメーションサービス** ディレクトリで、[ **Web 管理ツール**] というラベルの付いた項目を展開し、[ **IIS 管理コンソール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6521d-138">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="6521d-139">[ **Iis 6 管理互換**] というラベルの付いた項目を展開し、[ **Iis 6 スクリプトツール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6521d-139">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="6521d-140">**インターネットインフォメーションサービス** ディレクトリで、 **Microsoft .NET Framework 3.5.1**] というラベルの付いた項目を展開し、[ **Http アクティブ化の Windows Communication Foundation**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6521d-140">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="6521d-141">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-141">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="6521d-142">Windows Server 2008 に IIS バージョン 7.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="6521d-142">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="6521d-143">**サーバーマネージャー** から、[**ロール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6521d-143">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="6521d-144">[ **役割の概要**] で、[ **役割の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-144">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="6521d-145">[ **次へ** ] をクリックして、[ **サーバーの役割の選択** ] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="6521d-145">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="6521d-146">[**役割**] ボックスの一覧から [**アプリケーションサーバー** ] を選択し、[**次へ**] を2回クリックして、アプリケーションサーバーの役割の **[役割サービスの選択**] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="6521d-146">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="6521d-147">[ **Web サーバー (IIS)** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6521d-147">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="6521d-148">追加の役割サービスと機能をインストールするように求めるメッセージが表示されたら、[ **必要な機能の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-148">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="6521d-149">[ **次へ** ] を2回クリックして、Web サーバー (IIS) の役割の **[役割サービスの選択** ] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="6521d-149">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="6521d-150">[ **管理ツール**]、[ **IIS 6 管理互換**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-150">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="6521d-151">[ **IIS 6 スクリプトツール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6521d-151">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="6521d-152">追加の役割サービスと機能をインストールするように求めるメッセージが表示されたら、[ **必要な役割サービスの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-152">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="6521d-153">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-153">Click **Next**.</span></span>  
  
6. <span data-ttu-id="6521d-154">選択の概要が正しい場合は、[ **インストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-154">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="6521d-155">インストールが完了したら、[ **閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-155">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="6521d-156">Windows Vista に IIS バージョン 7.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="6521d-156">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="6521d-157">[スタート] ボタンをクリックし、[コントロール パネル] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-157">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="6521d-158">[ **プログラム** ] グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="6521d-158">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="6521d-159">[ **プログラムと機能**] の [ **Windows の機能の有効化または無効化**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-159">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="6521d-160">[ **ユーザーアカウント制御** ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6521d-160">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="6521d-161">**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-161">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="6521d-162">[ **Windows の機能** ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6521d-162">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="6521d-163">**インターネットインフォメーションサービス** というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-163">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="6521d-164">[ **World Wide Web Services**] というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-164">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="6521d-165">[ **アプリケーション開発機能**] というラベルの付いた項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-165">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="6521d-166">次の項目が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6521d-166">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="6521d-167">**.NET 拡張機能**</span><span class="sxs-lookup"><span data-stu-id="6521d-167">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="6521d-168">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="6521d-168">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="6521d-169">**ISAPI 拡張機能**</span><span class="sxs-lookup"><span data-stu-id="6521d-169">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="6521d-170">**ISAPI フィルター**</span><span class="sxs-lookup"><span data-stu-id="6521d-170">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="6521d-171">[ **Web 管理ツール**] というラベルの付いた項目を展開し、[ **IIS 管理コンソール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6521d-171">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="6521d-172">[ **World Wide Web Services**] というラベルの付いた項目の下で、[ **共通の Http 機能**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-172">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="6521d-173">**静的なコンテンツ** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6521d-173">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="6521d-174">[ **World Wide Web Services**] というラベルの付いた項目の下にある [ **セキュリティ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="6521d-174">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="6521d-175">**Windows 認証** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6521d-175">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="6521d-176">[ **Iis 6 管理互換**] というラベルの付いた項目を展開し、[ **Iis 6 スクリプトツール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6521d-176">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="6521d-177">**Microsoft .NET Framework 3.0**] というラベルの付いた項目を展開し、[ **Windows Communication Foundation Http Activation**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6521d-177">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="6521d-178">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-178">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="6521d-179">Windows Server 2003 に IIS バージョン 6.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="6521d-179">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="6521d-180">[ **サーバーの管理**] で、[ **ロールの追加または削除**] をクリックし、[ **次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-180">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="6521d-181">[**サーバーの役割**] ボックスの一覧から [**アプリケーションサーバー (IIS、ASP.NET)** ] を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-181">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="6521d-182">[ **ASP.NET を有効にする** ] チェックボックスをオンにし、[ **次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-182">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="6521d-183">選択内容が正しい場合は、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-183">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="6521d-184">Service Pack 2 および Service Pack 3 がインストールされている Windows XP に IIS バージョン 5.1 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="6521d-184">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="6521d-185">コントロール パネルで、**[プログラムの追加と削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-185">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="6521d-186">**[プログラムの追加と削除]** ダイアログ ボックスで、**[Windows コンポーネントの追加と削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-186">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="6521d-187">**Windows コンポーネントウィザード** で、[**インターネットインフォメーションサービス (IIS)** ] チェックボックスをオンにして、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-187">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="6521d-188">[ **ファイルが必要** ] ダイアログボックスが表示されたら、オペレーティングシステムのインストールディスクを挿入し、i386 フォルダーを参照して、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-188">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="6521d-189">インストールが完了したら、[ **完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6521d-189">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="6521d-190">[ **プログラムの追加と削除** ] ダイアログボックスを閉じて、[ **コントロールパネル**] を閉じます。</span><span class="sxs-lookup"><span data-stu-id="6521d-190">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="6521d-191">IIS と ASP.NET がインストールされていることを確認するには</span><span class="sxs-lookup"><span data-stu-id="6521d-191">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="6521d-192">このトピックの最後に示す HTML ファイルを \InetPub\wwwroot のルート ディレクトリに保存し、Default.aspx という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="6521d-192">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="6521d-193">ブラウザー ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="6521d-193">Open a browser window.</span></span>  
  
3. <span data-ttu-id="6521d-194">[ `http://localhost/Default.aspx` アドレス] ボックスに「」と入力し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6521d-194">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="6521d-195">Web ページに、テキスト "Hello World" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6521d-195">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6521d-196">新しいバージョンの .NET Framework をインストールするたびに、aspnet_isapi を IIS の Web サービス拡張機能として再登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6521d-196">Each time you install a new version of the .NET Framework, you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="6521d-197">これを行うには、`aspnet_regiis –I –enable` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6521d-197">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="6521d-198">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="6521d-198">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
