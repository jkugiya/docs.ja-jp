---
description: 詳細については、「ワークフローサービスのホスティング」を参照してください。
title: ワークフロー サービスのホスティング
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: 8d7d5bbc8b084ac74e51fe3906fd5eef13b5ea09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743006"
---
# <a name="hosting-workflow-services"></a><span data-ttu-id="ece45-103">ワークフロー サービスのホスティング</span><span class="sxs-lookup"><span data-stu-id="ece45-103">Hosting Workflow Services</span></span>

<span data-ttu-id="ece45-104">ワークフロー サービスが受信メッセージに応答するには、ワークフロー サービスがホストされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ece45-104">A workflow service must be hosted for it to respond to incoming messages.</span></span> <span data-ttu-id="ece45-105">ワークフロー サービスは WCF メッセージング インフラストラクチャを使用するため、これと似た方法でホストされます。</span><span class="sxs-lookup"><span data-stu-id="ece45-105">Workflow services use the WCF messaging infrastructure and are therefore hosted in similar ways.</span></span> <span data-ttu-id="ece45-106">WCF サービスと同様に、ワークフローサービスは、インターネットインフォメーションサービス (IIS) または Windows プロセスアクティブ化サービス (WAS) の下で、任意のマネージアプリケーションでホストできます。</span><span class="sxs-lookup"><span data-stu-id="ece45-106">Like WCF services, workflow services can be hosted in any managed application, under Internet Information Services (IIS), or under Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="ece45-107">また、ワークフローサービスは Windows Server App Fabric でホストできます。</span><span class="sxs-lookup"><span data-stu-id="ece45-107">In addition, workflow services can be hosted under Windows Server App Fabric.</span></span> <span data-ttu-id="ece45-108">Windows Server App Fabric の詳細については、「 [Windows Server App fabric のドキュメント](/previous-versions/appfabric/ff384253(v=azure.10))」、「 [Appfabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))」、および「 [appfabric のホスティングの概念](/previous-versions/appfabric/ee677371(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ece45-108">For more information about Windows Server App Fabric see [Windows Server App Fabric documentation](/previous-versions/appfabric/ff384253(v=azure.10)), [AppFabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10)), and [AppFabric Hosting Concepts](/previous-versions/appfabric/ee677371(v=azure.10)).</span></span> <span data-ttu-id="ece45-109">WCF サービスをホストするさまざまな方法の詳細については、「 [ホスティングサービス](../hosting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ece45-109">For more information about the various ways to host WCF services see [Hosting Services](../hosting-services.md).</span></span>

## <a name="hosting-in-a-managed-application"></a><span data-ttu-id="ece45-110">マネージド アプリケーションでのホスト</span><span class="sxs-lookup"><span data-stu-id="ece45-110">Hosting in a managed application</span></span>

 <span data-ttu-id="ece45-111">マネージド アプリケーションでワークフロー サービスをホストするには、<xref:System.ServiceModel.Activities.WorkflowServiceHost> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ece45-111">To host a workflow service in a managed application, use the <xref:System.ServiceModel.Activities.WorkflowServiceHost> class.</span></span> <span data-ttu-id="ece45-112"><xref:System.ServiceModel.Activities.WorkflowServiceHost> コンストラクターにより、シングルトン ワークフロー サービス インスタンス、ワークフロー サービス定義、またはワークフロー メッセージング アクティビティを使用するアクティビティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ece45-112">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> constructor allows you to specify a singleton workflow service instance, a workflow service definition, or an activity that uses the workflow messaging activities.</span></span> <span data-ttu-id="ece45-113"><xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> の呼び出しによって、サービスが受信メッセージのリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="ece45-113">Calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> causes the service to start listening for incoming messages.</span></span>

## <a name="hosting-under-iis-or-was"></a><span data-ttu-id="ece45-114">IIS または WAS の下でのホスト</span><span class="sxs-lookup"><span data-stu-id="ece45-114">Hosting under IIS or WAS</span></span>

 <span data-ttu-id="ece45-115">IIS または WAS の下でワークフロー サービスをホストする場合は、仮想ディレクトリを作成し、サービスとその動作を定義するファイルをその仮想ディレクトリ内に配置します。</span><span class="sxs-lookup"><span data-stu-id="ece45-115">Hosting a workflow service under IIS or WAS involves creating a virtual directory and placing files in the virtual directory that define the service and its behavior.</span></span> <span data-ttu-id="ece45-116">IIS または WAS の下でワークフローをホストする場合は、いくつかの方法が考えられます。</span><span class="sxs-lookup"><span data-stu-id="ece45-116">When hosting a workflow service under IIS or WAS there are several possibilities:</span></span>

- <span data-ttu-id="ece45-117">ワークフロー サービスを定義する .xamlx ファイルを、サービス動作、エンドポイント、およびその他の構成要素を指定する Web.config ファイルと共に、IIS/WAS 仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="ece45-117">Place a .xamlx file that defines the workflow service in an IIS/WAS virtual directory along with a Web.config file that specifies the service behaviors, endpoints, and other configuration elements.</span></span>

- <span data-ttu-id="ece45-118">ワークフロー サービスを定義する .xamlx ファイルを IIS/WAS 仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="ece45-118">Place a .xamlx file that defines the workflow service in an IIS/WAS virtual directory.</span></span> <span data-ttu-id="ece45-119">この .xamlx ファイルで、公開するエンドポイントが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ece45-119">The .xamlx file specifies the endpoints to expose.</span></span> <span data-ttu-id="ece45-120">エンドポイントは、次の例に示すように、`WorkflowService.Endpoints` 要素で指定されます。</span><span class="sxs-lookup"><span data-stu-id="ece45-120">Endpoints are specified in a `WorkflowService.Endpoints` element as shown in the following example.</span></span>

    ```xml
    <WorkflowService xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"  xmlns:p1="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
      <WorkflowService.Endpoints>
        <Endpoint ServiceContractName="IWorkFlowEchoService" AddressUri="">
          <Endpoint.Binding>
            <BasicHttpBinding />
          </Endpoint.Binding>
        </Endpoint>
      </WorkflowService.Endpoints>
    <!-- ... -->
    </WorkflowService>
    ```

    > [!NOTE]
    > <span data-ttu-id="ece45-121">動作は .xamlx ファイルで指定できないため、動作設定を指定するには Web.config を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ece45-121">Behaviors cannot be specified in a .xamlx file, so you must use a Web.config if you need to specify behavior settings.</span></span>

- <span data-ttu-id="ece45-122">ワークフロー サービスを定義する .xamlx ファイルを IIS/WAS 仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="ece45-122">Place a .xamlx file that defines the workflow service in an IIS/WAS virtual directory.</span></span> <span data-ttu-id="ece45-123">さらに、.svc ファイルを仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="ece45-123">In addition, place a .svc file in the virtual directory.</span></span> <span data-ttu-id="ece45-124">.svc ファイルでは、カスタム Web サービス ホスト ファクトリの指定、カスタム動作の適用、またはカスタムの場所からの構成の読み込みが可能です。</span><span class="sxs-lookup"><span data-stu-id="ece45-124">The .svc file allows you to specify a custom Web service host factory, apply custom behavior, or load configuration from a custom location.</span></span>

- <span data-ttu-id="ece45-125">WCF メッセージング アクティビティを使用するアクティビティを含むアセンブリを IIS/WAS 仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="ece45-125">Place an assembly in the IIS/WAS virtual directory that contains an activity that uses the WCF messaging activities.</span></span>

 <span data-ttu-id="ece45-126">ワークフローサービスを定義する .xamlx ファイルには、<`Service`> ルート要素、またはから派生した任意の型を含むルート要素が含まれている必要があり <xref:System.Workflow.ComponentModel.Activity> ます。</span><span class="sxs-lookup"><span data-stu-id="ece45-126">A .xamlx file that defines a workflow service must contain a <`Service`> root element or a root element that contains any type derived from <xref:System.Workflow.ComponentModel.Activity>.</span></span> <span data-ttu-id="ece45-127">Visual Studio アクティビティテンプレートを使用すると、.xamlx ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ece45-127">When using the Visual Studio activity template, a .xamlx file is created.</span></span> <span data-ttu-id="ece45-128">WCF ワークフローサービステンプレートを使用すると、.xamlx ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ece45-128">When using the WCF Workflow Service template, a .xamlx file is created.</span></span>

## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a><span data-ttu-id="ece45-129">Windows Server AppFabric でのワークフロー サービスのホスティング</span><span class="sxs-lookup"><span data-stu-id="ece45-129">Hosting Workflow Services under Windows Server App Fabric</span></span>

 <span data-ttu-id="ece45-130">Windows Server AppFabric でのワークフロー サービスのホスティングは IIS/WAS でのホスティングと同じ方法で行われます。</span><span class="sxs-lookup"><span data-stu-id="ece45-130">Hosting a workflow service under Windows Server App Fabric is done in the same way as hosting under IIS/WAS.</span></span> <span data-ttu-id="ece45-131">唯一の違いは、Windows Server AppFabric がインストールされるということです。</span><span class="sxs-lookup"><span data-stu-id="ece45-131">The only difference is the fact that Windows Server App Fabric is installed.</span></span> <span data-ttu-id="ece45-132">Windows Server App Fabric には、インターネットインフォメーションサービス Manager に追加されるツールと PowerShell コマンドレットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ece45-132">Windows Server App Fabric provides tools that are added to Internet Information Services Manager, as well as PowerShell commandlets.</span></span> <span data-ttu-id="ece45-133">これらのツールによって、ワークフロー サービスおよび WCF サービスの配置、管理、および追跡を簡略化することができます。</span><span class="sxs-lookup"><span data-stu-id="ece45-133">These tools simplify deploying, managing, and tracking of workflow services and WCF services.</span></span>

## <a name="referencing-custom-activities"></a><span data-ttu-id="ece45-134">カスタム アクティビティの参照</span><span class="sxs-lookup"><span data-stu-id="ece45-134">Referencing Custom Activities</span></span>

 <span data-ttu-id="ece45-135">カスタムアクティビティへの参照は、 `Assemblies` `System.Web.Compilation` アプリケーションドメインに読み込まれ、XAML デシリアライザーが型を見つけることができるように、<> の下の <> セクションに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ece45-135">References to custom activities must be added to the <`Assemblies`> section under <`System.Web.Compilation`> so that they are loaded into the Application Domain and the XAML deserializer is able to locate the types.</span></span> <span data-ttu-id="ece45-136">これらの設定をコンピューター上のすべてのアプリケーションに適用する必要がある場合は、アプリケーション レベルまたはルートの Web.config で設定できます。</span><span class="sxs-lookup"><span data-stu-id="ece45-136">These settings can be made at the application level or in the root Web.config if the settings should be applied to all applications on the machine.</span></span>

## <a name="deployment"></a><span data-ttu-id="ece45-137">デプロイ</span><span class="sxs-lookup"><span data-stu-id="ece45-137">Deployment</span></span>

 <span data-ttu-id="ece45-138">配置作業を容易にするために、Web 配置ツールが作成されています。</span><span class="sxs-lookup"><span data-stu-id="ece45-138">The Web Deployment tool has been created to make the job of deployment easier.</span></span> <span data-ttu-id="ece45-139">このツールを使用すると、アプリケーションの IIS 6.0 および IIS 7.0 間での移行や、サーバー ファームの同期のほか、Web アプリケーションのパッケージ化、アーカイブ、および配置を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ece45-139">The tool allows you to migrate applications between IIS 6.0 and IIS 7.0, synchronize server farms, and package, archive and deploy Web applications.</span></span> <span data-ttu-id="ece45-140">詳細については、「 [MS Deployment Tool](https://go.microsoft.com/fwlink/?LinkId=178690)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ece45-140">For more information, see [MS Deployment Tool](https://go.microsoft.com/fwlink/?LinkId=178690).</span></span>

## <a name="see-also"></a><span data-ttu-id="ece45-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="ece45-141">See also</span></span>

- [<span data-ttu-id="ece45-142">ワークフロー サービス ホストの内部</span><span class="sxs-lookup"><span data-stu-id="ece45-142">Workflow Service Host Internals</span></span>](workflow-service-host-internals.md)
- [<span data-ttu-id="ece45-143">WorkflowServiceHost の構成</span><span class="sxs-lookup"><span data-stu-id="ece45-143">Configuring WorkflowServiceHost</span></span>](configuring-workflowservicehost.md)
