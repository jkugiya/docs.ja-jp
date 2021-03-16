---
description: '詳細情報: <scopes>'
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 2df1101beb5b1bc09c2d98eb89a8200303c5b456
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786864"
---
# \<scopes>

<span data-ttu-id="88777-102">クエリの実行中に、サービス エンドポイントのフィルター処理に使用できるカスタム スコープ URI を指定する構成要素のコレクションを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="88777-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="88777-103">構文</span><span class="sxs-lookup"><span data-stu-id="88777-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88777-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="88777-104">Attributes and Elements</span></span>  

 <span data-ttu-id="88777-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="88777-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88777-106">属性</span><span class="sxs-lookup"><span data-stu-id="88777-106">Attributes</span></span>  

 <span data-ttu-id="88777-107">なし。</span><span class="sxs-lookup"><span data-stu-id="88777-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="88777-108">子要素</span><span class="sxs-lookup"><span data-stu-id="88777-108">Child Elements</span></span>  
  
|<span data-ttu-id="88777-109">属性</span><span class="sxs-lookup"><span data-stu-id="88777-109">Attribute</span></span>|<span data-ttu-id="88777-110">説明</span><span class="sxs-lookup"><span data-stu-id="88777-110">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="88777-111">サービス検索の一致条件に使用できるエンドポイントのスコープ情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="88777-111">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="88777-112">親要素</span><span class="sxs-lookup"><span data-stu-id="88777-112">Parent Elements</span></span>  
  
|<span data-ttu-id="88777-113">要素</span><span class="sxs-lookup"><span data-stu-id="88777-113">Element</span></span>|<span data-ttu-id="88777-114">説明</span><span class="sxs-lookup"><span data-stu-id="88777-114">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="88777-115">エンドポイントのさまざまな探索設定を指定します (探索可能性、スコープ、メタデータに対するカスタム拡張など)。</span><span class="sxs-lookup"><span data-stu-id="88777-115">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88777-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="88777-116">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
