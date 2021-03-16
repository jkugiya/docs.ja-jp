---
description: '詳細情報: <dynamicEndpoint>'
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 0fe30492e1daeecca5e27aef844f5f6977396049
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725897"
---
# \<dynamicEndpoint>

<span data-ttu-id="1c18d-102">この構成要素は、アプリケーションが、実行時に動的にエンドポイント アドレスを検索するクライアント プログラムとして機能するための情報を格納する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="1c18d-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="1c18d-103">構文</span><span class="sxs-lookup"><span data-stu-id="1c18d-103">Syntax</span></span>  
  
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
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c18d-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1c18d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="1c18d-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1c18d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c18d-106">属性</span><span class="sxs-lookup"><span data-stu-id="1c18d-106">Attributes</span></span>  

 <span data-ttu-id="1c18d-107">なし。</span><span class="sxs-lookup"><span data-stu-id="1c18d-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1c18d-108">子要素</span><span class="sxs-lookup"><span data-stu-id="1c18d-108">Child Elements</span></span>  
  
|<span data-ttu-id="1c18d-109">要素</span><span class="sxs-lookup"><span data-stu-id="1c18d-109">Element</span></span>|<span data-ttu-id="1c18d-110">説明</span><span class="sxs-lookup"><span data-stu-id="1c18d-110">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="1c18d-111">サービス探索プロセスにクライアントとして参加するためにアプリケーションが必要とする設定を格納します。</span><span class="sxs-lookup"><span data-stu-id="1c18d-111">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c18d-112">親要素</span><span class="sxs-lookup"><span data-stu-id="1c18d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="1c18d-113">要素</span><span class="sxs-lookup"><span data-stu-id="1c18d-113">Element</span></span>|<span data-ttu-id="1c18d-114">説明</span><span class="sxs-lookup"><span data-stu-id="1c18d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="1c18d-115">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="1c18d-115">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c18d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c18d-116">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
