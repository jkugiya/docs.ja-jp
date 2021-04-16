---
description: '詳細情報: <callbackTimeouts>'
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 8e2e05ad23f661c38430ccddc615c37705e6fc44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639199"
---
# \<callbackTimeouts>

<span data-ttu-id="23f5a-102">双方向コールバック コントラクト シナリオでトランザクションをサーバーからクライアントに転送する際のタイムアウト値を指定します。</span><span class="sxs-lookup"><span data-stu-id="23f5a-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="23f5a-103">構文</span><span class="sxs-lookup"><span data-stu-id="23f5a-103">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="23f5a-104">種類</span><span class="sxs-lookup"><span data-stu-id="23f5a-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23f5a-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="23f5a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="23f5a-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="23f5a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23f5a-107">属性</span><span class="sxs-lookup"><span data-stu-id="23f5a-107">Attributes</span></span>  
  
|<span data-ttu-id="23f5a-108">属性</span><span class="sxs-lookup"><span data-stu-id="23f5a-108">Attribute</span></span>|<span data-ttu-id="23f5a-109">説明</span><span class="sxs-lookup"><span data-stu-id="23f5a-109">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="23f5a-110">トランザクションが完了する必要があるまたは自動的に終了される必要がある制限時間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="23f5a-110">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="23f5a-111">既定値は "00:00:00" です。</span><span class="sxs-lookup"><span data-stu-id="23f5a-111">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23f5a-112">子要素</span><span class="sxs-lookup"><span data-stu-id="23f5a-112">Child Elements</span></span>  

 <span data-ttu-id="23f5a-113">なし。</span><span class="sxs-lookup"><span data-stu-id="23f5a-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23f5a-114">親要素</span><span class="sxs-lookup"><span data-stu-id="23f5a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="23f5a-115">要素</span><span class="sxs-lookup"><span data-stu-id="23f5a-115">Element</span></span>|<span data-ttu-id="23f5a-116">説明</span><span class="sxs-lookup"><span data-stu-id="23f5a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="23f5a-117">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="23f5a-117">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23f5a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="23f5a-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
