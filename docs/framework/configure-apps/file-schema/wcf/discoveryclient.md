---
description: '詳細情報: <discoveryClient>'
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: d04eee828bb16e56a65c39059665feb745f3006a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754395"
---
# \<discoveryClient>

<span data-ttu-id="4c700-102">クライアント アプリケーションが実行時に探索可能なサービスを自動的に検索し、そのアドレスを見つけることができるカスタム バインドを作成するための構成要素。</span><span class="sxs-lookup"><span data-stu-id="4c700-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="4c700-103">構文</span><span class="sxs-lookup"><span data-stu-id="4c700-103">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c700-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4c700-104">Attributes and Elements</span></span>  

 <span data-ttu-id="4c700-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c700-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c700-106">属性</span><span class="sxs-lookup"><span data-stu-id="4c700-106">Attributes</span></span>  
  
|<span data-ttu-id="4c700-107">属性</span><span class="sxs-lookup"><span data-stu-id="4c700-107">Attribute</span></span>|<span data-ttu-id="4c700-108">説明</span><span class="sxs-lookup"><span data-stu-id="4c700-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c700-109">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="4c700-109">discoveryEndpoint</span></span>|<span data-ttu-id="4c700-110">クライアント アプリケーションが実行時に探索可能なサービスを自動的に検索し、そのアドレスを見つけることができる探索エンドポイントの名前を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="4c700-110">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c700-111">子要素</span><span class="sxs-lookup"><span data-stu-id="4c700-111">Child Elements</span></span>  
  
|<span data-ttu-id="4c700-112">要素</span><span class="sxs-lookup"><span data-stu-id="4c700-112">Element</span></span>|<span data-ttu-id="4c700-113">説明</span><span class="sxs-lookup"><span data-stu-id="4c700-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="4c700-114">探索サービスの検索にクライアント アプリケーションによって使用される基準を提供する構成要素。</span><span class="sxs-lookup"><span data-stu-id="4c700-114">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="4c700-115">基準は、(探しているサービスを指定する) 検索条件と (検索をどのくらい続けるかを指定する) 検索終了条件にグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="4c700-115">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c700-116">親要素</span><span class="sxs-lookup"><span data-stu-id="4c700-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4c700-117">要素</span><span class="sxs-lookup"><span data-stu-id="4c700-117">Element</span></span>|<span data-ttu-id="4c700-118">説明</span><span class="sxs-lookup"><span data-stu-id="4c700-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="4c700-119">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="4c700-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c700-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c700-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
