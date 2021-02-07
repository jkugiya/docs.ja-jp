---
description: '詳細情報: LINQ メッセージクエリの相関関係'
title: LINQ メッセージ クエリの関連付け
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 7b979e3bdc2c0ede8f4f9d4595957f90581a0ecc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755279"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="52332-103">LINQ メッセージ クエリの関連付け</span><span class="sxs-lookup"><span data-stu-id="52332-103">LINQ Message Query Correlation</span></span>

<span data-ttu-id="52332-104">このサンプルでは、システム標準の <xref:System.ServiceModel.Dispatcher.MessageQuery> ではなく、カスタムの <xref:System.ServiceModel.XPathMessageQuery> 実装を使用して、コンテンツ ベースの関連付けを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="52332-104">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="52332-105">対象</span><span class="sxs-lookup"><span data-stu-id="52332-105">Demonstrates</span></span>  

 <span data-ttu-id="52332-106">カスタムの <xref:System.ServiceModel.Dispatcher.MessageQuery>、コンテンツ ベースの相関関係。</span><span class="sxs-lookup"><span data-stu-id="52332-106">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="52332-107">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="52332-107">Discussion</span></span>  

 <span data-ttu-id="52332-108">このサンプルでは、関連付けのために <xref:System.ServiceModel.Dispatcher.MessageQuery> 基本クラスから拡張する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="52332-108">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="52332-109">カスタム実装の `LinqMessageQuery` を使用すると、XLinq を使用してメッセージ内で検索する XName を指定できます。</span><span class="sxs-lookup"><span data-stu-id="52332-109">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="52332-110">クエリによって取得されたデータを使用して、メッセージを適切なワークフロー インスタンスにディスパッチするための相関関係キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="52332-110">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="52332-111">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="52332-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="52332-112">このサンプルでは、HTTP エンドポイントを使用してワークフロー サービスを公開します。</span><span class="sxs-lookup"><span data-stu-id="52332-112">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="52332-113">このサンプルを実行するには、適切な URL Acl を追加する必要があります (詳細については、「 [HTTP および HTTPS の構成](../../wcf/feature-details/configuring-http-and-https.md) 」を参照してください)。管理者として Visual Studio を実行するか、管理者特権のプロンプトで次のコマンドを実行して適切な acl を追加します。</span><span class="sxs-lookup"><span data-stu-id="52332-113">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="52332-114">ドメインとユーザー名は置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="52332-114">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="52332-115">URL ACL を追加したら、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="52332-115">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="52332-116">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="52332-116">Build the solution.</span></span>  
  
    2. <span data-ttu-id="52332-117">複数のスタートアッププロジェクトを設定するには、ソリューションを右クリックし、[ **スタートアッププロジェクトの設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52332-117">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="52332-118">**サービス** と **クライアント** を (この順序で) 複数のスタートアッププロジェクトとして追加します。</span><span class="sxs-lookup"><span data-stu-id="52332-118">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="52332-119">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="52332-119">Run the application.</span></span> <span data-ttu-id="52332-120">クライアント コンソールには、注文を送信し、発注書 ID を受信した後に、注文を確認するワークフローが示されます。</span><span class="sxs-lookup"><span data-stu-id="52332-120">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="52332-121">Service のウィンドウには、処理されている要求が示されます。</span><span class="sxs-lookup"><span data-stu-id="52332-121">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="52332-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="52332-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52332-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="52332-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="52332-124">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="52332-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52332-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="52332-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
