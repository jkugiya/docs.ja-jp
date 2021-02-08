---
description: '詳細情報: <activityScheduledQuery>'
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 72aa9c2d3480488d4468d008fa8a4306929c190d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802113"
---
# \<activityScheduledQuery>

<span data-ttu-id="d4abd-102">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="d4abd-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="d4abd-103">アクティビティがスケジュールされたレコードを追跡参加要素が定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="d4abd-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="d4abd-104">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4abd-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="d4abd-105">構文</span><span class="sxs-lookup"><span data-stu-id="d4abd-105">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4abd-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d4abd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d4abd-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4abd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4abd-108">属性</span><span class="sxs-lookup"><span data-stu-id="d4abd-108">Attributes</span></span>  
  
|<span data-ttu-id="d4abd-109">属性</span><span class="sxs-lookup"><span data-stu-id="d4abd-109">Attribute</span></span>|<span data-ttu-id="d4abd-110">説明</span><span class="sxs-lookup"><span data-stu-id="d4abd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4abd-111">activityName</span><span class="sxs-lookup"><span data-stu-id="d4abd-111">activityName</span></span>|<span data-ttu-id="d4abd-112">キャンセルを要求しているアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="d4abd-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="d4abd-113">childActivityName</span><span class="sxs-lookup"><span data-stu-id="d4abd-113">childActivityName</span></span>|<span data-ttu-id="d4abd-114">キャンセルが要求された子アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="d4abd-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4abd-115">子要素</span><span class="sxs-lookup"><span data-stu-id="d4abd-115">Child Elements</span></span>  

 <span data-ttu-id="d4abd-116">なし。</span><span class="sxs-lookup"><span data-stu-id="d4abd-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4abd-117">親要素</span><span class="sxs-lookup"><span data-stu-id="d4abd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d4abd-118">要素</span><span class="sxs-lookup"><span data-stu-id="d4abd-118">Element</span></span>|<span data-ttu-id="d4abd-119">説明</span><span class="sxs-lookup"><span data-stu-id="d4abd-119">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="d4abd-120">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="d4abd-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4abd-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4abd-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d4abd-122">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="d4abd-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d4abd-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="d4abd-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
