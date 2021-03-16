---
description: '詳細情報: <policyImporter>'
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 2103c424aef081b72fa822ed207537195b8fdea9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683516"
---
# \<policyImporter>

<span data-ttu-id="51d30-102">バインディングに関するカスタム ポリシー アサーションのインポートを制御するポリシー インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="51d30-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="51d30-103">構文</span><span class="sxs-lookup"><span data-stu-id="51d30-103">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51d30-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="51d30-104">Attributes and Elements</span></span>  

 <span data-ttu-id="51d30-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="51d30-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51d30-106">属性</span><span class="sxs-lookup"><span data-stu-id="51d30-106">Attributes</span></span>  
  
|<span data-ttu-id="51d30-107">属性</span><span class="sxs-lookup"><span data-stu-id="51d30-107">Attribute</span></span>|<span data-ttu-id="51d30-108">説明</span><span class="sxs-lookup"><span data-stu-id="51d30-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="51d30-109">この要素の型です。</span><span class="sxs-lookup"><span data-stu-id="51d30-109">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51d30-110">子要素</span><span class="sxs-lookup"><span data-stu-id="51d30-110">Child Elements</span></span>  

 <span data-ttu-id="51d30-111">なし</span><span class="sxs-lookup"><span data-stu-id="51d30-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51d30-112">親要素</span><span class="sxs-lookup"><span data-stu-id="51d30-112">Parent Elements</span></span>  
  
|<span data-ttu-id="51d30-113">要素</span><span class="sxs-lookup"><span data-stu-id="51d30-113">Element</span></span>|<span data-ttu-id="51d30-114">説明</span><span class="sxs-lookup"><span data-stu-id="51d30-114">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="51d30-115">バインディングに関するカスタム ポリシー アサーションのインポートを制御するすべてのポリシー インポーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="51d30-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51d30-116">解説</span><span class="sxs-lookup"><span data-stu-id="51d30-116">Remarks</span></span>  

 <span data-ttu-id="51d30-117">ポリシー インポーターは、バインディング機能についてのカスタム ポリシー アサーションの検索、およびアサーションで必要となる機能を実装するカスタム バインド要素の結び付けに使用されます。</span><span class="sxs-lookup"><span data-stu-id="51d30-117">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d30-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="51d30-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="51d30-119">WCF クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="51d30-119">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="51d30-120">クライアント</span><span class="sxs-lookup"><span data-stu-id="51d30-120">Clients</span></span>](../../../wcf/feature-details/clients.md)
