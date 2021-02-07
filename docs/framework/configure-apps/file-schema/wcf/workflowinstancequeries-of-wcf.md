---
description: 詳細については、「WCF」を参照してください。 <workflowInstanceQueries>
title: <workflowInstanceQueries> WCF の
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: d4dc4827cba5a1732070b5269350ca3dd9bf2c47
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682333"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="3558d-103">\<workflowInstanceQueries> WCF の</span><span class="sxs-lookup"><span data-stu-id="3558d-103">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="3558d-104">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡する構成要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="3558d-104">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="3558d-105">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3558d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="3558d-106">構文</span><span class="sxs-lookup"><span data-stu-id="3558d-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3558d-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="3558d-107">Attributes and elements</span></span>

<span data-ttu-id="3558d-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3558d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3558d-109">属性</span><span class="sxs-lookup"><span data-stu-id="3558d-109">Attributes</span></span>  

<span data-ttu-id="3558d-110">なし。</span><span class="sxs-lookup"><span data-stu-id="3558d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3558d-111">子要素</span><span class="sxs-lookup"><span data-stu-id="3558d-111">Child elements</span></span>  
  
|<span data-ttu-id="3558d-112">要素</span><span class="sxs-lookup"><span data-stu-id="3558d-112">Element</span></span>|<span data-ttu-id="3558d-113">説明</span><span class="sxs-lookup"><span data-stu-id="3558d-113">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="3558d-114">ワークフロー インスタンスのライフサイクルの変化を追跡するために使用されるクエリ。</span><span class="sxs-lookup"><span data-stu-id="3558d-114">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3558d-115">親要素</span><span class="sxs-lookup"><span data-stu-id="3558d-115">Parent elements</span></span>  
  
|<span data-ttu-id="3558d-116">要素</span><span class="sxs-lookup"><span data-stu-id="3558d-116">Element</span></span>|<span data-ttu-id="3558d-117">説明</span><span class="sxs-lookup"><span data-stu-id="3558d-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="3558d-118">[ActivityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId)プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="3558d-118">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3558d-119">解説</span><span class="sxs-lookup"><span data-stu-id="3558d-119">Remarks</span></span>

<span data-ttu-id="3558d-120"><xref:System.Activities.Tracking.WorkflowInstanceQuery> は、次の <xref:System.Activities.Tracking.TrackingRecord> オブジェクトの定期受信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3558d-120">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="3558d-121">例</span><span class="sxs-lookup"><span data-stu-id="3558d-121">Example</span></span>  

<span data-ttu-id="3558d-122">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="3558d-122">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="3558d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="3558d-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3558d-124">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="3558d-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3558d-125">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="3558d-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
