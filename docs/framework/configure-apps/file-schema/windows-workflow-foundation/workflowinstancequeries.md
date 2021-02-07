---
description: '詳細情報: <workflowInstanceQueries>'
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 7672bcd574c15f130b8553881e53994afe9cda93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697843"
---
# \<workflowInstanceQueries>

<span data-ttu-id="f9f0f-102">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡する構成要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="f9f0f-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="f9f0f-103">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9f0f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="f9f0f-104">構文</span><span class="sxs-lookup"><span data-stu-id="f9f0f-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9f0f-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f9f0f-105">Attributes and Elements</span></span>  

<span data-ttu-id="f9f0f-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f9f0f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9f0f-107">属性</span><span class="sxs-lookup"><span data-stu-id="f9f0f-107">Attributes</span></span>  

<span data-ttu-id="f9f0f-108">なし。</span><span class="sxs-lookup"><span data-stu-id="f9f0f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f9f0f-109">子要素</span><span class="sxs-lookup"><span data-stu-id="f9f0f-109">Child Elements</span></span>  
  
|<span data-ttu-id="f9f0f-110">要素</span><span class="sxs-lookup"><span data-stu-id="f9f0f-110">Element</span></span>|<span data-ttu-id="f9f0f-111">説明</span><span class="sxs-lookup"><span data-stu-id="f9f0f-111">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="f9f0f-112">ワークフロー インスタンスのライフサイクルの変化を追跡するために使用されるクエリ。</span><span class="sxs-lookup"><span data-stu-id="f9f0f-112">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9f0f-113">親要素</span><span class="sxs-lookup"><span data-stu-id="f9f0f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f9f0f-114">要素</span><span class="sxs-lookup"><span data-stu-id="f9f0f-114">Element</span></span>|<span data-ttu-id="f9f0f-115">説明</span><span class="sxs-lookup"><span data-stu-id="f9f0f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="f9f0f-116">**ActivityDefinitionId** プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="f9f0f-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9f0f-117">解説</span><span class="sxs-lookup"><span data-stu-id="f9f0f-117">Remarks</span></span>  

<span data-ttu-id="f9f0f-118"><xref:System.Activities.Tracking.WorkflowInstanceQuery> は、次の <xref:System.Activities.Tracking.TrackingRecord> オブジェクトの定期受信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f9f0f-118">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="f9f0f-119">例</span><span class="sxs-lookup"><span data-stu-id="f9f0f-119">Example</span></span>  

<span data-ttu-id="f9f0f-120">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="f9f0f-120">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9f0f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9f0f-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f9f0f-122">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="f9f0f-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f9f0f-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="f9f0f-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
