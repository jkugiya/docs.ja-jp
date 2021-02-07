---
description: 詳細については <add> 、 <scopes>
title: <add> の <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: e5582a7599c221e9ac00e03178911290e18ff536
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750235"
---
# <a name="add-of-scopes"></a><span data-ttu-id="a7de6-103">\<add> の \<scopes></span><span class="sxs-lookup"><span data-stu-id="a7de6-103">\<add> of \<scopes></span></span>

<span data-ttu-id="a7de6-104">クエリの実行中に、サービス エンドポイントのフィルター処理に使用できるカスタム スコープ URI を追加します。</span><span class="sxs-lookup"><span data-stu-id="a7de6-104">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="a7de6-105">構文</span><span class="sxs-lookup"><span data-stu-id="a7de6-105">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7de6-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a7de6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a7de6-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7de6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7de6-108">属性</span><span class="sxs-lookup"><span data-stu-id="a7de6-108">Attributes</span></span>  
  
|<span data-ttu-id="a7de6-109">属性</span><span class="sxs-lookup"><span data-stu-id="a7de6-109">Attribute</span></span>|<span data-ttu-id="a7de6-110">説明</span><span class="sxs-lookup"><span data-stu-id="a7de6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7de6-111">scope</span><span class="sxs-lookup"><span data-stu-id="a7de6-111">scope</span></span>|<span data-ttu-id="a7de6-112">サービス検索の一致条件に使用できるエンドポイントのスコープ情報を格納する URI。</span><span class="sxs-lookup"><span data-stu-id="a7de6-112">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7de6-113">子要素</span><span class="sxs-lookup"><span data-stu-id="a7de6-113">Child Elements</span></span>  

 <span data-ttu-id="a7de6-114">なし。</span><span class="sxs-lookup"><span data-stu-id="a7de6-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7de6-115">親要素</span><span class="sxs-lookup"><span data-stu-id="a7de6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a7de6-116">要素</span><span class="sxs-lookup"><span data-stu-id="a7de6-116">Element</span></span>|<span data-ttu-id="a7de6-117">説明</span><span class="sxs-lookup"><span data-stu-id="a7de6-117">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="a7de6-118">クエリの実行中に、サービス エンドポイントのフィルター処理に使用できるカスタム スコープ URI を指定する構成要素のコレクションを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="a7de6-118">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7de6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7de6-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
