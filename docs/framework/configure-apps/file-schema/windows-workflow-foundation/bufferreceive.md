---
description: '詳細情報: <bufferReceive>'
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 8f5e58e0e72a81d8b3a20a68e0890be907c20d2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698090"
---
# \<bufferReceive>

<span data-ttu-id="d40fe-102">サービスが、バッファーされた受信処理を使用するためのサービス動作。これにより、ワークフロー サービスは、順番を無視したメッセージを処理できます。</span><span class="sxs-lookup"><span data-stu-id="d40fe-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="d40fe-103">構文</span><span class="sxs-lookup"><span data-stu-id="d40fe-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d40fe-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d40fe-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d40fe-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d40fe-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d40fe-106">属性</span><span class="sxs-lookup"><span data-stu-id="d40fe-106">Attributes</span></span>  
  
|<span data-ttu-id="d40fe-107">属性</span><span class="sxs-lookup"><span data-stu-id="d40fe-107">Attribute</span></span>|<span data-ttu-id="d40fe-108">説明</span><span class="sxs-lookup"><span data-stu-id="d40fe-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d40fe-109">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="d40fe-109">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="d40fe-110">各チャネルで許容される保留状態のメッセージの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="d40fe-110">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="d40fe-111">既定値は 512 です。</span><span class="sxs-lookup"><span data-stu-id="d40fe-111">The default value is 512.</span></span> <span data-ttu-id="d40fe-112">このプロパティは、ワークフロー サービスで受信できる、順番を無視したメッセージの数を制限します。</span><span class="sxs-lookup"><span data-stu-id="d40fe-112">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d40fe-113">子要素</span><span class="sxs-lookup"><span data-stu-id="d40fe-113">Child Elements</span></span>  

 <span data-ttu-id="d40fe-114">なし。</span><span class="sxs-lookup"><span data-stu-id="d40fe-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d40fe-115">親要素</span><span class="sxs-lookup"><span data-stu-id="d40fe-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d40fe-116">要素</span><span class="sxs-lookup"><span data-stu-id="d40fe-116">Element</span></span>|<span data-ttu-id="d40fe-117">説明</span><span class="sxs-lookup"><span data-stu-id="d40fe-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d40fe-118">\<serviceBehaviors> の \<behavior></span><span class="sxs-lookup"><span data-stu-id="d40fe-118">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="d40fe-119">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="d40fe-119">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d40fe-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d40fe-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
