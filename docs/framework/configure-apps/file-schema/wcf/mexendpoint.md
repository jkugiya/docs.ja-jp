---
description: '詳細情報: <mexEndpoint>'
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 1872b6104aaaaa2787ca3f359026552499bade9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684413"
---
# \<mexEndpoint>

<span data-ttu-id="a2f02-102">この構成要素は、固定 IMetadataExchange コントラクトが含まれた標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="a2f02-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="a2f02-103">IMetadataExchange はすべてのメタデータ交換エンドポイントでコントラクトとして指定されるため、独自のエンドポイントを定義せずにこの標準エンドポイントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2f02-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="a2f02-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2f02-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2f02-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a2f02-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a2f02-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2f02-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2f02-107">属性</span><span class="sxs-lookup"><span data-stu-id="a2f02-107">Attributes</span></span>  
  
|<span data-ttu-id="a2f02-108">属性</span><span class="sxs-lookup"><span data-stu-id="a2f02-108">Attribute</span></span>|<span data-ttu-id="a2f02-109">説明</span><span class="sxs-lookup"><span data-stu-id="a2f02-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2f02-110">name</span><span class="sxs-lookup"><span data-stu-id="a2f02-110">name</span></span>|<span data-ttu-id="a2f02-111">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="a2f02-111">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="a2f02-112">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="a2f02-112">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2f02-113">子要素</span><span class="sxs-lookup"><span data-stu-id="a2f02-113">Child Elements</span></span>  

 <span data-ttu-id="a2f02-114">なし。</span><span class="sxs-lookup"><span data-stu-id="a2f02-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2f02-115">親要素</span><span class="sxs-lookup"><span data-stu-id="a2f02-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a2f02-116">要素</span><span class="sxs-lookup"><span data-stu-id="a2f02-116">Element</span></span>|<span data-ttu-id="a2f02-117">説明</span><span class="sxs-lookup"><span data-stu-id="a2f02-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="a2f02-118">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="a2f02-118">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
