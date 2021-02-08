---
description: '詳細情報: <discoveryClientSettings>'
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: c2fda0dea33ffd6dbca24881eefab2e54e361f92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802295"
---
# \<discoveryClientSettings>

<span data-ttu-id="801ed-102">サービス探索プロセスにクライアントとして参加するためにアプリケーションが必要とする設定を格納します。</span><span class="sxs-lookup"><span data-stu-id="801ed-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="801ed-103">構文</span><span class="sxs-lookup"><span data-stu-id="801ed-103">Syntax</span></span>  
  
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
              <add name="String"
                   namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="801ed-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="801ed-104">Attributes and Elements</span></span>  

 <span data-ttu-id="801ed-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="801ed-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="801ed-106">属性</span><span class="sxs-lookup"><span data-stu-id="801ed-106">Attributes</span></span>  
  
|<span data-ttu-id="801ed-107">属性</span><span class="sxs-lookup"><span data-stu-id="801ed-107">Attribute</span></span>|<span data-ttu-id="801ed-108">説明</span><span class="sxs-lookup"><span data-stu-id="801ed-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="801ed-109">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="801ed-109">discoveryEndpoint</span></span>|<span data-ttu-id="801ed-110">クライアント アプリケーションが実行時に探索可能なサービスを自動的に検索し、そのアドレスを見つけることができる探索エンドポイントの名前を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="801ed-110">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="801ed-111">子要素</span><span class="sxs-lookup"><span data-stu-id="801ed-111">Child Elements</span></span>  
  
|<span data-ttu-id="801ed-112">要素</span><span class="sxs-lookup"><span data-stu-id="801ed-112">Element</span></span>|<span data-ttu-id="801ed-113">説明</span><span class="sxs-lookup"><span data-stu-id="801ed-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="801ed-114">探索サービスの検索にクライアント アプリケーションによって使用される基準を提供する構成要素。</span><span class="sxs-lookup"><span data-stu-id="801ed-114">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="801ed-115">基準は、(探しているサービスを指定する) 検索条件と (検索をどのくらい続けるかを指定する) 検索終了条件にグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="801ed-115">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="801ed-116">親要素</span><span class="sxs-lookup"><span data-stu-id="801ed-116">Parent Elements</span></span>  
  
|<span data-ttu-id="801ed-117">要素</span><span class="sxs-lookup"><span data-stu-id="801ed-117">Element</span></span>|<span data-ttu-id="801ed-118">説明</span><span class="sxs-lookup"><span data-stu-id="801ed-118">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="801ed-119">アプリケーションが実行時に動的にエンドポイント アドレスを検索するクライアント プログラムとして機能するための情報を格納する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="801ed-119">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="801ed-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="801ed-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
