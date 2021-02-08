---
description: 詳細については、OperationContext へのアクセス
title: OperationContext へのアクセス
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 768475f115f653630aaedeee976d0c96bc9e4dd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792623"
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="0f8d2-103">OperationContext へのアクセス</span><span class="sxs-lookup"><span data-stu-id="0f8d2-103">Accessing OperationContext</span></span>

<span data-ttu-id="0f8d2-104">このサンプルでは、メッセージングアクティビティ ( <xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.Send> ) をカスタムスコープアクティビティと共に使用して、 <xref:System.ServiceModel.OperationContext.Current%2A> 送信メッセージまたは受信メッセージ内のカスタムメッセージヘッダーにアクセスして接続または取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-104">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0f8d2-105">対象</span><span class="sxs-lookup"><span data-stu-id="0f8d2-105">Demonstrates</span></span>  

 <span data-ttu-id="0f8d2-106">メッセージング アクティビティ、<xref:System.ServiceModel.Activities.ISendMessageCallback>、<xref:System.ServiceModel.Activities.IReceiveMessageCallback>。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-106">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="0f8d2-107">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="0f8d2-107">Discussion</span></span>  

 <span data-ttu-id="0f8d2-108">このサンプルでは、メッセージング アクティビティで拡張ポイント (<xref:System.ServiceModel.Activities.ISendMessageCallback> および <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) を使用して <xref:System.ServiceModel.OperationContext.Current%2A> にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-108">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="0f8d2-109">これらのコールバックは、実行時にメッセージング アクティビティによって取得される <xref:System.Activities.IExecutionProperty> の実装としてワークフロー ランタイム内に登録されます。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-109">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="0f8d2-110">その <xref:System.Activities.IExecutionProperty> 実装と同じスコープ内のメッセージング アクティビティはすべて影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-110">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="0f8d2-111">具体的には、このサンプルでは、カスタムのスコープ アクティビティを使用してコールバック動作を適用します。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-111">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="0f8d2-112"><xref:System.ServiceModel.Activities.ISendMessageCallback> は、ワークフローの <xref:System.Activities.WorkflowApplication.Id%2A> を送信 <xref:System.ServiceModel.Channels.MessageHeader> として含めるためにクライアント ワークフローで使用されます。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-112">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="0f8d2-113">このヘッダーはサービスで <xref:System.ServiceModel.Activities.IReceiveMessageCallback> を使用して取得され、ヘッダーの値がコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-113">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0f8d2-114">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="0f8d2-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0f8d2-115">このサンプルでは、HTTP エンドポイントを使用してワークフロー サービスを公開します。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-115">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="0f8d2-116">このサンプルを実行するには、適切な URL Acl を追加する必要があります (詳細については、「 [HTTP および HTTPS の構成](../../wcf/feature-details/configuring-http-and-https.md) 」を参照してください)。管理者として Visual Studio を実行するか、管理者特権のプロンプトで次のコマンドを実行して適切な acl を追加します。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-116">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="0f8d2-117">ドメインとユーザー名は置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-117">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="0f8d2-118">URL ACL を追加したら、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-118">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="0f8d2-119">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-119">Build the solution.</span></span>  
  
    2. <span data-ttu-id="0f8d2-120">複数のスタートアッププロジェクトを設定するには、ソリューションを右クリックし、[ **スタートアッププロジェクトの設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-120">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3. <span data-ttu-id="0f8d2-121">**サービス** と **クライアント** を (この順序で) 複数のスタートアッププロジェクトとして追加します。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-121">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4. <span data-ttu-id="0f8d2-122">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-122">Run the application.</span></span> <span data-ttu-id="0f8d2-123">クライアント コンソールに実行中のワークフローが 2 回示され、[サービス] ウィンドウにこれらのワークフローのインスタンス ID が示されます。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-123">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0f8d2-124">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0f8d2-125">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0f8d2-126">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0f8d2-127">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0f8d2-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
