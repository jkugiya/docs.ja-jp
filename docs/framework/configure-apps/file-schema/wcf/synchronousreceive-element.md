---
description: '詳細情報: <synchronousReceive> 要素'
title: <synchronousReceive> 要素
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: afcd10b4ad41bd6ff12dbf246f66ef7fac4e759a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682619"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="c93a0-103">\<synchronousReceive> 要素</span><span class="sxs-lookup"><span data-stu-id="c93a0-103">\<synchronousReceive> element</span></span>

<span data-ttu-id="c93a0-104">この構成要素は、サービスまたはクライアント アプリケーションでメッセージを受信する場合のランタイム動作を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c93a0-104">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="c93a0-105">属性や子要素はありません。</span><span class="sxs-lookup"><span data-stu-id="c93a0-105">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="c93a0-106">構文</span><span class="sxs-lookup"><span data-stu-id="c93a0-106">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c93a0-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c93a0-107">Attributes and Elements</span></span>  

 <span data-ttu-id="c93a0-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c93a0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c93a0-109">属性</span><span class="sxs-lookup"><span data-stu-id="c93a0-109">Attributes</span></span>  

 <span data-ttu-id="c93a0-110">なし。</span><span class="sxs-lookup"><span data-stu-id="c93a0-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c93a0-111">子要素</span><span class="sxs-lookup"><span data-stu-id="c93a0-111">Child Elements</span></span>  

 <span data-ttu-id="c93a0-112">なし。</span><span class="sxs-lookup"><span data-stu-id="c93a0-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c93a0-113">親要素</span><span class="sxs-lookup"><span data-stu-id="c93a0-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c93a0-114">要素</span><span class="sxs-lookup"><span data-stu-id="c93a0-114">Element</span></span>|<span data-ttu-id="c93a0-115">説明</span><span class="sxs-lookup"><span data-stu-id="c93a0-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c93a0-116">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="c93a0-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c93a0-117">解説</span><span class="sxs-lookup"><span data-stu-id="c93a0-117">Remarks</span></span>  

 <span data-ttu-id="c93a0-118">この動作を使用して、既定の非同期受信ではなく同期受信を使用するようにチャネル リスナーに指示します。</span><span class="sxs-lookup"><span data-stu-id="c93a0-118">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="c93a0-119">Windows Communication Foundation (WCF) は、受け入れられたチャネルごとに新しいスレッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="c93a0-119">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="c93a0-120">チャネルが多数ある場合は、スレッドが不足する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c93a0-120">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c93a0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c93a0-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
