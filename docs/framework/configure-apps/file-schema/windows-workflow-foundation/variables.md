---
description: '詳細情報: <variables>'
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: e77c4fb1d4d16a655cd1918bb9460177b7ff3266
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698012"
---
# \<variables>

<span data-ttu-id="90d83-102">このアクティビティ クエリに関連付けられている変数のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="90d83-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="90d83-103">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90d83-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variables>**  
  
## <a name="syntax"></a><span data-ttu-id="90d83-104">構文</span><span class="sxs-lookup"><span data-stu-id="90d83-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90d83-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="90d83-105">Attributes and Elements</span></span>  

 <span data-ttu-id="90d83-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="90d83-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90d83-107">属性</span><span class="sxs-lookup"><span data-stu-id="90d83-107">Attributes</span></span>  

 <span data-ttu-id="90d83-108">なし。</span><span class="sxs-lookup"><span data-stu-id="90d83-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90d83-109">子要素</span><span class="sxs-lookup"><span data-stu-id="90d83-109">Child Elements</span></span>  
  
|<span data-ttu-id="90d83-110">要素</span><span class="sxs-lookup"><span data-stu-id="90d83-110">Element</span></span>|<span data-ttu-id="90d83-111">説明</span><span class="sxs-lookup"><span data-stu-id="90d83-111">Description</span></span>|  
|-------------|-----------------|  
|[\<variable>](variable.md)|<span data-ttu-id="90d83-112">アクティビティ状態クエリに関連付けられている変数。</span><span class="sxs-lookup"><span data-stu-id="90d83-112">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90d83-113">親要素</span><span class="sxs-lookup"><span data-stu-id="90d83-113">Parent Elements</span></span>  
  
|<span data-ttu-id="90d83-114">要素</span><span class="sxs-lookup"><span data-stu-id="90d83-114">Element</span></span>|<span data-ttu-id="90d83-115">説明</span><span class="sxs-lookup"><span data-stu-id="90d83-115">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="90d83-116">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="90d83-116">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="90d83-117">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="90d83-117">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90d83-118">解説</span><span class="sxs-lookup"><span data-stu-id="90d83-118">Remarks</span></span>  

 <span data-ttu-id="90d83-119">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="90d83-119">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="90d83-120">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="90d83-120">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="90d83-121">、、およびの各要素を使用して、 [\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) ワークフロー内の任意のアクティビティから任意の変数または引数を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="90d83-121">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="90d83-122">次の例は、アクティビティの `Closed` 追跡レコードが生成されたときに変数と引数を抽出するアクティビティ状態クエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="90d83-122">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="90d83-123">変数と引数は、ActivityStateRecord でのみ抽出できるため、を使用して追跡プロファイル内でサブスクライブされ [\<activityStateQuery>](activitystatequery.md) ます。</span><span class="sxs-lookup"><span data-stu-id="90d83-123">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="90d83-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="90d83-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="90d83-125">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="90d83-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="90d83-126">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="90d83-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
