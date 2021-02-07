---
description: '詳細情報: <mexNamedPipeBinding>'
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: a7d1c6b10ed436d5ec1b20092d042d6b0a80bd34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684322"
---
# \<mexNamedPipeBinding>

<span data-ttu-id="784a9-102">名前付きパイプを経由する WS-MetadataExchange (WS-MEX) メッセージ交換に使用されるバインディングの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="784a9-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="784a9-103">構文</span><span class="sxs-lookup"><span data-stu-id="784a9-103">Syntax</span></span>  
  
```xml  
<mexNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="784a9-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="784a9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="784a9-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="784a9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="784a9-106">属性</span><span class="sxs-lookup"><span data-stu-id="784a9-106">Attributes</span></span>  
  
|<span data-ttu-id="784a9-107">属性</span><span class="sxs-lookup"><span data-stu-id="784a9-107">Attribute</span></span>|<span data-ttu-id="784a9-108">説明</span><span class="sxs-lookup"><span data-stu-id="784a9-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="784a9-109">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="784a9-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="784a9-110">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="784a9-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="784a9-111">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="784a9-111">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="784a9-112">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="784a9-112">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="784a9-113">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="784a9-113">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="784a9-114">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="784a9-114">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="784a9-115">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="784a9-115">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="784a9-116">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="784a9-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="784a9-117">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="784a9-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="784a9-118">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="784a9-118">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="784a9-119">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="784a9-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="784a9-120">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="784a9-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="784a9-121">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="784a9-121">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="784a9-122">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="784a9-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="784a9-123">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="784a9-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="784a9-124">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="784a9-124">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="784a9-125">子要素</span><span class="sxs-lookup"><span data-stu-id="784a9-125">Child Elements</span></span>  

 <span data-ttu-id="784a9-126">なし。</span><span class="sxs-lookup"><span data-stu-id="784a9-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="784a9-127">親要素</span><span class="sxs-lookup"><span data-stu-id="784a9-127">Parent Elements</span></span>  
  
|<span data-ttu-id="784a9-128">要素</span><span class="sxs-lookup"><span data-stu-id="784a9-128">Element</span></span>|<span data-ttu-id="784a9-129">説明</span><span class="sxs-lookup"><span data-stu-id="784a9-129">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="784a9-130">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="784a9-130">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="784a9-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="784a9-131">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="784a9-132">方法: 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="784a9-132">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="784a9-133">カスタム バインディングを介したメタデータの公開と取得</span><span class="sxs-lookup"><span data-stu-id="784a9-133">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="784a9-134">Metadata</span><span class="sxs-lookup"><span data-stu-id="784a9-134">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="784a9-135">バインド</span><span class="sxs-lookup"><span data-stu-id="784a9-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="784a9-136">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="784a9-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="784a9-137">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="784a9-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
