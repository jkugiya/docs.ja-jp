---
description: '詳細情報: <activityScheduledQueries>'
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 1f43642edffea782a9e5257a3568868645994a46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729837"
---
# \<activityScheduledQueries>

<span data-ttu-id="b0c5a-102">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="b0c5a-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b0c5a-103">アクティビティがスケジュールされたレコードを追跡参加要素が定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="b0c5a-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="b0c5a-104">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0c5a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="b0c5a-105">構文</span><span class="sxs-lookup"><span data-stu-id="b0c5a-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0c5a-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b0c5a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b0c5a-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b0c5a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0c5a-108">属性</span><span class="sxs-lookup"><span data-stu-id="b0c5a-108">Attributes</span></span>  

 <span data-ttu-id="b0c5a-109">なし。</span><span class="sxs-lookup"><span data-stu-id="b0c5a-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b0c5a-110">子要素</span><span class="sxs-lookup"><span data-stu-id="b0c5a-110">Child Elements</span></span>  
  
|<span data-ttu-id="b0c5a-111">要素</span><span class="sxs-lookup"><span data-stu-id="b0c5a-111">Element</span></span>|<span data-ttu-id="b0c5a-112">説明</span><span class="sxs-lookup"><span data-stu-id="b0c5a-112">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="b0c5a-113">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="b0c5a-113">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0c5a-114">親要素</span><span class="sxs-lookup"><span data-stu-id="b0c5a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b0c5a-115">要素</span><span class="sxs-lookup"><span data-stu-id="b0c5a-115">Element</span></span>|<span data-ttu-id="b0c5a-116">説明</span><span class="sxs-lookup"><span data-stu-id="b0c5a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="b0c5a-117">**ActivityDefinitionId** プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="b0c5a-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0c5a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0c5a-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b0c5a-119">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="b0c5a-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b0c5a-120">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="b0c5a-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
