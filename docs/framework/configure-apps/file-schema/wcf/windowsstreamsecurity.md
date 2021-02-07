---
description: '詳細情報: <windowsStreamSecurity>'
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: c623dc23ca67d0341b66a2a4d97de564be77dcc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682398"
---
# \<windowsStreamSecurity>

<span data-ttu-id="3c912-102">カスタム バインディングの Windows ストリーム セキュリティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c912-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="3c912-103">構文</span><span class="sxs-lookup"><span data-stu-id="3c912-103">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c912-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3c912-104">Attributes and Elements</span></span>  

 <span data-ttu-id="3c912-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c912-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c912-106">属性</span><span class="sxs-lookup"><span data-stu-id="3c912-106">Attributes</span></span>  
  
|<span data-ttu-id="3c912-107">属性</span><span class="sxs-lookup"><span data-stu-id="3c912-107">Attribute</span></span>|<span data-ttu-id="3c912-108">説明</span><span class="sxs-lookup"><span data-stu-id="3c912-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c912-109">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="3c912-109">protectionLevel</span></span>|<span data-ttu-id="3c912-110">メッセージ レベルのセキュリティを定義します。</span><span class="sxs-lookup"><span data-stu-id="3c912-110">Defines message-level security.</span></span> <span data-ttu-id="3c912-111">メッセージに署名を付けることで、メッセージの転送中に第三者によって改ざんされるリスクが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="3c912-111">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="3c912-112">暗号化によって、トランスポート中にデータ レベルのプライバシーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="3c912-112">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="3c912-113">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3c912-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3c912-114">-None: 保護がありません。</span><span class="sxs-lookup"><span data-stu-id="3c912-114">-   None: No protection.</span></span><br /><span data-ttu-id="3c912-115">-Sign: メッセージは署名されています。</span><span class="sxs-lookup"><span data-stu-id="3c912-115">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="3c912-116">-EncryptAndSign: メッセージは署名され、暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="3c912-116">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="3c912-117">既定値は EncryptAndSign です。</span><span class="sxs-lookup"><span data-stu-id="3c912-117">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="3c912-118">この属性は <xref:System.Net.Security.ProtectionLevel> 型です。</span><span class="sxs-lookup"><span data-stu-id="3c912-118">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c912-119">子要素</span><span class="sxs-lookup"><span data-stu-id="3c912-119">Child Elements</span></span>  

 <span data-ttu-id="3c912-120">なし</span><span class="sxs-lookup"><span data-stu-id="3c912-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c912-121">親要素</span><span class="sxs-lookup"><span data-stu-id="3c912-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3c912-122">要素</span><span class="sxs-lookup"><span data-stu-id="3c912-122">Element</span></span>|<span data-ttu-id="3c912-123">説明</span><span class="sxs-lookup"><span data-stu-id="3c912-123">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="3c912-124">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="3c912-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c912-125">解説</span><span class="sxs-lookup"><span data-stu-id="3c912-125">Remarks</span></span>  

 <span data-ttu-id="3c912-126">TCP などのストリーム指向プロトコルおよび名前付きパイプを使用するトランスポートは、ストリーム ベースのトランスポート アップグレードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="3c912-126">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="3c912-127">特に、WCF にはセキュリティ アップグレードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3c912-127">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="3c912-128">このトランスポートセキュリティの構成は、この構成要素およびによってカプセル化され、これを [\<sslStreamSecurity>](sslstreamsecurity.md) 構成してカスタムバインドに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="3c912-128">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c912-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c912-129">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="3c912-130">バインド</span><span class="sxs-lookup"><span data-stu-id="3c912-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3c912-131">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="3c912-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3c912-132">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="3c912-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
