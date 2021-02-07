---
description: '詳細情報: <workflowControlEndpoint>'
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 5205edf159bd947531231e69fd23f6cdf9c77d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682346"
---
# \<workflowControlEndpoint>

<span data-ttu-id="44238-102">この構成要素は、ワークフロー インスタンスの実行の制御 (作成、実行、保留、終了など) に使用する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="44238-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="44238-103">構文</span><span class="sxs-lookup"><span data-stu-id="44238-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44238-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="44238-104">Attributes and Elements</span></span>  

 <span data-ttu-id="44238-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="44238-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44238-106">属性</span><span class="sxs-lookup"><span data-stu-id="44238-106">Attributes</span></span>  
  
|<span data-ttu-id="44238-107">属性</span><span class="sxs-lookup"><span data-stu-id="44238-107">Attribute</span></span>|<span data-ttu-id="44238-108">説明</span><span class="sxs-lookup"><span data-stu-id="44238-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44238-109">name</span><span class="sxs-lookup"><span data-stu-id="44238-109">name</span></span>|<span data-ttu-id="44238-110">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="44238-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="44238-111">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="44238-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44238-112">子要素</span><span class="sxs-lookup"><span data-stu-id="44238-112">Child Elements</span></span>  

 <span data-ttu-id="44238-113">なし。</span><span class="sxs-lookup"><span data-stu-id="44238-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44238-114">親要素</span><span class="sxs-lookup"><span data-stu-id="44238-114">Parent Elements</span></span>  
  
|<span data-ttu-id="44238-115">要素</span><span class="sxs-lookup"><span data-stu-id="44238-115">Element</span></span>|<span data-ttu-id="44238-116">説明</span><span class="sxs-lookup"><span data-stu-id="44238-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="44238-117">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="44238-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44238-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="44238-118">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
