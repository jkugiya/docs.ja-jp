---
description: 詳細については、「インターネットインフォメーションサービスでのホスト」を参照してください。
title: インターネット インフォメーション サービスでのホスティング
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 23c81bcfccba316500d333d277907d66e5d457c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743136"
---
# <a name="host-in-internet-information-services"></a><span data-ttu-id="5ef9b-103">インターネットインフォメーションサービスのホスト</span><span class="sxs-lookup"><span data-stu-id="5ef9b-103">Host in Internet Information Services</span></span>

<span data-ttu-id="5ef9b-104">Windows Communication Foundation (WCF) サービスをホストするための1つのオプションは、インターネットインフォメーションサービス (IIS) アプリケーションの内部にあります。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-104">One option for hosting Windows Communication Foundation (WCF) services is inside of an Internet Information Services (IIS) application.</span></span> <span data-ttu-id="5ef9b-105">このホスティングモデルは、ASP.NET および ASP.NET Web services (ASMX) Web サービスで使用されるモデルに似ています。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-105">This hosting model is similar to the model used by ASP.NET and ASP.NET Web services (ASMX) Web Services.</span></span>

## <a name="versions-of-iis"></a><span data-ttu-id="5ef9b-106">IIS バージョン</span><span class="sxs-lookup"><span data-stu-id="5ef9b-106">Versions of IIS</span></span>

<span data-ttu-id="5ef9b-107">WCF は、次のオペレーティングシステム上の IIS の次のバージョンでホストできます。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-107">WCF can be hosted on the following versions of IIS on the following operating systems:</span></span>

- <span data-ttu-id="5ef9b-108">Windows XP SP2 の IIS 5.1。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-108">IIS 5.1 on Windows XP SP2.</span></span> <span data-ttu-id="5ef9b-109">この環境は、後で Windows Server 2003 などのサーバーオペレーティングシステムに展開される IIS でホストされるアプリケーションの設計と開発に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-109">This environment is useful for the design and development of IIS-hosted applications that are later deployed on a server operating system such as Windows Server 2003.</span></span>

- <span data-ttu-id="5ef9b-110">Windows Server 2003 上の IIS 6.0:</span><span class="sxs-lookup"><span data-stu-id="5ef9b-110">IIS 6.0 on Windows Server 2003.</span></span> <span data-ttu-id="5ef9b-111">IIS 6.0 は、スケーラビリティ、信頼性、およびアプリケーションの分離が強化された高度なプロセス モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-111">IIS 6.0 provides an advanced process model that offers improved scalability, reliability, and application isolation.</span></span> <span data-ttu-id="5ef9b-112">この環境は、HTTP 通信のみを使用する WCF サービスの運用環境へのデプロイに適しています。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-112">This environment is suitable for production deployment of WCF services that use HTTP communication exclusively.</span></span>

- <span data-ttu-id="5ef9b-113">Windows Vista および Windows Server 2008 の IIS 7.0。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-113">IIS 7.0 on Windows Vista and Windows Server 2008.</span></span> <span data-ttu-id="5ef9b-114">IIS 7.0 は、IIS 6.0 と同じ高度なプロセスモデルを提供しますが、Windows プロセスアクティブ化サービス (WAS) を使用して、HTTP 以外のプロトコルを介したアクティベーションとネットワーク通信を許可します。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-114">IIS 7.0 provides the same advanced process model as IIS 6.0, but uses the Windows Process Activation Service (WAS) to allow activation and network communication over protocols other than HTTP.</span></span> <span data-ttu-id="5ef9b-115">この環境は、WCF でサポートされている任意のネットワークプロトコル (HTTP、net.tcp、net.pipe、および net.tcp を含む) を介して通信する WCF サービスの開発に適しています。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-115">This environment is suitable for the development of WCF services that communicate over any network protocol supported by WCF (including HTTP, net.tcp, net.pipe, and net.msmq).</span></span> <span data-ttu-id="5ef9b-116">WAS の詳細については、「 [Windows プロセスアクティブ化サービスでのホスト](hosting-in-windows-process-activation-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-116">For more information about WAS, see [Hosting in Windows Process Activation Service](hosting-in-windows-process-activation-service.md).</span></span>

- <span data-ttu-id="5ef9b-117">[Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)) は、IIS 7.0 および Windows プロセスアクティブ化サービス (WAS) と連携して、NET4 WCF および WF サービスのための豊富なアプリケーションホスティング環境を提供します。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-117">[Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)) works with IIS 7.0 and Windows Process Activation Service (WAS) to provide a rich application hosting environment for NET4 WCF and WF services.</span></span> <span data-ttu-id="5ef9b-118">この利点には、プロセス ライフサイクル管理、プロセス リサイクル、共有ホスティング、迅速な障害保護、プロセスの孤立化、オンデマンド アクティブ化、状態監視などがあります。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-118">These benefits include process life-cycle management, process recycling, shared hosting, rapid failure protection, process orphaning, on-demand activation, and health monitoring.</span></span> <span data-ttu-id="5ef9b-119">詳細については、「 [appfabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10)) 」と「 [appfabric のホスティングの概念](/previous-versions/appfabric/ee677371(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-119">For detailed information, see [AppFabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10)) and [AppFabric Hosting Concepts](/previous-versions/appfabric/ee677371(v=azure.10)).</span></span>

## <a name="benefits-of-iis-hosting"></a><span data-ttu-id="5ef9b-120">IIS ホストの利点</span><span class="sxs-lookup"><span data-stu-id="5ef9b-120">Benefits of IIS hosting</span></span>

<span data-ttu-id="5ef9b-121">IIS で WCF サービスをホストすると、いくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-121">Hosting WCF services in IIS has several benefits:</span></span>

- <span data-ttu-id="5ef9b-122">IIS でホストされている WCF サービスは、ASP.NET アプリケーションや ASMX など、他の種類の IIS アプリケーションと同様に展開および管理されます。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-122">WCF services hosted in IIS are deployed and managed like any other type of IIS application, including ASP.NET applications and ASMX.</span></span>

- <span data-ttu-id="5ef9b-123">IIS はプロセスのアクティブ化、状態管理、リサイクル機能を提供し、ホストされるアプリケーションの信頼性を向上します。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-123">IIS provides process activation, health management, and recycling capabilities to increase the reliability of hosted applications.</span></span>

- <span data-ttu-id="5ef9b-124">ASP.NET と同様に、ASP.NET でホストされる WCF サービスは、サーバーの密度とスケーラビリティを向上させるために、共通のワーカープロセス内に複数のアプリケーションが存在する ASP.NET 共有ホスティングモデルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-124">Like ASP.NET, WCF services hosted in ASP.NET can take advantage of the ASP.NET shared hosting model where multiple applications reside in a common worker process for improved server density and scalability.</span></span>

- <span data-ttu-id="5ef9b-125">IIS でホストされる WCF サービスは、ASP.NET 2.0 と同じ動的コンパイルモデルを使用します。これにより、ホステッドサービスの開発とデプロイが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-125">WCF services hosted in IIS use the same dynamic compilation model as ASP.NET 2.0, which simplifies development and deployment of hosted services.</span></span>

<span data-ttu-id="5ef9b-126">IIS で WCF サービスをホストする場合は、IIS 5.1 と IIS 6.0 が HTTP 通信のみに制限されていることに注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-126">When deciding to host WCF services in IIS, it is important to remember that IIS 5.1 and IIS 6.0 are limited to HTTP communication only.</span></span> <span data-ttu-id="5ef9b-127">ホスティング環境の選択の詳細については、「 [ホスティングサービス](../hosting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-127">For more information about choosing a hosting environment, see [Hosting Services](../hosting-services.md).</span></span>

## <a name="deploy-an-iis-hosted-wcf-service"></a><span data-ttu-id="5ef9b-128">IIS でホストされる WCF サービスを展開する</span><span class="sxs-lookup"><span data-stu-id="5ef9b-128">Deploy an IIS-hosted WCF service</span></span>

<span data-ttu-id="5ef9b-129">IIS でホストされる WCF サービスの開発と展開は、次のタスクで構成されています。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-129">Developing and deploying an IIS-hosted WCF service consists of the following tasks:</span></span>

- <span data-ttu-id="5ef9b-130">IIS、ASP.NET、WCF、および WCF HTTP アクティブ化コンポーネントが正しくインストールおよび登録されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-130">Ensure that IIS, ASP.NET, WCF, and the WCF HTTP activation component are correctly installed and registered.</span></span>

- <span data-ttu-id="5ef9b-131">新しい IIS アプリケーションを作成するか、既存の ASP.NET アプリケーションを再利用します。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-131">Create a new IIS application, or reuse an existing ASP.NET application.</span></span>

- <span data-ttu-id="5ef9b-132">WCF サービスの .svc ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-132">Create a .svc file for the WCF service.</span></span>

- <span data-ttu-id="5ef9b-133">IIS アプリケーションにサービス実装を展開します。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-133">Deploy the service implementation to the IIS application.</span></span>

- <span data-ttu-id="5ef9b-134">WCF サービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-134">Configure the WCF service.</span></span>

<span data-ttu-id="5ef9b-135">これらの各タスクの詳細については、「 [WCF サービス Services-Hosted のインターネット情報の展開](deploying-an-internet-information-services-hosted-wcf-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-135">For a discussion of each of these tasks, see [Deploying an Internet Information Services-Hosted WCF Service](deploying-an-internet-information-services-hosted-wcf-service.md).</span></span>

## <a name="wcf-services-and-aspnet"></a><span data-ttu-id="5ef9b-136">WCF サービスと ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5ef9b-136">WCF services and ASP.NET</span></span>

<span data-ttu-id="5ef9b-137">WCF サービスは、ASP.NET とサイドバイサイドでホストすることも、ASP.NET 互換モードでホストすることもできます。このモードでは、ASP.NET Web アプリケーションプラットフォームによって提供される機能をサービスが最大限に活用できます。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-137">WCF services can be hosted either side-by-side with ASP.NET or in ASP.NET Compatibility Mode in which services can take full advantage of features provided by the ASP.NET Web application platform.</span></span> <span data-ttu-id="5ef9b-138">これらの機能の詳細については、「 [WCF Services と ASP.NET](wcf-services-and-aspnet.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef9b-138">For a discussion of these features, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ef9b-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ef9b-139">See also</span></span>

- [<span data-ttu-id="5ef9b-140">ServiceHostFactory を使用したホストの拡張</span><span class="sxs-lookup"><span data-stu-id="5ef9b-140">Extending Hosting Using ServiceHostFactory</span></span>](../extending/extending-hosting-using-servicehostfactory.md)
- [<span data-ttu-id="5ef9b-141">インターネット インフォメーション サービスでホストされる WCF サービスの配置</span><span class="sxs-lookup"><span data-stu-id="5ef9b-141">Deploying an Internet Information Services-Hosted WCF Service</span></span>](deploying-an-internet-information-services-hosted-wcf-service.md)
- [<span data-ttu-id="5ef9b-142">WCF サービスと ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5ef9b-142">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="5ef9b-143">インターネット インフォメーション サービス ホスティングのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="5ef9b-143">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="5ef9b-144">Windows Communication Foundation での Internet Information Services 7.0 の構成</span><span class="sxs-lookup"><span data-stu-id="5ef9b-144">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>](configuring-iis-for-wcf.md)
- <span data-ttu-id="5ef9b-145">[AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5ef9b-145">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
