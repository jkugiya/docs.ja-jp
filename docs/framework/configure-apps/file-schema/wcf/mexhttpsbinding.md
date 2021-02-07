---
description: '詳細情報: <mexHttpsBinding>'
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 1e6eb66e1379cb8f351e34d4fd406dd3cc1f9a4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684335"
---
# \<mexHttpsBinding>

<span data-ttu-id="1a08f-102">HTTPS 経由の WS-MetadataExchange (WS-MEX) メッセージ交換に使用されるバインディングの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="1a08f-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="1a08f-103">構文</span><span class="sxs-lookup"><span data-stu-id="1a08f-103">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a08f-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1a08f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="1a08f-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a08f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a08f-106">属性</span><span class="sxs-lookup"><span data-stu-id="1a08f-106">Attributes</span></span>  
  
|<span data-ttu-id="1a08f-107">属性</span><span class="sxs-lookup"><span data-stu-id="1a08f-107">Attribute</span></span>|<span data-ttu-id="1a08f-108">説明</span><span class="sxs-lookup"><span data-stu-id="1a08f-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="1a08f-109">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="1a08f-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1a08f-110">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a08f-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1a08f-111">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="1a08f-111">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="1a08f-112">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="1a08f-112">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1a08f-113">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a08f-113">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1a08f-114">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1a08f-114">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1a08f-115">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a08f-115">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1a08f-116">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="1a08f-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1a08f-117">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a08f-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1a08f-118">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="1a08f-118">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1a08f-119">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="1a08f-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1a08f-120">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a08f-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1a08f-121">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="1a08f-121">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1a08f-122">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="1a08f-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1a08f-123">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a08f-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1a08f-124">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="1a08f-124">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a08f-125">子要素</span><span class="sxs-lookup"><span data-stu-id="1a08f-125">Child Elements</span></span>  

 <span data-ttu-id="1a08f-126">なし。</span><span class="sxs-lookup"><span data-stu-id="1a08f-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a08f-127">親要素</span><span class="sxs-lookup"><span data-stu-id="1a08f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1a08f-128">要素</span><span class="sxs-lookup"><span data-stu-id="1a08f-128">Element</span></span>|<span data-ttu-id="1a08f-129">説明</span><span class="sxs-lookup"><span data-stu-id="1a08f-129">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="1a08f-130">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="1a08f-130">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a08f-131">解説</span><span class="sxs-lookup"><span data-stu-id="1a08f-131">Remarks</span></span>  

 <span data-ttu-id="1a08f-132">このバインディングは、基本的には証明書を使用してトランスポート レベルのセキュリティをサポートする `WSHttpBinding` バインディングです。</span><span class="sxs-lookup"><span data-stu-id="1a08f-132">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="1a08f-133">このようなメタデータエンドポイントの構成と使用の詳細については、「 [方法: カスタム WS-Metadata 交換バインディングを構成](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)する」、「 [方法: MEX 以外のバインディングを使用してメタデータを取得する](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)」、および「 [カスタムのセキュリティで保護されたメタデータエンドポイント](../../../wcf/samples/custom-secure-metadata-endpoint.md)のサンプル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a08f-133">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a08f-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a08f-134">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="1a08f-135">方法: 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="1a08f-135">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="1a08f-136">カスタム バインディングを介したメタデータの公開と取得</span><span class="sxs-lookup"><span data-stu-id="1a08f-136">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="1a08f-137">方法: カスタム WS-Metadata Exchange バインディングを構成する</span><span class="sxs-lookup"><span data-stu-id="1a08f-137">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="1a08f-138">方法: MEX 以外のバインディングを介してメタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="1a08f-138">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="1a08f-139">カスタム セキュア メタデータ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="1a08f-139">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="1a08f-140">Metadata</span><span class="sxs-lookup"><span data-stu-id="1a08f-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="1a08f-141">バインド</span><span class="sxs-lookup"><span data-stu-id="1a08f-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1a08f-142">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="1a08f-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1a08f-143">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="1a08f-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
