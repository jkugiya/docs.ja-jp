---
description: 詳細については、「WCF」を参照してください。 <activityScheduledQuery>
title: <activityScheduledQuery> WCF の
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b1b5f971dccfbc650ee12a08a9ae2fa7b745db50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802360"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="31b30-103">\<activityScheduledQuery> WCF の</span><span class="sxs-lookup"><span data-stu-id="31b30-103">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="31b30-104">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="31b30-104">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="31b30-105">アクティビティがスケジュールされたレコードを追跡参加要素が定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="31b30-105">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="31b30-106">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31b30-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="31b30-107">構文</span><span class="sxs-lookup"><span data-stu-id="31b30-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31b30-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="31b30-108">Attributes and elements</span></span>  

<span data-ttu-id="31b30-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="31b30-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31b30-110">属性</span><span class="sxs-lookup"><span data-stu-id="31b30-110">Attributes</span></span>  
  
|<span data-ttu-id="31b30-111">属性</span><span class="sxs-lookup"><span data-stu-id="31b30-111">Attribute</span></span>|<span data-ttu-id="31b30-112">説明</span><span class="sxs-lookup"><span data-stu-id="31b30-112">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="31b30-113">キャンセルを要求しているアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="31b30-113">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="31b30-114">キャンセルが要求された子アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="31b30-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31b30-115">子要素</span><span class="sxs-lookup"><span data-stu-id="31b30-115">Child elements</span></span>

<span data-ttu-id="31b30-116">なし。</span><span class="sxs-lookup"><span data-stu-id="31b30-116">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="31b30-117">親要素</span><span class="sxs-lookup"><span data-stu-id="31b30-117">Parent elements</span></span>  
  
|<span data-ttu-id="31b30-118">要素</span><span class="sxs-lookup"><span data-stu-id="31b30-118">Element</span></span>|<span data-ttu-id="31b30-119">説明</span><span class="sxs-lookup"><span data-stu-id="31b30-119">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="31b30-120">親アクティビティによって実行されるようにスケジュールされたアクティビティを追跡するために使用されるクエリのコレクション。</span><span class="sxs-lookup"><span data-stu-id="31b30-120">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31b30-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="31b30-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="31b30-122">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="31b30-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="31b30-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="31b30-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
