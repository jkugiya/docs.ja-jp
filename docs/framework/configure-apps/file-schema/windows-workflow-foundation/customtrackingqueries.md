---
description: '詳細情報: <customTrackingQueries>'
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 3601950742eb002f43969bea4612e830d8365509
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719059"
---
# \<customTrackingQueries>

<span data-ttu-id="c4ad2-102">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="c4ad2-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="c4ad2-103">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="c4ad2-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="c4ad2-104">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4ad2-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="c4ad2-105">構文</span><span class="sxs-lookup"><span data-stu-id="c4ad2-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4ad2-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c4ad2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c4ad2-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c4ad2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4ad2-108">属性</span><span class="sxs-lookup"><span data-stu-id="c4ad2-108">Attributes</span></span>  

 <span data-ttu-id="c4ad2-109">なし。</span><span class="sxs-lookup"><span data-stu-id="c4ad2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4ad2-110">子要素</span><span class="sxs-lookup"><span data-stu-id="c4ad2-110">Child Elements</span></span>  
  
|<span data-ttu-id="c4ad2-111">要素</span><span class="sxs-lookup"><span data-stu-id="c4ad2-111">Element</span></span>|<span data-ttu-id="c4ad2-112">説明</span><span class="sxs-lookup"><span data-stu-id="c4ad2-112">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="c4ad2-113">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="c4ad2-113">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4ad2-114">親要素</span><span class="sxs-lookup"><span data-stu-id="c4ad2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c4ad2-115">要素</span><span class="sxs-lookup"><span data-stu-id="c4ad2-115">Element</span></span>|<span data-ttu-id="c4ad2-116">説明</span><span class="sxs-lookup"><span data-stu-id="c4ad2-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="c4ad2-117">**ActivityDefinitionId** プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="c4ad2-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4ad2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4ad2-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c4ad2-119">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="c4ad2-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c4ad2-120">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="c4ad2-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
