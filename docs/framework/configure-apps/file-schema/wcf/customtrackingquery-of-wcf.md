---
description: 詳細については、「WCF」を参照してください。 <customTrackingQuery>
title: <customTrackingQuery> WCF の
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 3eac26ee94a95b480d743e3c6ec554a84b8747a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754460"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="0ce7f-103">\<customTrackingQuery> WCF の</span><span class="sxs-lookup"><span data-stu-id="0ce7f-103">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="0ce7f-104">コードアクティビティで定義するイベントを追跡するために使用されるクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="0ce7f-104">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="0ce7f-105">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="0ce7f-105">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="0ce7f-106">追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ce7f-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="0ce7f-107">構文</span><span class="sxs-lookup"><span data-stu-id="0ce7f-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ce7f-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="0ce7f-108">Attributes and elements</span></span>  

<span data-ttu-id="0ce7f-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0ce7f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ce7f-110">属性</span><span class="sxs-lookup"><span data-stu-id="0ce7f-110">Attributes</span></span>  
  
|<span data-ttu-id="0ce7f-111">属性</span><span class="sxs-lookup"><span data-stu-id="0ce7f-111">Attribute</span></span>|<span data-ttu-id="0ce7f-112">説明</span><span class="sxs-lookup"><span data-stu-id="0ce7f-112">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="0ce7f-113">追跡レコードを生成したアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="0ce7f-113">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="0ce7f-114">生成されたカスタム追跡レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="0ce7f-114">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ce7f-115">子要素</span><span class="sxs-lookup"><span data-stu-id="0ce7f-115">Child elements</span></span>

<span data-ttu-id="0ce7f-116">なし。</span><span class="sxs-lookup"><span data-stu-id="0ce7f-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0ce7f-117">親要素</span><span class="sxs-lookup"><span data-stu-id="0ce7f-117">Parent elements</span></span>

|<span data-ttu-id="0ce7f-118">要素</span><span class="sxs-lookup"><span data-stu-id="0ce7f-118">Element</span></span>|<span data-ttu-id="0ce7f-119">説明</span><span class="sxs-lookup"><span data-stu-id="0ce7f-119">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="0ce7f-120">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="0ce7f-120">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="0ce7f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ce7f-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0ce7f-122">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="0ce7f-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0ce7f-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="0ce7f-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
