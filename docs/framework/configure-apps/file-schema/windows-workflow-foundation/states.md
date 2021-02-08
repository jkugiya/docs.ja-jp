---
description: '詳細情報: <states>'
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 9a66a1ce460db1f5f55fb99a191368635220f32f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781975"
---
# \<states>

<span data-ttu-id="958a8-102">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="958a8-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="958a8-103">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="958a8-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="958a8-104">構文</span><span class="sxs-lookup"><span data-stu-id="958a8-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="958a8-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="958a8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="958a8-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="958a8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="958a8-107">属性</span><span class="sxs-lookup"><span data-stu-id="958a8-107">Attributes</span></span>  

 <span data-ttu-id="958a8-108">なし。</span><span class="sxs-lookup"><span data-stu-id="958a8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="958a8-109">子要素</span><span class="sxs-lookup"><span data-stu-id="958a8-109">Child Elements</span></span>  
  
|<span data-ttu-id="958a8-110">要素</span><span class="sxs-lookup"><span data-stu-id="958a8-110">Element</span></span>|<span data-ttu-id="958a8-111">説明</span><span class="sxs-lookup"><span data-stu-id="958a8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="958a8-112">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態。</span><span class="sxs-lookup"><span data-stu-id="958a8-112">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="958a8-113">親要素</span><span class="sxs-lookup"><span data-stu-id="958a8-113">Parent Elements</span></span>  
  
|<span data-ttu-id="958a8-114">要素</span><span class="sxs-lookup"><span data-stu-id="958a8-114">Element</span></span>|<span data-ttu-id="958a8-115">説明</span><span class="sxs-lookup"><span data-stu-id="958a8-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="958a8-116">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡するクエリ。</span><span class="sxs-lookup"><span data-stu-id="958a8-116">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="958a8-117">解説</span><span class="sxs-lookup"><span data-stu-id="958a8-117">Remarks</span></span>  

 <span data-ttu-id="958a8-118">返されたレコードは、このコレクションの状態でフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="958a8-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="958a8-119">次の表に、有効な状態の値を示します。</span><span class="sxs-lookup"><span data-stu-id="958a8-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="958a8-120">状態</span><span class="sxs-lookup"><span data-stu-id="958a8-120">State</span></span>|<span data-ttu-id="958a8-121">説明</span><span class="sxs-lookup"><span data-stu-id="958a8-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="958a8-122">Aborted</span><span class="sxs-lookup"><span data-stu-id="958a8-122">Aborted</span></span>|<span data-ttu-id="958a8-123">ワークフロー インスタンスは中止されました。</span><span class="sxs-lookup"><span data-stu-id="958a8-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="958a8-124">完了</span><span class="sxs-lookup"><span data-stu-id="958a8-124">Completed</span></span>|<span data-ttu-id="958a8-125">ワークフロー インスタンスは完了しました。</span><span class="sxs-lookup"><span data-stu-id="958a8-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="958a8-126">Deleted</span><span class="sxs-lookup"><span data-stu-id="958a8-126">Deleted</span></span>|<span data-ttu-id="958a8-127">ワークフロー インスタンスは削除されました。</span><span class="sxs-lookup"><span data-stu-id="958a8-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="958a8-128">アイドル</span><span class="sxs-lookup"><span data-stu-id="958a8-128">Idle</span></span>|<span data-ttu-id="958a8-129">ワークフロー インスタンスはアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="958a8-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="958a8-130">Persisted</span><span class="sxs-lookup"><span data-stu-id="958a8-130">Persisted</span></span>|<span data-ttu-id="958a8-131">ワークフロー インスタンスは永続化されました。</span><span class="sxs-lookup"><span data-stu-id="958a8-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="958a8-132">Resumed</span><span class="sxs-lookup"><span data-stu-id="958a8-132">Resumed</span></span>|<span data-ttu-id="958a8-133">ワークフロー インスタンスが再開されました。</span><span class="sxs-lookup"><span data-stu-id="958a8-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="958a8-134">Started</span><span class="sxs-lookup"><span data-stu-id="958a8-134">Started</span></span>|<span data-ttu-id="958a8-135">ワークフロー インスタンスが開始されました。</span><span class="sxs-lookup"><span data-stu-id="958a8-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="958a8-136">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="958a8-136">UnhandledException</span></span>|<span data-ttu-id="958a8-137">ワークフロー インスタンスで未処理の例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="958a8-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="958a8-138">アンロードされました</span><span class="sxs-lookup"><span data-stu-id="958a8-138">Unloaded</span></span>|<span data-ttu-id="958a8-139">ワークフロー インスタンスはアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="958a8-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="958a8-140">Canceled</span><span class="sxs-lookup"><span data-stu-id="958a8-140">Canceled</span></span>|<span data-ttu-id="958a8-141">ワークフロー インスタンスは取り消されました。</span><span class="sxs-lookup"><span data-stu-id="958a8-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="958a8-142">Suspended</span><span class="sxs-lookup"><span data-stu-id="958a8-142">Suspended</span></span>|<span data-ttu-id="958a8-143">ワークフロー インスタンスが中断されています。</span><span class="sxs-lookup"><span data-stu-id="958a8-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="958a8-144">終了</span><span class="sxs-lookup"><span data-stu-id="958a8-144">Terminated</span></span>|<span data-ttu-id="958a8-145">ワークフロー インスタンスは終了しました。</span><span class="sxs-lookup"><span data-stu-id="958a8-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="958a8-146">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="958a8-146">Unsuspended</span></span>|<span data-ttu-id="958a8-147">ワークフロー インスタンスの中断が解除されました。</span><span class="sxs-lookup"><span data-stu-id="958a8-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="958a8-148">例</span><span class="sxs-lookup"><span data-stu-id="958a8-148">Example</span></span>  

 <span data-ttu-id="958a8-149">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="958a8-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="958a8-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="958a8-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="958a8-151">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="958a8-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="958a8-152">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="958a8-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
