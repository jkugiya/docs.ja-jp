---
description: '詳細情報: <findCriteria>'
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 6415dfd4614122ac361fd7d5b872f840b01734f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767948"
---
# \<findCriteria>

<span data-ttu-id="c8338-102">探索サービスの検索にクライアント アプリケーションによって使用される基準を提供する構成要素。</span><span class="sxs-lookup"><span data-stu-id="c8338-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="c8338-103">基準は、(探しているサービスを指定する) 検索条件と (検索をどのくらい続けるかを指定する) 検索終了条件にグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="c8338-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**  
  
## <a name="syntax"></a><span data-ttu-id="c8338-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8338-104">Syntax</span></span>  
  
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
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8338-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c8338-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c8338-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8338-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8338-107">属性</span><span class="sxs-lookup"><span data-stu-id="c8338-107">Attributes</span></span>  
  
|<span data-ttu-id="c8338-108">属性</span><span class="sxs-lookup"><span data-stu-id="c8338-108">Attribute</span></span>|<span data-ttu-id="c8338-109">説明</span><span class="sxs-lookup"><span data-stu-id="c8338-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8338-110">duration</span><span class="sxs-lookup"><span data-stu-id="c8338-110">duration</span></span>|<span data-ttu-id="c8338-111">ネットワーク上でサービスからの応答を待機する最長時間を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="c8338-111">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="c8338-112">既定の時間は 20 秒です。</span><span class="sxs-lookup"><span data-stu-id="c8338-112">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="c8338-113">maxResults</span><span class="sxs-lookup"><span data-stu-id="c8338-113">maxResults</span></span>|<span data-ttu-id="c8338-114">ネットワークまたはインターネット上で待機する、サービスから応答の最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="c8338-114">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="c8338-115">`duration` 属性に指定した時間が経過する前に応答の最大数に達した場合、検索操作は終了します。</span><span class="sxs-lookup"><span data-stu-id="c8338-115">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="c8338-116">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="c8338-116">scopeMatchBy</span></span>|<span data-ttu-id="c8338-117">Probe メッセージのスコープをエンドポイントのスコープと一致させるときに使用する、一致のアルゴリズムを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="c8338-117">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="c8338-118">サポートされているスコープ一致規則は 5 つあります。</span><span class="sxs-lookup"><span data-stu-id="c8338-118">There are five supported scope-matching rules.</span></span> <span data-ttu-id="c8338-119">スコープ一致規則を指定しなかった場合は、`ScopeMatchByPrefix` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c8338-119">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="c8338-120">詳細については、「<xref:System.ServiceModel.Discovery.FindCriteria>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8338-120">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8338-121">子要素</span><span class="sxs-lookup"><span data-stu-id="c8338-121">Child Elements</span></span>  
  
|<span data-ttu-id="c8338-122">要素</span><span class="sxs-lookup"><span data-stu-id="c8338-122">Element</span></span>|<span data-ttu-id="c8338-123">説明</span><span class="sxs-lookup"><span data-stu-id="c8338-123">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="c8338-124">ワークフローサービスコントラクト型の名前を含む構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="c8338-124">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="c8338-125">\<extensions> の \<findCriteria></span><span class="sxs-lookup"><span data-stu-id="c8338-125">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="c8338-126">拡張を提供する XML 要素オブジェクトのコレクション。</span><span class="sxs-lookup"><span data-stu-id="c8338-126">A collection of XML element objects that provide extensions.</span></span>|  
|[\<scopes>](scopes.md)|<span data-ttu-id="c8338-127">特定のサービスを特定する検索操作の実行中に使用される絶対 URI を格納するオブジェクトのコレクション。</span><span class="sxs-lookup"><span data-stu-id="c8338-127">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="c8338-128">特定のサービスが見つかった場合、サービス URI とスコープ URI が一致します。複雑な一致を処理するスコープ規則が使用されることもあります。</span><span class="sxs-lookup"><span data-stu-id="c8338-128">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c8338-129">親要素</span><span class="sxs-lookup"><span data-stu-id="c8338-129">Parent Elements</span></span>  
  
|<span data-ttu-id="c8338-130">要素</span><span class="sxs-lookup"><span data-stu-id="c8338-130">Element</span></span>|<span data-ttu-id="c8338-131">説明</span><span class="sxs-lookup"><span data-stu-id="c8338-131">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="c8338-132">サービス探索プロセスにクライアントとして参加するためにアプリケーションが必要とする設定を格納します。</span><span class="sxs-lookup"><span data-stu-id="c8338-132">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8338-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8338-133">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
