---
description: 詳細については、「<System.servicemodel> ワークフロー」を参照してください。
title: ワークフローの System.servicemodel> を <する
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 393c1055d6b136ed27a297e00133f5b53d12fd38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681748"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="bbf65-103">\<system.serviceModel> ワークフローの</span><span class="sxs-lookup"><span data-stu-id="bbf65-103">\<system.serviceModel> of workflow</span></span>

<span data-ttu-id="bbf65-104">この構成セクションには、すべてのワークフロー構成要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bbf65-104">This configuration section contains all the workflow configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.ServiceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="bbf65-105">構文</span><span class="sxs-lookup"><span data-stu-id="bbf65-105">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore
          connectionStringName="String"
          hostLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionAction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>
     <participants>
      <add name="String"
           profileName="String"  
           type="String" />
     </participants>
    <trackingProfile name="String">  
      <workflow activityDefinitionId="String">  
          <activityScheduledQueries>  
             <activityScheduledQuery activityName="String"  
                 childActivityName="String"/>  
          </activityScheduledQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
                </variables>  
          </activityStateQueries>  
          <bookmarkResumptionQueries>  
             <bookmarkResumptionQuery name="String" />  
          </bookmarkResumptionQueries>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
          <customTrackingQueries>  
             <customTrackingQuery activityName="String"  
                 name="String"/>  
          </customTrackingQueries>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>
   </profiles>  
  </tracking>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbf65-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bbf65-106">Attributes and Elements</span></span>  

 <span data-ttu-id="bbf65-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbf65-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbf65-108">属性</span><span class="sxs-lookup"><span data-stu-id="bbf65-108">Attributes</span></span>  

 <span data-ttu-id="bbf65-109">なし</span><span class="sxs-lookup"><span data-stu-id="bbf65-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bbf65-110">子要素</span><span class="sxs-lookup"><span data-stu-id="bbf65-110">Child Elements</span></span>  
  
|<span data-ttu-id="bbf65-111">要素</span><span class="sxs-lookup"><span data-stu-id="bbf65-111">Element</span></span>|<span data-ttu-id="bbf65-112">説明</span><span class="sxs-lookup"><span data-stu-id="bbf65-112">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors-of-workflow.md)|<span data-ttu-id="bbf65-113">このセクションでは、 **Servicebehaviors** コレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="bbf65-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="bbf65-114">各コレクション内の要素は、サービスによって使用されるそれぞれの動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="bbf65-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="bbf65-115">各動作要素は、一意の **name** 属性によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="bbf65-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[\<tracking>](tracking.md)|<span data-ttu-id="bbf65-116">ワークフロー サービスの追跡設定を定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="bbf65-116">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="bbf65-117">ワークフロー追跡とその構成の詳細については、「ワークフローの [追跡とトレース](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 」と「ワークフロー [の追跡の構成](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbf65-117">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbf65-118">親要素</span><span class="sxs-lookup"><span data-stu-id="bbf65-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bbf65-119">要素</span><span class="sxs-lookup"><span data-stu-id="bbf65-119">Element</span></span>|<span data-ttu-id="bbf65-120">説明</span><span class="sxs-lookup"><span data-stu-id="bbf65-120">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="bbf65-121">.NET 構成ファイルのすべての構成要素のルート要素。</span><span class="sxs-lookup"><span data-stu-id="bbf65-121">The root element for all configuration elements in a .NET configuration file.</span></span>|
