---
description: '詳細情報: <serviceTimeouts>'
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: bc9ef99078f8c6fa3b441604e14df928eec054e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682727"
---
# \<serviceTimeouts>

<span data-ttu-id="2d5d7-102">サービスのタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="2d5d7-102">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="2d5d7-103">構文</span><span class="sxs-lookup"><span data-stu-id="2d5d7-103">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="2d5d7-104">Type</span><span class="sxs-lookup"><span data-stu-id="2d5d7-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d5d7-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2d5d7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2d5d7-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d5d7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d5d7-107">属性</span><span class="sxs-lookup"><span data-stu-id="2d5d7-107">Attributes</span></span>  
  
|<span data-ttu-id="2d5d7-108">属性</span><span class="sxs-lookup"><span data-stu-id="2d5d7-108">Attribute</span></span>|<span data-ttu-id="2d5d7-109">説明</span><span class="sxs-lookup"><span data-stu-id="2d5d7-109">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="2d5d7-110">クライアントからサーバーへのトランザクションが発生するまでに待機できる時間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="2d5d7-110">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="2d5d7-111">既定値は "00:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="2d5d7-111">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d5d7-112">子要素</span><span class="sxs-lookup"><span data-stu-id="2d5d7-112">Child Elements</span></span>  

 <span data-ttu-id="2d5d7-113">なし。</span><span class="sxs-lookup"><span data-stu-id="2d5d7-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d5d7-114">親要素</span><span class="sxs-lookup"><span data-stu-id="2d5d7-114">Parent Elements</span></span>  
  
|<span data-ttu-id="2d5d7-115">要素</span><span class="sxs-lookup"><span data-stu-id="2d5d7-115">Element</span></span>|<span data-ttu-id="2d5d7-116">説明</span><span class="sxs-lookup"><span data-stu-id="2d5d7-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2d5d7-117">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="2d5d7-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d5d7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d5d7-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
