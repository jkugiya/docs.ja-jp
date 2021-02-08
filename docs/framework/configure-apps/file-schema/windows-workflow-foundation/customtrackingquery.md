---
description: '詳細情報: <customTrackingQuery>'
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 24857aca39aad825a3dd4eca83fa3a51ec440b25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795093"
---
# \<customTrackingQuery>

<span data-ttu-id="b4a77-102">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="b4a77-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="b4a77-103">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="b4a77-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="b4a77-104">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4a77-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="b4a77-105">構文</span><span class="sxs-lookup"><span data-stu-id="b4a77-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String"
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4a77-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b4a77-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b4a77-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b4a77-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4a77-108">属性</span><span class="sxs-lookup"><span data-stu-id="b4a77-108">Attributes</span></span>  
  
|<span data-ttu-id="b4a77-109">属性</span><span class="sxs-lookup"><span data-stu-id="b4a77-109">Attribute</span></span>|<span data-ttu-id="b4a77-110">説明</span><span class="sxs-lookup"><span data-stu-id="b4a77-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b4a77-111">activityName</span><span class="sxs-lookup"><span data-stu-id="b4a77-111">activityName</span></span>|<span data-ttu-id="b4a77-112">追跡レコードを生成したアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b4a77-112">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="b4a77-113">name</span><span class="sxs-lookup"><span data-stu-id="b4a77-113">name</span></span>|<span data-ttu-id="b4a77-114">生成されたカスタム追跡レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b4a77-114">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4a77-115">子要素</span><span class="sxs-lookup"><span data-stu-id="b4a77-115">Child Elements</span></span>  

 <span data-ttu-id="b4a77-116">なし。</span><span class="sxs-lookup"><span data-stu-id="b4a77-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b4a77-117">親要素</span><span class="sxs-lookup"><span data-stu-id="b4a77-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b4a77-118">要素</span><span class="sxs-lookup"><span data-stu-id="b4a77-118">Element</span></span>|<span data-ttu-id="b4a77-119">説明</span><span class="sxs-lookup"><span data-stu-id="b4a77-119">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="b4a77-120">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="b4a77-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4a77-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4a77-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b4a77-122">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="b4a77-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b4a77-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="b4a77-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
