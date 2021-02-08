---
description: '詳細情報: <compositeDuplex>'
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 0a9ec47027618a5f4fb30b627ccb9ad04c547f48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782183"
---
# \<compositeDuplex>

<span data-ttu-id="d4627-102">サービスがメッセージをクライアントに返送するためのエンドポイントをクライアントが公開する必要がある場合に使用される、バインド要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="d4627-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="d4627-103">構文</span><span class="sxs-lookup"><span data-stu-id="d4627-103">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4627-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d4627-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d4627-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4627-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4627-106">属性</span><span class="sxs-lookup"><span data-stu-id="d4627-106">Attributes</span></span>  
  
|<span data-ttu-id="d4627-107">属性</span><span class="sxs-lookup"><span data-stu-id="d4627-107">Attribute</span></span>|<span data-ttu-id="d4627-108">説明</span><span class="sxs-lookup"><span data-stu-id="d4627-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4627-109">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="d4627-109">clientBaseAddress</span></span>|<span data-ttu-id="d4627-110">二重モードのバック チャネルのアドレスを設定する URI。</span><span class="sxs-lookup"><span data-stu-id="d4627-110">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="d4627-111">サービスは、このアドレスを使用して、クライアントへのアクセス、接続の確立を行います。</span><span class="sxs-lookup"><span data-stu-id="d4627-111">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="d4627-112">この属性が設定されていない場合、既定のアドレス " `full qualified name+default port\TemporaryIndigoAddress\guid` " が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d4627-112">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="d4627-113">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="d4627-113">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4627-114">子要素</span><span class="sxs-lookup"><span data-stu-id="d4627-114">Child Elements</span></span>  

 <span data-ttu-id="d4627-115">なし</span><span class="sxs-lookup"><span data-stu-id="d4627-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4627-116">親要素</span><span class="sxs-lookup"><span data-stu-id="d4627-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d4627-117">要素</span><span class="sxs-lookup"><span data-stu-id="d4627-117">Element</span></span>|<span data-ttu-id="d4627-118">説明</span><span class="sxs-lookup"><span data-stu-id="d4627-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d4627-119">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="d4627-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4627-120">解説</span><span class="sxs-lookup"><span data-stu-id="d4627-120">Remarks</span></span>  

 <span data-ttu-id="d4627-121">たとえば HTTP のように、この構成要素はネイティブでの二重通信を許可しないトランスポートで使用されます。</span><span class="sxs-lookup"><span data-stu-id="d4627-121">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="d4627-122">これとは対照的に、TCP では、二重通信がネイティブで許可されているので、クライアントにメッセージを返信するためにこのバインディング要素をサービスで使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d4627-122">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="d4627-123">クライアントは、サービスのアドレスを公開して、アクセスおよび接続の確立ができるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4627-123">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="d4627-124">このクライアント アドレスは、`clientBaseAddress` 属性によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="d4627-124">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="d4627-125">ClientBaseAddress がユーザーによって明示的に設定されていない場合は、WCF (Windows Communication Foundation) によって自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="d4627-125">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4627-126">例</span><span class="sxs-lookup"><span data-stu-id="d4627-126">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="d4627-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4627-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d4627-128">バインド</span><span class="sxs-lookup"><span data-stu-id="d4627-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d4627-129">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="d4627-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d4627-130">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="d4627-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
