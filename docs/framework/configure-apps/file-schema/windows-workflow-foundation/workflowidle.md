---
description: '詳細情報: <workflowIdle>'
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: c1707ab5c633a358846a8ddf529bbfab90d3012d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697960"
---
# \<workflowIdle>

<span data-ttu-id="d53df-102">アイドル状態のワークフロー インスタンスのアンロードおよび永続化のタイミングを制御するサービス動作。</span><span class="sxs-lookup"><span data-stu-id="d53df-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a><span data-ttu-id="d53df-103">構文</span><span class="sxs-lookup"><span data-stu-id="d53df-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan"
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d53df-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d53df-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d53df-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d53df-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d53df-106">属性</span><span class="sxs-lookup"><span data-stu-id="d53df-106">Attributes</span></span>  
  
|<span data-ttu-id="d53df-107">属性</span><span class="sxs-lookup"><span data-stu-id="d53df-107">Attribute</span></span>|<span data-ttu-id="d53df-108">説明</span><span class="sxs-lookup"><span data-stu-id="d53df-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d53df-109">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="d53df-109">timeToPersist</span></span>|<span data-ttu-id="d53df-110">ワークフローがアイドル状態から永続化されるまでの継続時間を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="d53df-110">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="d53df-111">既定値は TimeSpan.MaxValue です。</span><span class="sxs-lookup"><span data-stu-id="d53df-111">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="d53df-112">継続時間は、ワークフロー インスタンスがアイドル状態になった時点から開始します。</span><span class="sxs-lookup"><span data-stu-id="d53df-112">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="d53df-113">この属性は、ワークフロー インスタンスを、可能な限り長くメモリに保持しながら、積極的に永続化しようとする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d53df-113">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="d53df-114">この属性は、値が **timeToUnload** 属性より小さい場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="d53df-114">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="d53df-115">それより大きい場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="d53df-115">If it is greater, it is ignored.</span></span> <span data-ttu-id="d53df-116">**TimeToUnload** 属性によって指定された値の前にこの属性が経過した場合、ワークフローがアンロードされる前に永続化を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d53df-116">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="d53df-117">これは、ワークフローを永続化するまでアンロード操作に遅延が生じる場合があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="d53df-117">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="d53df-118">永続化レイヤーは一時的なエラーの再試行処理は行いますが、回復不可能なエラーに対しては例外をスローするだけです。</span><span class="sxs-lookup"><span data-stu-id="d53df-118">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="d53df-119">したがって、永続化中にスローされる例外は致命的な例外として処理され、ワークフロー インスタンスが中止されます。</span><span class="sxs-lookup"><span data-stu-id="d53df-119">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="d53df-120">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="d53df-120">timeToUnload</span></span>|<span data-ttu-id="d53df-121">ワークフローがアイドル状態からアンロードされるまでの継続時間を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="d53df-121">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="d53df-122">既定値は 1 分です。</span><span class="sxs-lookup"><span data-stu-id="d53df-122">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="d53df-123">ワークフローをアンロードすることは、同時に、永続化することも意味します。</span><span class="sxs-lookup"><span data-stu-id="d53df-123">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="d53df-124">この属性をゼロに設定した場合は、ワークフローがアイドル状態になった直後に、ワークフロー インスタンスが永続化され、アンロードされます。</span><span class="sxs-lookup"><span data-stu-id="d53df-124">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="d53df-125">この属性を TimeSpan.MaxValue に設定すると、アンロード操作を事実上、無効にします。</span><span class="sxs-lookup"><span data-stu-id="d53df-125">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="d53df-126">アイドル状態になったワークフロー インスタンスはアンロードされません。</span><span class="sxs-lookup"><span data-stu-id="d53df-126">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d53df-127">子要素</span><span class="sxs-lookup"><span data-stu-id="d53df-127">Child Elements</span></span>  

 <span data-ttu-id="d53df-128">なし。</span><span class="sxs-lookup"><span data-stu-id="d53df-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d53df-129">親要素</span><span class="sxs-lookup"><span data-stu-id="d53df-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d53df-130">要素</span><span class="sxs-lookup"><span data-stu-id="d53df-130">Element</span></span>|<span data-ttu-id="d53df-131">説明</span><span class="sxs-lookup"><span data-stu-id="d53df-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d53df-132">\<serviceBehaviors> の \<behavior></span><span class="sxs-lookup"><span data-stu-id="d53df-132">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="d53df-133">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="d53df-133">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d53df-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="d53df-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
