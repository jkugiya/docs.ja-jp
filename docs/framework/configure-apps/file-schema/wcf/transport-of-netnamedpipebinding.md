---
description: 詳細については <transport> 、 <netNamedPipeBinding>
title: <transport> の <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: a54c429bcac192ddc46df7232c33ab98bd1a4c58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773486"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="0922e-103">\<transport> の \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="0922e-103">\<transport> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="0922e-104">名前付きパイプのトランスポート セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="0922e-104">Defines the transport security settings for a named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="0922e-105">構文</span><span class="sxs-lookup"><span data-stu-id="0922e-105">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0922e-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0922e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0922e-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0922e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0922e-108">属性</span><span class="sxs-lookup"><span data-stu-id="0922e-108">Attributes</span></span>  
  
|<span data-ttu-id="0922e-109">属性</span><span class="sxs-lookup"><span data-stu-id="0922e-109">Attribute</span></span>|<span data-ttu-id="0922e-110">説明</span><span class="sxs-lookup"><span data-stu-id="0922e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0922e-111">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="0922e-111">protectionLevel</span></span>|<span data-ttu-id="0922e-112">名前付きパイプの保護レベルを定義します。</span><span class="sxs-lookup"><span data-stu-id="0922e-112">Defines protection level of the named pipe.</span></span> <span data-ttu-id="0922e-113">メッセージに署名を付けることで、メッセージの転送中に第三者によって改ざんされるリスクが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="0922e-113">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="0922e-114">暗号化によって、トランスポート中にデータ レベルのプライバシーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="0922e-114">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="0922e-115">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0922e-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0922e-116">-None: 保護がありません。</span><span class="sxs-lookup"><span data-stu-id="0922e-116">-   None: No protection.</span></span><br /><span data-ttu-id="0922e-117">-Sign: メッセージは署名されています。</span><span class="sxs-lookup"><span data-stu-id="0922e-117">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="0922e-118">-EncryptAndSign: メッセージは暗号化され、署名されます。</span><span class="sxs-lookup"><span data-stu-id="0922e-118">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="0922e-119">既定値は EncryptAndSign です。</span><span class="sxs-lookup"><span data-stu-id="0922e-119">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0922e-120">子要素</span><span class="sxs-lookup"><span data-stu-id="0922e-120">Child Elements</span></span>  

 <span data-ttu-id="0922e-121">なし</span><span class="sxs-lookup"><span data-stu-id="0922e-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0922e-122">親要素</span><span class="sxs-lookup"><span data-stu-id="0922e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0922e-123">要素</span><span class="sxs-lookup"><span data-stu-id="0922e-123">Element</span></span>|<span data-ttu-id="0922e-124">説明</span><span class="sxs-lookup"><span data-stu-id="0922e-124">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="0922e-125">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="0922e-125">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0922e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="0922e-126">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="0922e-127">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="0922e-127">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0922e-128">バインド</span><span class="sxs-lookup"><span data-stu-id="0922e-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0922e-129">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="0922e-129">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0922e-130">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="0922e-130">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
