---
description: '詳細情報: フェデレーションのサンプル'
title: フェデレーション サンプル
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: a85a290988b6cbb4b30a1098f3558ec34ead1d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704083"
---
# <a name="federation-sample"></a><span data-ttu-id="e36ad-103">フェデレーション サンプル</span><span class="sxs-lookup"><span data-stu-id="e36ad-103">Federation Sample</span></span>

<span data-ttu-id="e36ad-104">このサンプルではフェデレーション セキュリティを示します。</span><span class="sxs-lookup"><span data-stu-id="e36ad-104">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="e36ad-105">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="e36ad-105">Sample Details</span></span>  

 <span data-ttu-id="e36ad-106">Windows Communication Foundation (WCF) では、を介したフェデレーションセキュリティアーキテクチャの展開がサポートされて `wsFederationHttpBinding` います。</span><span class="sxs-lookup"><span data-stu-id="e36ad-106">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="e36ad-107">`wsFederationHttpBinding` は、セキュリティで保護された、信頼できる、相互運用が可能なバインディングを提供します。このバインディングでは、要求/応答の通信のための基になるトランスポート機構として HTTP を使用でき、エンコーディングのためのワイヤ形式として Text/XML を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-107">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="e36ad-108">WCF でのフェデレーションの詳細については、「 [フェデレーション](../feature-details/federation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e36ad-108">For more information about Federation in WCF, see [Federation](../feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="e36ad-109">シナリオは、次の 4 つの部分から構成されます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-109">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="e36ad-110">BookStore サービス</span><span class="sxs-lookup"><span data-stu-id="e36ad-110">BookStore service</span></span>  
  
- <span data-ttu-id="e36ad-111">BookStore STS</span><span class="sxs-lookup"><span data-stu-id="e36ad-111">BookStore STS</span></span>  
  
- <span data-ttu-id="e36ad-112">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="e36ad-112">HomeRealm STS</span></span>  
  
- <span data-ttu-id="e36ad-113">BookStore クライアント</span><span class="sxs-lookup"><span data-stu-id="e36ad-113">BookStore Client</span></span>  
  
 <span data-ttu-id="e36ad-114">BookStore サービスは、`BrowseBooks` と `BuyBook` の 2 つの操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="e36ad-114">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="e36ad-115">サービスでは、`BrowseBooks` 操作には匿名アクセスできますが、`BuyBooks` 操作にアクセスするには認証済みのアクセス権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e36ad-115">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="e36ad-116">認証は、BookStore STS によって発行されたトークンの形式を取ります。</span><span class="sxs-lookup"><span data-stu-id="e36ad-116">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="e36ad-117">BookStore サービス用の構成ファイルは、次のように `wsFederationHttpBinding` を使用して、クライアントを BookStore STS にポイントします。</span><span class="sxs-lookup"><span data-stu-id="e36ad-117">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="e36ad-118">次に BookStore STS は、HomeRealm STS によって発行されたトークンを使用した、クライアントの認証を要求します。</span><span class="sxs-lookup"><span data-stu-id="e36ad-118">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="e36ad-119">ここでも、BookStore STS 用の構成ファイルは、`wsFederationHttpBinding` を使用して、クライアントを HomeRealm STS にポイントします。</span><span class="sxs-lookup"><span data-stu-id="e36ad-119">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="e36ad-120">`BuyBook` 操作にアクセスするときに発生するイベントの順序は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e36ad-120">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="e36ad-121">クライアントは、Windows 資格情報を使用して HomeRealm STS に対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="e36ad-121">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="e36ad-122">HomeRealm STS は、BookStore STS に対する認証に使用できるトークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="e36ad-122">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="e36ad-123">クライアントは、HomeRealm STS によって発行されたトークンを使用して BookStore STS に対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="e36ad-123">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="e36ad-124">BookStore STS は、BookStore サービスに対する認証に使用できるトークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="e36ad-124">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="e36ad-125">クライアントは、BookStore STS によって発行されたトークンを使用して BookStore サービスに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="e36ad-125">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="e36ad-126">クライアントは `BuyBook` 操作にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="e36ad-126">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="e36ad-127">このサンプルの設定および実行方法については、次の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e36ad-127">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e36ad-128">このサンプルを実行するには、 **wwwroot** ディレクトリに対する書き込みアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="e36ad-128">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e36ad-129">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="e36ad-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e36ad-130">SDK コマンド ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-130">Open the SDK command window.</span></span> <span data-ttu-id="e36ad-131">Setup.bat をサンプルのパスで実行します。</span><span class="sxs-lookup"><span data-stu-id="e36ad-131">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="e36ad-132">これにより、サンプルに必要な仮想ディレクトリが作成され、必要な証明書が適切な権限を付与されてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-132">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e36ad-133">Setup.bat バッチ ファイルは、Windows SDK コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="e36ad-133">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="e36ad-134">MSSDK 環境変数が SDK のインストール ディレクトリを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="e36ad-134">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="e36ad-135">この環境変数は、Windows SDK コマンド プロンプトで自動設定されます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-135">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="e36ad-136">Windows Vista では、セットアップで IIS 管理者スクリプトが使用されるため、IIS 6.0 管理互換がインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e36ad-136">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="e36ad-137">Windows Vista でセットアップスクリプトを実行するには、管理者特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="e36ad-137">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="e36ad-138">Visual Studio で FederationSample を開き、[**ビルド**] メニューの [**ソリューションのビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e36ad-138">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="e36ad-139">これによって共通のプロジェクト ファイル、Bookstore サービス、Bookstore STS、および HomeRealm STS が作成され、IIS に展開されます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-139">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="e36ad-140">さらに Bookstore クライアント アプリケーションがビルドされ、FederationSample\BookStoreClient\bin\Debug フォルダーに実行可能ファイル BookStoreClient.exe が配置されます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-140">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="e36ad-141">BookStoreClient.exe をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e36ad-141">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="e36ad-142">BookStoreClient ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-142">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="e36ad-143">書店で利用可能な書籍を参照するには、[ **参照**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e36ad-143">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="e36ad-144">特定の本を購入するには、一覧で本を選択し、[ **Book book**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e36ad-144">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="e36ad-145">アプリケーションが起動し、HomeRealm セキュリティ トークン サービスを使用した Windows 認証によって認証を行います。</span><span class="sxs-lookup"><span data-stu-id="e36ad-145">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="e36ad-146">サンプルは、ユーザーが 15 ドル以下の本を購入できるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="e36ad-146">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="e36ad-147">15 ドルを超える本を購入しようとすると、クライアントは、BookStore サービスからアクセス拒否のメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e36ad-147">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e36ad-148">サンプルでは、購入後にユーザーの与信限度額を更新しません。</span><span class="sxs-lookup"><span data-stu-id="e36ad-148">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="e36ad-149">ユーザーは、(固定の) 与信限度額以内なら何度でも本を購入できます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-149">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="e36ad-150">クリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="e36ad-150">To clean up</span></span>  
  
1. <span data-ttu-id="e36ad-151">Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="e36ad-151">Run Cleanup.bat.</span></span> <span data-ttu-id="e36ad-152">これによって、設定中に作成された仮想ディレクトリが削除されます。同時に、設定中にインストールされた証明書も削除されます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-152">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e36ad-153">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e36ad-153">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e36ad-154">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e36ad-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e36ad-155">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="e36ad-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e36ad-156">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e36ad-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
