---
description: '詳細情報: <standardEndpoints>'
title: <standardEndpoints>
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: f792f55b2c0c76727f4aaee50df072ee0c8bdbc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786656"
---
# \<standardEndpoints>

<span data-ttu-id="b8a9f-102">この構成セクションでは、再使用可能な構成済みのエンドポイントである標準エンドポイントのコレクションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-102">This configuration section allows you to define a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="b8a9f-103">標準エンドポイントは、固定値に設定されたアドレス、バインディング、およびコントラクトの 1 つ以上の属性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-103">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="b8a9f-104">たとえば、探索エンドポイントでは、コントラクトが固定されています。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-104">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="b8a9f-105">標準エンドポイントを使用して、カスタム バインドの定義と同様に新しいプロパティを指定して、サービス エンドポイントを拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-105">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoints>**  
  
## <a name="syntax"></a><span data-ttu-id="b8a9f-106">構文</span><span class="sxs-lookup"><span data-stu-id="b8a9f-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8a9f-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b8a9f-107">Attributes and Elements</span></span>  

 <span data-ttu-id="b8a9f-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8a9f-109">属性</span><span class="sxs-lookup"><span data-stu-id="b8a9f-109">Attributes</span></span>  

 <span data-ttu-id="b8a9f-110">なし。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8a9f-111">子要素</span><span class="sxs-lookup"><span data-stu-id="b8a9f-111">Child Elements</span></span>  
  
|<span data-ttu-id="b8a9f-112">要素</span><span class="sxs-lookup"><span data-stu-id="b8a9f-112">Element</span></span>|<span data-ttu-id="b8a9f-113">説明</span><span class="sxs-lookup"><span data-stu-id="b8a9f-113">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="b8a9f-114">固定アナウンス コントラクトが含まれた標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-114">Defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="b8a9f-115">サービスは、サービスが開いたとき、または閉じたときにオンラインおよびオフラインのアナウンス メッセージを送信することによって、その可用性をアナウンスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-115">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="b8a9f-116">Windows Communication Foundation (WCF) サービスでは、要素内のアナウンスエンドポイントを指定 [\<serviceDiscovery>](servicediscovery.md) し、アナウンスメント Ementclient を使用してアナウンスを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-116">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="b8a9f-117">他のサービスからのアナウンスをリッスンするクライアントは、実際には WCF サービスとして機能します。そのため、「」セクションで、そのクライアントのアナウンスエンドポイントを構成する必要があり [\<services>](services.md) ます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-117">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="b8a9f-118">固定探索コントラクトが含まれた標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-118">Defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="b8a9f-119">サービスの構成に追加すると、この要素により、探索メッセージをリッスンする場所が指定されます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-119">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="b8a9f-120">クライアントの構成に追加すると、この要素により、探索クエリの送信先となる場所が指定されます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-120">When added to the client configuration it specifies where to send the discovery queries.</span></span>|  
|[\<dynamicEndpoint>](dynamicendpoint.md)|<span data-ttu-id="b8a9f-121">この構成要素は、アプリケーションが、実行時に動的にエンドポイント アドレスを検索するクライアント プログラムとして機能するための情報を格納する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-121">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
|[\<mexEndpoint>](mexendpoint.md)|<span data-ttu-id="b8a9f-122">固定 IMetadataExchange コントラクトが含まれた標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-122">Defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="b8a9f-123">IMetadataExchange はすべてのメタデータ交換エンドポイントでコントラクトとして指定されるため、独自のエンドポイントを定義せずにこの標準エンドポイントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-123">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|<span data-ttu-id="b8a9f-124">サービスが UDP バインディングでアナウンス メッセージを送信するために使用する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-124">Defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="b8a9f-125">これには固定コントラクトがあり、2 つの探索のバージョンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-125">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="b8a9f-126">また、WS-Discovery の仕様 (WS-Discovery April 2005 または WS-Discovery V1.1) に規定された固定 UDP バインディングと既定のアドレスも備えています。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-126">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="b8a9f-127">アナウンス メッセージの送受信に使用するマルチキャスト アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-127">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|<span data-ttu-id="b8a9f-128">UDP マルチキャスト バインディングを使用した探索操作用に事前に構成される標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-128">Defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="b8a9f-129">このエンドポイントには固定コントラクトがあり、WS-Discovery プロトコルの 2 つのバージョンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-129">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="b8a9f-130">また、WS-Discovery の仕様 (WS-Discovery April 2005 または WS-Discovery V1.1) に規定された固定 UDP バインディングと既定のアドレスも備えています。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-130">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>|  
|[\<webHttpEndpoint>](webhttpendpoint.md)|<span data-ttu-id="b8a9f-131">動作を自動的に追加する固定バインドを持つ標準エンドポイントを定義し [\<webHttpBinding>](webhttpbinding.md) [\<webHttp>](webhttp.md) ます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-131">Defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="b8a9f-132">このエンドポイントは、REST サービスを作成する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-132">Use this endpoint when writing a REST service.</span></span>|  
|[\<webScriptEndpoint>](webscriptendpoint.md)|<span data-ttu-id="b8a9f-133">動作を自動的に追加する固定バインドを持つ標準エンドポイントを定義し [\<webHttpBinding>](webhttpbinding.md) [\<enableWebScript>](enablewebscript.md) ます。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-133">Defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="b8a9f-134">このエンドポイントは、ASP.NET AJAX アプリケーションから呼び出されるサービスを作成する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-134">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>|  
|[\<workflowControlEndpoint>](workflowcontrolendpoint.md)|<span data-ttu-id="b8a9f-135">ワークフロー インスタンスの実行の制御 (作成、実行、保留、終了など) に使用する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-135">Defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8a9f-136">親要素</span><span class="sxs-lookup"><span data-stu-id="b8a9f-136">Parent Elements</span></span>  
  
|<span data-ttu-id="b8a9f-137">要素</span><span class="sxs-lookup"><span data-stu-id="b8a9f-137">Element</span></span>|<span data-ttu-id="b8a9f-138">説明</span><span class="sxs-lookup"><span data-stu-id="b8a9f-138">Description</span></span>|  
|-------------|-----------------|  
|\<system.ServiceModel>|<span data-ttu-id="b8a9f-139">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="b8a9f-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8a9f-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8a9f-140">See also</span></span>

- [<span data-ttu-id="b8a9f-141">標準エンドポイント</span><span class="sxs-lookup"><span data-stu-id="b8a9f-141">Standard Endpoints</span></span>](../../../wcf/feature-details/standard-endpoints.md)
