---
description: '詳細情報: <workflowUnhandledException>'
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: b9258c986ffa154e490f80bead1dc53d8f7ef44d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697778"
---
# \<workflowUnhandledException>

<span data-ttu-id="7a02a-102">ワークフロー サービス内で未処理の例外が発生した場合のアクションを指定するためのサービス動作。</span><span class="sxs-lookup"><span data-stu-id="7a02a-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="7a02a-103">構文</span><span class="sxs-lookup"><span data-stu-id="7a02a-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a02a-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7a02a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7a02a-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a02a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a02a-106">属性</span><span class="sxs-lookup"><span data-stu-id="7a02a-106">Attributes</span></span>  
  
|<span data-ttu-id="7a02a-107">属性</span><span class="sxs-lookup"><span data-stu-id="7a02a-107">Attribute</span></span>|<span data-ttu-id="7a02a-108">説明</span><span class="sxs-lookup"><span data-stu-id="7a02a-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a02a-109">action</span><span class="sxs-lookup"><span data-stu-id="7a02a-109">action</span></span>|<span data-ttu-id="7a02a-110">未処理の例外が発生した場合のアクションを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="7a02a-110">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="7a02a-111">この属性は <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> 型です。</span><span class="sxs-lookup"><span data-stu-id="7a02a-111">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a02a-112">子要素</span><span class="sxs-lookup"><span data-stu-id="7a02a-112">Child Elements</span></span>  

 <span data-ttu-id="7a02a-113">なし。</span><span class="sxs-lookup"><span data-stu-id="7a02a-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a02a-114">親要素</span><span class="sxs-lookup"><span data-stu-id="7a02a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="7a02a-115">要素</span><span class="sxs-lookup"><span data-stu-id="7a02a-115">Element</span></span>|<span data-ttu-id="7a02a-116">説明</span><span class="sxs-lookup"><span data-stu-id="7a02a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a02a-117">\<serviceBehaviors> の \<behavior></span><span class="sxs-lookup"><span data-stu-id="7a02a-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="7a02a-118">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a02a-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a02a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a02a-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
