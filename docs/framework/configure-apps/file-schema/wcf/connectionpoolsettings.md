---
description: '詳細情報: <connectionPoolSettings>'
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 5acf2d800f1a18f45750d0fabd23516f987b2c5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782170"
---
# \<connectionPoolSettings>

<span data-ttu-id="1b6f3-102">名前付きパイプ バインディングの追加の接続プール設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="1b6f3-103">構文</span><span class="sxs-lookup"><span data-stu-id="1b6f3-103">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b6f3-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1b6f3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="1b6f3-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b6f3-106">属性</span><span class="sxs-lookup"><span data-stu-id="1b6f3-106">Attributes</span></span>  
  
|<span data-ttu-id="1b6f3-107">属性</span><span class="sxs-lookup"><span data-stu-id="1b6f3-107">Attribute</span></span>|<span data-ttu-id="1b6f3-108">説明</span><span class="sxs-lookup"><span data-stu-id="1b6f3-108">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="1b6f3-109">送信チャネルに使用される接続プールの名前を定義する文字列です。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-109">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="1b6f3-110">ストリーム配信モードでは、接続が共有されません。したがって、接続プールは無効です。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-110">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="1b6f3-111">既定は、"default" 文字列です。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-111">The default is a "default" string.</span></span> <span data-ttu-id="1b6f3-112">この値を変更して、特定のクライアントの接続を、個別のグループに分離できます。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-112">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="1b6f3-113">接続が切断されるまでの最大アイドル時間を指定する正の <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-113">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="1b6f3-114">既定値は 00:02:00 です。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-114">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="1b6f3-115">そのサービスによって開始されるリモート エンドポイントへの接続の最大数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-115">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="1b6f3-116">制限を超えた接続は、制限内に空きができるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-116">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="1b6f3-117">`idleTimeout` は、例外がスローされるまでに接続をキューに入れたままにする期間を制限します。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-117">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="1b6f3-118">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-118">The default is 10.</span></span><br /><br /> <span data-ttu-id="1b6f3-119">この属性は、クライアントから特定のサービス エンドポイントへの接続で、同時にアクティブできる接続数を制限します。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-119">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="1b6f3-120">この値よりも多くのアクティブなクライアント接続がある場合、サービスは、クライアントに応答しないように見える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-120">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="1b6f3-121">この場合は、この値を調整して、予想される特定のエンドポイントへの同時クライアント接続の最大数より大きくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-121">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b6f3-122">子要素</span><span class="sxs-lookup"><span data-stu-id="1b6f3-122">Child Elements</span></span>  

 <span data-ttu-id="1b6f3-123">なし。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b6f3-124">親要素</span><span class="sxs-lookup"><span data-stu-id="1b6f3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1b6f3-125">要素</span><span class="sxs-lookup"><span data-stu-id="1b6f3-125">Element</span></span>|<span data-ttu-id="1b6f3-126">説明</span><span class="sxs-lookup"><span data-stu-id="1b6f3-126">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="1b6f3-127">チャネルで名前付きパイプを使用してメッセージを転送するトランスポートを定義します。</span><span class="sxs-lookup"><span data-stu-id="1b6f3-127">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b6f3-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b6f3-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1b6f3-129">トランスポート</span><span class="sxs-lookup"><span data-stu-id="1b6f3-129">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="1b6f3-130">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="1b6f3-130">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="1b6f3-131">バインド</span><span class="sxs-lookup"><span data-stu-id="1b6f3-131">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1b6f3-132">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="1b6f3-132">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1b6f3-133">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="1b6f3-133">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
