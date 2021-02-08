---
description: 詳細については <state> 、 <states>
title: <state> の <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 748044986143f182faa0edafb0cfe299a79a704e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781988"
---
# <a name="state-of-states"></a><span data-ttu-id="05d3a-103">\<state> の \<states></span><span class="sxs-lookup"><span data-stu-id="05d3a-103">\<state> of \<states></span></span>

<span data-ttu-id="05d3a-104">追跡レコードを生成する必要がある定期受信済みアクティビティの状態を含む構成要素。</span><span class="sxs-lookup"><span data-stu-id="05d3a-104">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="05d3a-105">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05d3a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="05d3a-106">構文</span><span class="sxs-lookup"><span data-stu-id="05d3a-106">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05d3a-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="05d3a-107">Attributes and Elements</span></span>  

 <span data-ttu-id="05d3a-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="05d3a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05d3a-109">属性</span><span class="sxs-lookup"><span data-stu-id="05d3a-109">Attributes</span></span>  
  
|<span data-ttu-id="05d3a-110">属性</span><span class="sxs-lookup"><span data-stu-id="05d3a-110">Attribute</span></span>|<span data-ttu-id="05d3a-111">説明</span><span class="sxs-lookup"><span data-stu-id="05d3a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05d3a-112">name</span><span class="sxs-lookup"><span data-stu-id="05d3a-112">name</span></span>|<span data-ttu-id="05d3a-113">追跡レコードを生成する必要がある定期受信済みアクティビティの状態を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="05d3a-113">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05d3a-114">子要素</span><span class="sxs-lookup"><span data-stu-id="05d3a-114">Child Elements</span></span>  

 <span data-ttu-id="05d3a-115">なし。</span><span class="sxs-lookup"><span data-stu-id="05d3a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05d3a-116">親要素</span><span class="sxs-lookup"><span data-stu-id="05d3a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="05d3a-117">要素</span><span class="sxs-lookup"><span data-stu-id="05d3a-117">Element</span></span>|<span data-ttu-id="05d3a-118">説明</span><span class="sxs-lookup"><span data-stu-id="05d3a-118">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-activitystatequery.md)|<span data-ttu-id="05d3a-119">追跡レコードを生成する必要がある定期受信済みアクティビティの状態を含む構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="05d3a-119">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05d3a-120">解説</span><span class="sxs-lookup"><span data-stu-id="05d3a-120">Remarks</span></span>  

 <span data-ttu-id="05d3a-121">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="05d3a-121">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="05d3a-122">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="05d3a-122">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="05d3a-123">、、およびの各要素を使用して、 [\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) ワークフロー内の任意のアクティビティから任意の変数または引数を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="05d3a-123">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="05d3a-124">次の例は、アクティビティの `Closed` 追跡レコードが生成されたときに変数と引数を抽出するアクティビティ状態クエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="05d3a-124">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="05d3a-125">変数と引数は、ActivityStateRecord でのみ抽出できるため、を使用して追跡プロファイル内でサブスクライブされ [\<activityStateQuery>](activitystatequery.md) ます。</span><span class="sxs-lookup"><span data-stu-id="05d3a-125">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05d3a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="05d3a-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="05d3a-127">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="05d3a-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="05d3a-128">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="05d3a-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
