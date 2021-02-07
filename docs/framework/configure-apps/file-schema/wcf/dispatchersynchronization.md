---
description: '詳細情報: <dispatcherSynchronization>'
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 93664dec3648ed58df7e3e5c0760f1694c60ba7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749605"
---
# \<dispatcherSynchronization>
  
<span data-ttu-id="ee034-102">サービスが非同期に応答を返すことができるようにするエンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee034-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a><span data-ttu-id="ee034-103">構文</span><span class="sxs-lookup"><span data-stu-id="ee034-103">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="ee034-104">Type</span><span class="sxs-lookup"><span data-stu-id="ee034-104">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee034-105">属性と要素</span><span class="sxs-lookup"><span data-stu-id="ee034-105">Attributes and elements</span></span>  
  
<span data-ttu-id="ee034-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee034-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee034-107">属性</span><span class="sxs-lookup"><span data-stu-id="ee034-107">Attributes</span></span>

| <span data-ttu-id="ee034-108">属性</span><span class="sxs-lookup"><span data-stu-id="ee034-108">Attribute</span></span>               | <span data-ttu-id="ee034-109">説明</span><span class="sxs-lookup"><span data-stu-id="ee034-109">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="ee034-110">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="ee034-110">asynchronousSendEnabled</span></span> | <span data-ttu-id="ee034-111">非同期の送信動作が有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="ee034-111">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="ee034-112">チャネルで発行可能な同時受信の数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="ee034-112">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="ee034-113">この値は、サービス調整の動作を適切に構成した後に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee034-113">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="ee034-114">子要素</span><span class="sxs-lookup"><span data-stu-id="ee034-114">Child elements</span></span>

<span data-ttu-id="ee034-115">なし。</span><span class="sxs-lookup"><span data-stu-id="ee034-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ee034-116">親要素</span><span class="sxs-lookup"><span data-stu-id="ee034-116">Parent elements</span></span>

| <span data-ttu-id="ee034-117">要素</span><span class="sxs-lookup"><span data-stu-id="ee034-117">Element</span></span> | <span data-ttu-id="ee034-118">説明</span><span class="sxs-lookup"><span data-stu-id="ee034-118">Description</span></span> |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ee034-119">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee034-119">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ee034-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee034-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
