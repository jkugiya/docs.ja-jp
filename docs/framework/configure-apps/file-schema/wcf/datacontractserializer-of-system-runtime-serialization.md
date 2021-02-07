---
description: 詳細については <dataContractSerializer> 、「<の>」を参照してください。
title: <dataContractSerializer> <の> の。
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 3755005782ea773344326d211b9f8f115a97f2ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754421"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="eb52b-103">\<dataContractSerializer> の \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="eb52b-103">\<dataContractSerializer> of \<system.runtime.serialization></span></span>

<span data-ttu-id="eb52b-104"><xref:System.Runtime.Serialization.DataContractSerializer> 用の設定データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="eb52b-104">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="eb52b-105">構文</span><span class="sxs-lookup"><span data-stu-id="eb52b-105">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb52b-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="eb52b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="eb52b-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb52b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb52b-108">属性</span><span class="sxs-lookup"><span data-stu-id="eb52b-108">Attributes</span></span>  
  
|<span data-ttu-id="eb52b-109">要素</span><span class="sxs-lookup"><span data-stu-id="eb52b-109">Element</span></span>|<span data-ttu-id="eb52b-110">説明</span><span class="sxs-lookup"><span data-stu-id="eb52b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb52b-111">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="eb52b-111">ignoreExtensionDataObject</span></span>|<span data-ttu-id="eb52b-112">エンドポイントがシリアル化または逆シリアル化されているときに、そのエンドポイントにより提供されるデータを無視するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="eb52b-112">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="eb52b-113">この属性は、`<dataContractSerializer>` 要素の下の `<behavior>` でのみ設定可能です。</span><span class="sxs-lookup"><span data-stu-id="eb52b-113">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="eb52b-114">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="eb52b-114">maxItemsInObjectGraph</span></span>|<span data-ttu-id="eb52b-115">シリアル化または逆シリアル化する項目の最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="eb52b-115">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="eb52b-116">この属性は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="eb52b-116">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb52b-117">子要素</span><span class="sxs-lookup"><span data-stu-id="eb52b-117">Child Elements</span></span>  
  
|<span data-ttu-id="eb52b-118">要素</span><span class="sxs-lookup"><span data-stu-id="eb52b-118">Element</span></span>|<span data-ttu-id="eb52b-119">説明</span><span class="sxs-lookup"><span data-stu-id="eb52b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="eb52b-120">逆シリアル化時に <xref:System.Runtime.Serialization.DataContractSerializer> が使用する既知の型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="eb52b-120">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="eb52b-121">データコントラクトと既知の型の詳細については、「 [データコントラクトの既知の型](../../../wcf/feature-details/data-contract-known-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb52b-121">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb52b-122">親要素</span><span class="sxs-lookup"><span data-stu-id="eb52b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="eb52b-123">要素</span><span class="sxs-lookup"><span data-stu-id="eb52b-123">Element</span></span>|<span data-ttu-id="eb52b-124">説明</span><span class="sxs-lookup"><span data-stu-id="eb52b-124">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="eb52b-125"><xref:System.Runtime.Serialization> 名前空間セクションのルート要素を表し、<xref:System.Runtime.Serialization.DataContractSerializer> のオプションを設定するための要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="eb52b-125">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb52b-126">解説</span><span class="sxs-lookup"><span data-stu-id="eb52b-126">Remarks</span></span>  

 <span data-ttu-id="eb52b-127">既知の型の詳細については、「」 <xref:System.Runtime.Serialization.DataContractSerializer> および「 [データコントラクトの既知の型](../../../wcf/feature-details/data-contract-known-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb52b-127">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb52b-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb52b-128">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="eb52b-129">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="eb52b-129">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
