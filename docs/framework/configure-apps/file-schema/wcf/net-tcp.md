---
description: 詳細については、「net.tcp> の <」を参照してください。
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: b7b36e0309139508011e5abceab97cc6f6f9a53d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786942"
---
# \<net.tcp>

<span data-ttu-id="a2192-103">複数のプロセスが同じ TCP ポートを共有できる NET.TCP ポート共有サービスの構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="a2192-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a><span data-ttu-id="a2192-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2192-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="a2192-105">Type</span><span class="sxs-lookup"><span data-stu-id="a2192-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2192-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a2192-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a2192-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2192-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2192-108">属性</span><span class="sxs-lookup"><span data-stu-id="a2192-108">Attributes</span></span>  
  
|<span data-ttu-id="a2192-109">属性</span><span class="sxs-lookup"><span data-stu-id="a2192-109">Attribute</span></span>|<span data-ttu-id="a2192-110">説明</span><span class="sxs-lookup"><span data-stu-id="a2192-110">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="a2192-111">共有接続から受け入れられ、まだ Windows Communication Foundation (WCF) サービスにディスパッチされていない未処理の接続の最大数を指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="a2192-111">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="a2192-112">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="a2192-112">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="a2192-113">整数は、共有サービスの待機エンドポイントで同時に受け入れる未処理のスレッドの最大数を示しています。</span><span class="sxs-lookup"><span data-stu-id="a2192-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="a2192-114">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="a2192-114">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="a2192-115">アプリケーションによる受け入れをリスナーで待機できる最大接続数。</span><span class="sxs-lookup"><span data-stu-id="a2192-115">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="a2192-116">このクォータ値を超過すると、新規の受信接続は受け入れられるのを待機せずに切断されます。</span><span class="sxs-lookup"><span data-stu-id="a2192-116">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="a2192-117">メッセージ セキュリティのような接続機能では、クライアントは複数の接続を開くことがあります。</span><span class="sxs-lookup"><span data-stu-id="a2192-117">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="a2192-118">このクォータ値を設定する場合、サービス管理者はこのような追加の接続も考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2192-118">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="a2192-119">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="a2192-119">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="a2192-120">フレーム データを読み取り、基礎となる接続から接続ディスパッチを実行するタイムアウトを指定する <xref:System.TimeSpan> です。</span><span class="sxs-lookup"><span data-stu-id="a2192-120">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="a2192-121">既定値は "00:00:10" です。</span><span class="sxs-lookup"><span data-stu-id="a2192-121">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="a2192-122">ポート共有サービスが Microsoft Teredo サービスを使用して、WCF サービスの代わりに TCP ポートをリッスンするかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="a2192-122">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="a2192-123">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="a2192-123">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2192-124">子要素</span><span class="sxs-lookup"><span data-stu-id="a2192-124">Child Elements</span></span>  
  
|<span data-ttu-id="a2192-125">要素</span><span class="sxs-lookup"><span data-stu-id="a2192-125">Element</span></span>|<span data-ttu-id="a2192-126">説明</span><span class="sxs-lookup"><span data-stu-id="a2192-126">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="a2192-127">`securityIdentifier`WCF サービスをホストするプロセスのユーザーアカウントを指定する属性を含む構成要素のコレクション。共有サービスへの接続アクセス権が付与されます。</span><span class="sxs-lookup"><span data-stu-id="a2192-127">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2192-128">親要素</span><span class="sxs-lookup"><span data-stu-id="a2192-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a2192-129">要素</span><span class="sxs-lookup"><span data-stu-id="a2192-129">Element</span></span>|<span data-ttu-id="a2192-130">説明</span><span class="sxs-lookup"><span data-stu-id="a2192-130">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="a2192-131">リスナー プロセス SMSvcHost.exe の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a2192-131">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2192-132">解説</span><span class="sxs-lookup"><span data-stu-id="a2192-132">Remarks</span></span>  

 <span data-ttu-id="a2192-133">ポート共有の詳細については、「 [Net.tcp ポート共有](../../../wcf/feature-details/net-tcp-port-sharing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2192-133">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="a2192-134">ポート共有サービスの構成方法については、「 [Net.tcp ポート共有サービスの構成](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2192-134">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2192-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2192-135">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="a2192-136">Net.TCP ポート共有</span><span class="sxs-lookup"><span data-stu-id="a2192-136">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="a2192-137">Net.TCP ポート共有サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="a2192-137">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
