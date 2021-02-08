---
description: 詳細については、「WCF」を参照してください。 <activityScheduledQueries>
title: <activityScheduledQueries> WCF の
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: b92bb2827b4c8bce43e4ee0b8dc03c7be124e3da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782248"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="f9528-103">\<activityScheduledQueries> WCF の</span><span class="sxs-lookup"><span data-stu-id="f9528-103">\<activityScheduledQueries> of WCF</span></span>

<span data-ttu-id="f9528-104">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="f9528-104">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="f9528-105">アクティビティがスケジュールされたレコードを追跡参加要素が定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="f9528-105">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="f9528-106">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9528-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="f9528-107">構文</span><span class="sxs-lookup"><span data-stu-id="f9528-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9528-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="f9528-108">Attributes and elements</span></span>  

<span data-ttu-id="f9528-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f9528-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9528-110">属性</span><span class="sxs-lookup"><span data-stu-id="f9528-110">Attributes</span></span>  

<span data-ttu-id="f9528-111">なし。</span><span class="sxs-lookup"><span data-stu-id="f9528-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f9528-112">子要素</span><span class="sxs-lookup"><span data-stu-id="f9528-112">Child elements</span></span>  
  
|<span data-ttu-id="f9528-113">要素</span><span class="sxs-lookup"><span data-stu-id="f9528-113">Element</span></span>|<span data-ttu-id="f9528-114">説明</span><span class="sxs-lookup"><span data-stu-id="f9528-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="f9528-115">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="f9528-115">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9528-116">親要素</span><span class="sxs-lookup"><span data-stu-id="f9528-116">Parent elements</span></span>  
  
|<span data-ttu-id="f9528-117">要素</span><span class="sxs-lookup"><span data-stu-id="f9528-117">Element</span></span>|<span data-ttu-id="f9528-118">説明</span><span class="sxs-lookup"><span data-stu-id="f9528-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="f9528-119">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="f9528-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9528-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9528-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="f9528-121">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="f9528-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f9528-122">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="f9528-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
