---
description: '詳細情報: ホスティング'
title: Hosting2
ms.date: 03/30/2017
ms.assetid: 0820c7e5-0b50-4cde-80e7-74e346513002
ms.openlocfilehash: 4371cbb3b65242235ad0bb26c2b99b8e35d729c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742967"
---
# <a name="hosting"></a><span data-ttu-id="eb707-103">Hosting</span><span class="sxs-lookup"><span data-stu-id="eb707-103">Hosting</span></span>

<span data-ttu-id="eb707-104">このセクションのトピックでは、サービス ホスティングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="eb707-104">The topics in the section describe service hosting.</span></span> <span data-ttu-id="eb707-105">サービスは、インターネットインフォメーションサービス (IIS)、windows プロセスアクティブ化サービス (WAS)、Windows Server AppFabric、Windows サービス、またはマネージアプリケーションによってホストできます。このオプションは、多くの場合、 *自己ホスト* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="eb707-105">A service can be hosted by Internet Information Services (IIS), Windows Process Activation Service (WAS), Windows Server AppFabric, a Windows service, or by a managed application—this option is often referred to as *self hosting*.</span></span>  
  
 <span data-ttu-id="eb707-106">信頼されていないホストからサービスや拡張機能を実行すると、セキュリティが損なわれるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="eb707-106">It is important to note that running a service or any extension from an untrusted host compromises security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb707-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="eb707-107">In This Section</span></span>  

 [<span data-ttu-id="eb707-108">インターネット インフォメーション サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="eb707-108">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)  
 <span data-ttu-id="eb707-109">Windows Communication Foundation (WCF) サービスがインターネットインフォメーションサービスまたは [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10))でどのようにホストされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="eb707-109">Describes how a Windows Communication Foundation (WCF) service is hosted in Internet Information Services or [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)).</span></span>  
  
 [<span data-ttu-id="eb707-110">Windows プロセス アクティブ化サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="eb707-110">Hosting in Windows Process Activation Service</span></span>](hosting-in-windows-process-activation-service.md)  
 <span data-ttu-id="eb707-111">WCF サービスが Windows プロセスアクティブ化サービスによってどのようにホストされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="eb707-111">Describes how a WCF service is hosted by Windows Process Activation Service.</span></span>  
  
 [<span data-ttu-id="eb707-112">Windows サービス アプリケーションのホスト</span><span class="sxs-lookup"><span data-stu-id="eb707-112">Hosting in a Windows Service Application</span></span>](hosting-in-a-windows-service-application.md)  
 <span data-ttu-id="eb707-113">WCF サービスが Windows サービスによってどのようにホストされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="eb707-113">Describes how a WCF service is hosted by a Windows service.</span></span>  
  
 [<span data-ttu-id="eb707-114">マネージド アプリケーションのホスト</span><span class="sxs-lookup"><span data-stu-id="eb707-114">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)  
 <span data-ttu-id="eb707-115">マネージアプリケーションでの WCF サービスのホスト方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb707-115">Describes how a WCF service is hosted in a managed application.</span></span>  
  
 [<span data-ttu-id="eb707-116">IIS と WAS における構成ベースのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="eb707-116">Configuration-Based Activation in IIS and WAS</span></span>](configuration-based-activation-in-iis-and-was.md)  
 <span data-ttu-id="eb707-117">.Svc ファイルを使用せずに、IIS または WAS で WCF サービスをホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb707-117">Describes how a WCF service is hosted under IIS or WAS without using a .svc file.</span></span>  
  
 [<span data-ttu-id="eb707-118">複数の IIS サイト バインディングのサポート</span><span class="sxs-lookup"><span data-stu-id="eb707-118">Supporting Multiple IIS Site Bindings</span></span>](supporting-multiple-iis-site-bindings.md)  
 <span data-ttu-id="eb707-119">1 つの Web サイト上で同じ URI スキームを使用してサービスの複数のベース アドレスを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb707-119">Describes how to specify multiple base addresses for a service using the same URI scheme on a single Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb707-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb707-120">See also</span></span>

- [<span data-ttu-id="eb707-121">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="eb707-121">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="eb707-122">[AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="eb707-122">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
