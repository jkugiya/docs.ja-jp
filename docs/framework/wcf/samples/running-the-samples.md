---
description: 詳細については、Windows Communication Foundation サンプルの実行に関するページを参照してください。
title: Windows Communication Foundation サンプルの実行
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: 4edbd7aef8eed42e4815666c15ff07aa2c2e82de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703732"
---
# <a name="running-the-windows-communication-foundation-samples"></a><span data-ttu-id="08252-103">Windows Communication Foundation サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="08252-103">Running the Windows Communication Foundation Samples</span></span>

<span data-ttu-id="08252-104">Windows Communication Foundation (WCF) サンプルは、単一コンピューター構成または複数コンピューター構成で実行できます。</span><span class="sxs-lookup"><span data-stu-id="08252-104">The Windows Communication Foundation (WCF) samples can be run in a single-machine or cross-machine configuration.</span></span> <span data-ttu-id="08252-105">サンプルは、単一コンピューターでそのまま実行できます。</span><span class="sxs-lookup"><span data-stu-id="08252-105">As supplied, the samples are ready for running on a single machine.</span></span> <span data-ttu-id="08252-106">複数コンピューター構成で実行するには、サンプルの構成ファイルの設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08252-106">In a cross-machine configuration, it is necessary to modify a sample's configuration file settings.</span></span> <span data-ttu-id="08252-107">単一コンピューターおよび複数コンピューターの構成でサンプルを実行する手順を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="08252-107">The following procedures explain how to run a sample in same-machine and cross-machine configurations.</span></span> <span data-ttu-id="08252-108">インターネット インフォメーション サービス (IIS) でホストされるサービスと自己ホスト型のサービスのサンプルとでは、手順が異なります。</span><span class="sxs-lookup"><span data-stu-id="08252-108">Note that there are variations in the steps for services hosted in Internet Information Services (IIS) and the self-hosted samples.</span></span> <span data-ttu-id="08252-109">ほとんどのサンプルは IIS でホストされます。サンプルのホスト方法を判断するには、サンプルの Readme 情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08252-109">Most samples are hosted in IIS; see the sample readme information to determine how it is hosted.</span></span>  
  
 <span data-ttu-id="08252-110">Windows Vista では、IIS でホストされていないサンプルでは、リスナーを Http.sys に登録するには、管理者特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="08252-110">On Windows Vista, samples that are not hosted in IIS require elevated privileges to register a listener with Http.sys.</span></span> <span data-ttu-id="08252-111">Httpcfg.exe を使用して、サービスのリッスン アドレスをサービスが実行されているアカウントに登録するか、管理者権限で実行されているコマンド プロンプトでサービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="08252-111">Use Httpcfg.exe to register the service's listening addresses with the account the service is running under, or launch the service from a command prompt running with administrator privileges.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08252-112">WCF サンプルをビルドまたは実行する前に、 [Windows Communication Foundation のサンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="08252-112">Before building or running any of the WCF samples, be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="08252-113">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="08252-113">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="08252-114">サービスが IIS によってホストされている場合は、次のアドレスを入力して、ブラウザーを使用してサービスにアクセスできることを確認します `http://localhost/servicemodelsamples/service.svc` 。</span><span class="sxs-lookup"><span data-stu-id="08252-114">If the service is hosted by IIS, ensure that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="08252-115">これに応答して、確認ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08252-115">A confirmation page should be displayed in response.</span></span> <span data-ttu-id="08252-116">[確認] ページが表示されない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08252-116">If the confirmation page is not displayed, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
2. <span data-ttu-id="08252-117">サービスが自己ホスト型の場合は、言語固有のフォルダーの下の \service\bin にある Service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="08252-117">If the service is self-hosted, run Service.exe from \service\bin, from under the language-specific folder.</span></span> <span data-ttu-id="08252-118">サービス アクティビティがサービス コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="08252-118">Service activity is displayed on the service console window.</span></span>  
  
3. <span data-ttu-id="08252-119">\\言語固有のフォルダーの下から、\ client\bin から Client.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="08252-119">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="08252-120">クライアント アクティビティがクライアント コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="08252-120">Client activity is displayed on the client console window.</span></span>  
  
4. <span data-ttu-id="08252-121">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08252-121">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="08252-122">サンプルを複数コンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="08252-122">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="08252-123">サービスが IIS でホストされている場合 :</span><span class="sxs-lookup"><span data-stu-id="08252-123">If the service is hosted in IIS:</span></span>  
  
    1. <span data-ttu-id="08252-124">サービス コンピューターで、ServiceModelSamples という仮想ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="08252-124">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="08252-125">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)に含まれているバッチファイル Setupvroot.bat、ディスクディレクトリと仮想ディレクトリを作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="08252-125">The batch file Setupvroot.bat included with [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="08252-126">サービス プログラム ファイルを %SystemDrive%\Inetpub\wwwroot\servicemodelsamples からサービス コンピューターの ServiceModelSamples 仮想ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="08252-126">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="08252-127">このファイルが \bin ディレクトリにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="08252-127">Ensure that you include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="08252-128">ブラウザーを使用して、サービスにクライアント コンピューターからアクセスできるかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="08252-128">Test that you can access the service from the client machine using a browser.</span></span>  
  
     <span data-ttu-id="08252-129">サービスが自己ホスト型の場合、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="08252-129">If the service is self-hosted:</span></span>  
  
    1. <span data-ttu-id="08252-130">サービス コンピューターで、サービス ファイルを保持するディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="08252-130">On the service machine, create a directory to hold the service files.</span></span>  
  
    2. <span data-ttu-id="08252-131">サービス プログラム ファイルを、言語固有のフォルダーにある \service\bin\ フォルダーからサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="08252-131">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service machine.</span></span>  
  
    3. <span data-ttu-id="08252-132">サービスの構成ファイルで、エンドポイント定義のアドレス値をサービスの新しいアドレスに変更します。</span><span class="sxs-lookup"><span data-stu-id="08252-132">In the service configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="08252-133">アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="08252-133">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    4. <span data-ttu-id="08252-134">コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="08252-134">Launch Service.exe from a command prompt.</span></span>  
  
2. <span data-ttu-id="08252-135">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="08252-135">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
3. <span data-ttu-id="08252-136">エンドポイント アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="08252-136">Set the endpoint address.</span></span>  
  
    1. <span data-ttu-id="08252-137">サービスの実行に使用されているのがドメイン アカウントではない場合、クライアント構成ファイルを開き、エンドポイント定義のアドレス値をサービスの新しいアドレスに変更します。</span><span class="sxs-lookup"><span data-stu-id="08252-137">If the service is not running under a domain account, open the client configuration file and change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="08252-138">アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="08252-138">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    2. <span data-ttu-id="08252-139">サービスの実行に使用されているのがドメイン アカウントの場合、サービスに対して Svcutil.exe を実行し、クライアントの構成を再生成します。</span><span class="sxs-lookup"><span data-stu-id="08252-139">If the service is running under a domain account, regenerate the client configuration by running Svcutil.exe against the service.</span></span> <span data-ttu-id="08252-140">Svcutil.exe の実行の詳細については、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08252-140">For more information about running Svcutil.exe, see [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="08252-141">サンプルの構成ファイルではなく、生成されたファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="08252-141">Use the generated file instead of the configuration file in the sample.</span></span> <span data-ttu-id="08252-142">生成された構成ファイルには、追加の ID 情報があります (また、サービス エンドポイントへの接続に必要なすべての設定が、既定の設定であるにもかかわらず含まれています)。</span><span class="sxs-lookup"><span data-stu-id="08252-142">The generated configuration file has additional identity information, and contains all settings necessary to connect to the service endpoint even though they are the default settings.</span></span> <span data-ttu-id="08252-143">Id 情報の詳細については、「 [サービス id と認証](../feature-details/service-identity-and-authentication.md)」および「」を参照してください [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 。</span><span class="sxs-lookup"><span data-stu-id="08252-143">For more information about identity information, see [Service Identity and Authentication](../feature-details/service-identity-and-authentication.md), and [\<identity>](../../configure-apps/file-schema/wcf/identity.md).</span></span>  
  
4. <span data-ttu-id="08252-144">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="08252-144">On the client machine, launch Client.exe from a command prompt.</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="08252-145">サービスをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="08252-145">To debug a service</span></span>  
  
1. <span data-ttu-id="08252-146">[ **ビルド** ] メニューまたは CTRL + SHIFT + B キーを使用して、ソリューション (クライアントとサービスの両方) をビルドします。</span><span class="sxs-lookup"><span data-stu-id="08252-146">Build the solution (both client and service) using the **Build** menu or CTRL+SHIFT+B.</span></span>  
  
2. <span data-ttu-id="08252-147">サービスが IIS でホストされている場合 :</span><span class="sxs-lookup"><span data-stu-id="08252-147">If the service is hosted in IIS:</span></span>  
  
    1. <span data-ttu-id="08252-148">アドレスを入力して、ブラウザーを使用してサービスをアクティブにし `http://localhost/servicemodelsamples/service.svc` ます。</span><span class="sxs-lookup"><span data-stu-id="08252-148">Activate the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
    2. <span data-ttu-id="08252-149">ソリューションで、[ **デバッグ** ] メニューの [ **プロセスにアタッチ** ] メニュー項目をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08252-149">In the solution, choose the **Debug** menu and the **Attach to Process** menu item.</span></span>  
  
    3. <span data-ttu-id="08252-150">**[全ユーザーのプロセスを表示する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="08252-150">Select the **Show processes from all users** check box.</span></span>  
  
    4. <span data-ttu-id="08252-151">デバッグ対象のホスト ワーカー プロセス W3wp.exe を選択します (Windows XP では ASPNet_wp.exe を選択します)。</span><span class="sxs-lookup"><span data-stu-id="08252-151">Select the host worker process W3wp.exe to debug (select ASPNet_wp.exe on Windows XP).</span></span>  
  
3. <span data-ttu-id="08252-152">これで、サービス内にブレークポイントを設定し、例外に対してブレークポイントを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="08252-152">You can now set breakpoints in the service code and enable breakpoints on exceptions.</span></span>  
  
4. <span data-ttu-id="08252-153">クライアントプロジェクト項目を右クリックし、[ **デバッグ**]、[ **新しいインスタンスを開始**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="08252-153">Right-click the client project item and choose **Debug**, **Start new instance**.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="08252-154">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="08252-154">To clean up after the sample</span></span>  
  
- <span data-ttu-id="08252-155">サービスがセキュリティの目的で IIS でホストされている場合、サンプルの使用が終わったら、このセットアップで付与された仮想ディレクトリの定義とアクセス許可を削除してください。</span><span class="sxs-lookup"><span data-stu-id="08252-155">If the service is hosted in IIS for security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08252-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="08252-156">See also</span></span>

- [<span data-ttu-id="08252-157">Windows Communication Foundation サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="08252-157">Building the Windows Communication Foundation Samples</span></span>](building-the-samples.md)
- <span data-ttu-id="08252-158">[WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="08252-158">[Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))</span></span>
