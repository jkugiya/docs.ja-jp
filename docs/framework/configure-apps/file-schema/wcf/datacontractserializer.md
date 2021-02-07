---
description: '詳細情報: dataContractSerializer'
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 5dee59ba97a1632c142179aee79058dd3ce8c349
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754408"
---
# <a name="datacontractserializer"></a><span data-ttu-id="0ff89-103">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="0ff89-103">dataContractSerializer</span></span>

<span data-ttu-id="0ff89-104"><xref:System.Runtime.Serialization.DataContractSerializer> 用の設定データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0ff89-104">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="0ff89-105">構文</span><span class="sxs-lookup"><span data-stu-id="0ff89-105">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ff89-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0ff89-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0ff89-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0ff89-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ff89-108">属性</span><span class="sxs-lookup"><span data-stu-id="0ff89-108">Attributes</span></span>  
  
|<span data-ttu-id="0ff89-109">要素</span><span class="sxs-lookup"><span data-stu-id="0ff89-109">Element</span></span>|<span data-ttu-id="0ff89-110">説明</span><span class="sxs-lookup"><span data-stu-id="0ff89-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ff89-111">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="0ff89-111">ignoreExtensionDataObject</span></span>|<span data-ttu-id="0ff89-112">エンドポイントがシリアル化または逆シリアル化されているときに、そのエンドポイントにより提供されるデータを無視するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="0ff89-112">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="0ff89-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="0ff89-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="0ff89-114">シリアル化または逆シリアル化する項目の最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="0ff89-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ff89-115">子要素</span><span class="sxs-lookup"><span data-stu-id="0ff89-115">Child Elements</span></span>  

 <span data-ttu-id="0ff89-116">なし。</span><span class="sxs-lookup"><span data-stu-id="0ff89-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ff89-117">親要素</span><span class="sxs-lookup"><span data-stu-id="0ff89-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0ff89-118">要素</span><span class="sxs-lookup"><span data-stu-id="0ff89-118">Element</span></span>|<span data-ttu-id="0ff89-119">説明</span><span class="sxs-lookup"><span data-stu-id="0ff89-119">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0ff89-120">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="0ff89-120">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ff89-121">解説</span><span class="sxs-lookup"><span data-stu-id="0ff89-121">Remarks</span></span>  

 <span data-ttu-id="0ff89-122">既知の型の詳細については、<xref:System.Runtime.Serialization.DataContractSerializer> のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ff89-122">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0ff89-123">`<dataContractSerializer>` 動作要素が存在する場合は、構成ファイル内で `<enableWebScript>` 動作要素よりも前に出現する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ff89-123">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="0ff89-124">それ以外の場合は、動作結果は未定義になります。</span><span class="sxs-lookup"><span data-stu-id="0ff89-124">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff89-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ff89-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="0ff89-126">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="0ff89-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="0ff89-127">データ転送とシリアル化</span><span class="sxs-lookup"><span data-stu-id="0ff89-127">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
