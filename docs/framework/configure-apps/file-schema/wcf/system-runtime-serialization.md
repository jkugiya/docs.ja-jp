---
description: 詳細については、「<の>」を参照してください。
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: cf1d95c8650e4b6979d4f34b0bed1fa395911f2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786630"
---
# \<system.runtime.serialization>

<span data-ttu-id="97b03-103"><xref:System.Runtime.Serialization> 名前空間セクションのルート要素を表し、<xref:System.Runtime.Serialization.DataContractSerializer> のオプションを設定するための要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="97b03-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="97b03-104">構文</span><span class="sxs-lookup"><span data-stu-id="97b03-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97b03-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="97b03-105">Attributes and Elements</span></span>  

 <span data-ttu-id="97b03-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="97b03-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97b03-107">属性</span><span class="sxs-lookup"><span data-stu-id="97b03-107">Attributes</span></span>  

 <span data-ttu-id="97b03-108">なし。</span><span class="sxs-lookup"><span data-stu-id="97b03-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="97b03-109">子要素</span><span class="sxs-lookup"><span data-stu-id="97b03-109">Child Elements</span></span>  
  
|<span data-ttu-id="97b03-110">要素</span><span class="sxs-lookup"><span data-stu-id="97b03-110">Element</span></span>|<span data-ttu-id="97b03-111">説明</span><span class="sxs-lookup"><span data-stu-id="97b03-111">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="97b03-112">逆シリアル化時に使用される既知の型の追加を可能にします。</span><span class="sxs-lookup"><span data-stu-id="97b03-112">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97b03-113">親要素</span><span class="sxs-lookup"><span data-stu-id="97b03-113">Parent Elements</span></span>  
  
|<span data-ttu-id="97b03-114">要素</span><span class="sxs-lookup"><span data-stu-id="97b03-114">Element</span></span>|<span data-ttu-id="97b03-115">説明</span><span class="sxs-lookup"><span data-stu-id="97b03-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97b03-116">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="97b03-116">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="97b03-117">構成の最上位の要素。</span><span class="sxs-lookup"><span data-stu-id="97b03-117">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97b03-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="97b03-118">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="97b03-119">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="97b03-119">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="97b03-120">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="97b03-120">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
