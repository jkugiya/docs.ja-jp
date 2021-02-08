---
description: 詳細については <add> 、 <contractTypeNames>
title: <add> の <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 0708aa277b4250cb4134a98ddf7af661840981a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803998"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="969c9-103">\<add> の \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="969c9-103">\<add> of \<contractTypeNames></span></span>

<span data-ttu-id="969c9-104">検索対象サービスのコントラクト名と、サービスを検索するときに一般的に使用される条件を指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="969c9-104">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="969c9-105">複数のコントラクト名が指定されると、すべてのコントラクトに一致するサービス エンドポイントのみが適用されます。</span><span class="sxs-lookup"><span data-stu-id="969c9-105">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="969c9-106">Windows Communication Foundation (WCF) では、エンドポイントでサポートされるコントラクトは1つだけであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="969c9-106">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="969c9-107">構文</span><span class="sxs-lookup"><span data-stu-id="969c9-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="969c9-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="969c9-108">Attributes and Elements</span></span>  

 <span data-ttu-id="969c9-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="969c9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="969c9-110">属性</span><span class="sxs-lookup"><span data-stu-id="969c9-110">Attributes</span></span>  
  
|<span data-ttu-id="969c9-111">属性</span><span class="sxs-lookup"><span data-stu-id="969c9-111">Attribute</span></span>|<span data-ttu-id="969c9-112">説明</span><span class="sxs-lookup"><span data-stu-id="969c9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="969c9-113">name</span><span class="sxs-lookup"><span data-stu-id="969c9-113">name</span></span>|<span data-ttu-id="969c9-114">コントラクト型の名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="969c9-114">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="969c9-115">namespace</span><span class="sxs-lookup"><span data-stu-id="969c9-115">namespace</span></span>|<span data-ttu-id="969c9-116">コントラクト型の名前空間を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="969c9-116">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="969c9-117">子要素</span><span class="sxs-lookup"><span data-stu-id="969c9-117">Child Elements</span></span>  

 <span data-ttu-id="969c9-118">なし</span><span class="sxs-lookup"><span data-stu-id="969c9-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="969c9-119">親要素</span><span class="sxs-lookup"><span data-stu-id="969c9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="969c9-120">要素</span><span class="sxs-lookup"><span data-stu-id="969c9-120">Element</span></span>|<span data-ttu-id="969c9-121">説明</span><span class="sxs-lookup"><span data-stu-id="969c9-121">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="969c9-122">コントラクトの型名のコレクション。</span><span class="sxs-lookup"><span data-stu-id="969c9-122">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="969c9-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="969c9-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
