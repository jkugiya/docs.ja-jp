---
description: 詳細については、「マネージアプリケーションでのホスティング」を参照してください。
title: マネージド アプリケーションのホスト
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 14fd6b2dea1a4315567611f505f2898314a07908
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756202"
---
# <a name="hosting-in-a-managed-application"></a><span data-ttu-id="35476-103">マネージド アプリケーションのホスト</span><span class="sxs-lookup"><span data-stu-id="35476-103">Hosting in a Managed Application</span></span>

<span data-ttu-id="35476-104">Windows Communication Foundation (WCF) サービスは、任意の .NET Framework アプリケーションでホストできます。</span><span class="sxs-lookup"><span data-stu-id="35476-104">Windows Communication Foundation (WCF) services can be hosted in any .NET Framework application.</span></span> <span data-ttu-id="35476-105">自己ホスト型サービスは、展開を要するインフラストラクチャが最も少ないので、最も柔軟なホスト オプションです。</span><span class="sxs-lookup"><span data-stu-id="35476-105">Self-hosting services is the most flexible hosting option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="35476-106">ただし、マネージアプリケーションは、インターネットインフォメーションサービス (IIS) や Windows サービスなど、WCF の他のホストオプションの高度なホスト機能や管理機能を提供しないため、最も信頼性の低いホストオプションでもあります。</span><span class="sxs-lookup"><span data-stu-id="35476-106">However, it is also the least robust hosting option, because managed applications do not provide the advanced hosting and management features of other hosting options in WCF, such as Internet Information Services (IIS) and Windows services.</span></span>  
  
 <span data-ttu-id="35476-107">自己ホスト型サービスを作成するには、メッセージをリッスンするサービスを開始する <xref:System.ServiceModel.ServiceHost>のインスタンスを作成して開きます。</span><span class="sxs-lookup"><span data-stu-id="35476-107">To create a self-hosted service, create and open an instance of the <xref:System.ServiceModel.ServiceHost>, which starts a service listening for messages.</span></span> <span data-ttu-id="35476-108">詳細については、「 [方法: マネージアプリケーションで WCF サービスをホスト](../how-to-host-a-wcf-service-in-a-managed-application.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35476-108">For more information, see [How to: Host a WCF Service in a Managed Application](../how-to-host-a-wcf-service-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="35476-109">コントラクトを定義する方法、コントラクトを実装する方法、およびマネージアプリケーション内でサービスをホストする方法の完全な例については、 [はじめにチュートリアル](../getting-started-tutorial.md) と [自己ホスト](../samples/self-host.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35476-109">For a complete example on how to define a contract, implement the contract, and host a service inside of a managed application see the [Getting Started Tutorial](../getting-started-tutorial.md) and the [Self-Host](../samples/self-host.md).</span></span>  
  
 <span data-ttu-id="35476-110">以下に、このホスト オプションを使用する一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="35476-110">The following sections describe common scenarios that use this hosting option.</span></span>  
  
## <a name="console-applications"></a><span data-ttu-id="35476-111">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="35476-111">Console Applications</span></span>  

 <span data-ttu-id="35476-112">自己ホストによって可能になる一般的なシナリオは、コンソールアプリケーション内で実行される WCF サービスです。</span><span class="sxs-lookup"><span data-stu-id="35476-112">Common scenarios that self-hosting enables are WCF services running inside console applications.</span></span> <span data-ttu-id="35476-113">通常、コンソールアプリケーション内で WCF サービスをホストすることは、サービスの開発フェーズで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="35476-113">Hosting a WCF service inside a console application is typically useful during the development phase of the service.</span></span> <span data-ttu-id="35476-114">コンソール アプリケーションにより、アプリケーション内部で起こっている状況を見極めるための情報のデバッグやトレースが容易になり、新しい場所にアプリケーションをコピーして移動することも簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="35476-114">This makes them easy to debug, easy to get trace information from to find out what is happening inside of the application, and easy to move around by copying them to new locations.</span></span>  
  
## <a name="rich-client-applications"></a><span data-ttu-id="35476-115">リッチ クライアント アプリケーション</span><span class="sxs-lookup"><span data-stu-id="35476-115">Rich Client Applications</span></span>  

 <span data-ttu-id="35476-116">自己ホストによって有効になるその他の一般的なシナリオとしては、Windows Presentation Foundation (WPF) または Windows フォーム (WinForms) に基づいたクライアントアプリケーションなどがあります。</span><span class="sxs-lookup"><span data-stu-id="35476-116">Other common scenarios that self-hosting enables are rich client applications, such as those based on Windows Presentation Foundation (WPF) or Windows Forms (WinForms).</span></span> <span data-ttu-id="35476-117">また、このホストオプションを使用すると、WPF や WinForms アプリケーションなどのリッチクライアントアプリケーションで外部との通信を容易に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="35476-117">This hosting option also makes it easy for rich client applications, such as WPF and WinForms applications, to communicate with the outside world.</span></span> <span data-ttu-id="35476-118">たとえば、ユーザーインターフェイスに WPF を使用し、他のクライアントがそれに接続して情報を共有できるようにする WCF サービスもホストするピアツーピアコラボレーションクライアントなどです。</span><span class="sxs-lookup"><span data-stu-id="35476-118">For example, a peer-to-peer collaboration client that uses WPF for its user interface and also hosts a WCF service that allows other clients to connect to it and share information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35476-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="35476-119">See also</span></span>

- [<span data-ttu-id="35476-120">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="35476-120">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="35476-121">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="35476-121">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
