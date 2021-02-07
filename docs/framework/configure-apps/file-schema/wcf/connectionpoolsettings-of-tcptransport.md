---
description: 詳細については <connectionPoolSettings> 、 <tcpTransport>
title: <connectionPoolSettings> の <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 065d3529740714ffd740c2cec71832a7b386b4a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698389"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="6ddf3-103">\<connectionPoolSettings> の \<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="6ddf3-103">\<connectionPoolSettings> of \<tcpTransport></span></span>

<span data-ttu-id="6ddf3-104">TCP トランスポートの追加の接続プール設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-104">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="6ddf3-105">構文</span><span class="sxs-lookup"><span data-stu-id="6ddf3-105">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ddf3-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6ddf3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6ddf3-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ddf3-108">属性</span><span class="sxs-lookup"><span data-stu-id="6ddf3-108">Attributes</span></span>  
  
|<span data-ttu-id="6ddf3-109">属性</span><span class="sxs-lookup"><span data-stu-id="6ddf3-109">Attribute</span></span>|<span data-ttu-id="6ddf3-110">説明</span><span class="sxs-lookup"><span data-stu-id="6ddf3-110">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="6ddf3-111">送信チャネルに使用される接続プールの名前を定義する文字列です。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-111">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="6ddf3-112">ストリーム配信モードでは、接続が共有されません。したがって、接続プールは無効です。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-112">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="6ddf3-113">既定は、"default" 文字列です。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-113">The default is a "default" string.</span></span> <span data-ttu-id="6ddf3-114">この値を変更して、特定のクライアントの接続を、個別のグループに分離できます。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-114">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="6ddf3-115">接続が切断されるまでの最大アイドル時間を指定する正の <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-115">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="6ddf3-116">既定値は 00:02:00 です。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="6ddf3-117">アクティブな接続が終了されるまでの時間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-117">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="6ddf3-118">既定値は 00:05:00 です。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-118">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="6ddf3-119">接続は、接続キャッシュに返された後、アクティブに転送中ではないときに終了します。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-119">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="6ddf3-120">TCP トランスポートによって使用される接続キャッシュは、各エンドポイントの必要に応じて、`maxOutboundConnectionsPerEndpoint.` で設定されているキャッシュ制限内で新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-120">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="6ddf3-121">そのサービスによって開始されるリモート エンドポイントへの接続の最大数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="6ddf3-122">制限を超えた接続は、制限内に空きができるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="6ddf3-123">`idleTimeout` は、例外がスローされるまでに接続をキューに入れたままにする期間を制限します。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="6ddf3-124">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="6ddf3-125">この属性は、クライアントから特定のサービス エンドポイントへの接続で、同時にアクティブできる接続数を制限します。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="6ddf3-126">この値よりも多くのアクティブなクライアント接続がある場合、サービスは、クライアントに応答しないように見える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="6ddf3-127">この場合は、この値を調整して、予想される特定のエンドポイントへの同時クライアント接続の最大数より大きくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ddf3-128">子要素</span><span class="sxs-lookup"><span data-stu-id="6ddf3-128">Child Elements</span></span>  

 <span data-ttu-id="6ddf3-129">なし。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ddf3-130">親要素</span><span class="sxs-lookup"><span data-stu-id="6ddf3-130">Parent Elements</span></span>  
  
|<span data-ttu-id="6ddf3-131">要素</span><span class="sxs-lookup"><span data-stu-id="6ddf3-131">Element</span></span>|<span data-ttu-id="6ddf3-132">説明</span><span class="sxs-lookup"><span data-stu-id="6ddf3-132">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="6ddf3-133">チャネルで名前付きパイプを使用してメッセージを転送するトランスポートを定義します。</span><span class="sxs-lookup"><span data-stu-id="6ddf3-133">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ddf3-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ddf3-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6ddf3-135">トランスポート</span><span class="sxs-lookup"><span data-stu-id="6ddf3-135">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="6ddf3-136">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="6ddf3-136">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="6ddf3-137">バインド</span><span class="sxs-lookup"><span data-stu-id="6ddf3-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6ddf3-138">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="6ddf3-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6ddf3-139">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="6ddf3-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
