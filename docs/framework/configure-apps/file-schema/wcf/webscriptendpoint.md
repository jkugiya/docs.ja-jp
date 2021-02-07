---
description: '詳細情報: <webScriptEndpoint>'
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: eef4eb8e8e7345492f967c85b6245f733a4c824f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682502"
---
# \<webScriptEndpoint>

<span data-ttu-id="489f9-102">この構成要素は、 [\<webHttpBinding>](webhttpbinding.md) 動作を自動的に追加する固定バインドを持つ標準エンドポイントを定義し [\<enableWebScript>](enablewebscript.md) ます。</span><span class="sxs-lookup"><span data-stu-id="489f9-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="489f9-103">このエンドポイントは、ASP.NET AJAX アプリケーションから呼び出されるサービスを作成する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="489f9-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="489f9-104">構文</span><span class="sxs-lookup"><span data-stu-id="489f9-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="489f9-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="489f9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="489f9-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="489f9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="489f9-107">属性</span><span class="sxs-lookup"><span data-stu-id="489f9-107">Attributes</span></span>  
  
|<span data-ttu-id="489f9-108">属性</span><span class="sxs-lookup"><span data-stu-id="489f9-108">Attribute</span></span>|<span data-ttu-id="489f9-109">説明</span><span class="sxs-lookup"><span data-stu-id="489f9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="489f9-110">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="489f9-110">webEndpointType</span></span>|<span data-ttu-id="489f9-111">エンドポイントの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="489f9-111">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="489f9-112">子要素</span><span class="sxs-lookup"><span data-stu-id="489f9-112">Child Elements</span></span>  

 <span data-ttu-id="489f9-113">なし。</span><span class="sxs-lookup"><span data-stu-id="489f9-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="489f9-114">親要素</span><span class="sxs-lookup"><span data-stu-id="489f9-114">Parent Elements</span></span>  
  
|<span data-ttu-id="489f9-115">要素</span><span class="sxs-lookup"><span data-stu-id="489f9-115">Element</span></span>|<span data-ttu-id="489f9-116">説明</span><span class="sxs-lookup"><span data-stu-id="489f9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="489f9-117">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="489f9-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="489f9-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="489f9-118">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
