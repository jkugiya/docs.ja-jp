---
description: '詳細情報: <variable>'
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 187aa0b1ab0494a9bad759c504b804580a60553e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697999"
---
# \<variable>

<span data-ttu-id="db8fe-102">このアクティビティ クエリに関連付けられている変数のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="db8fe-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="db8fe-103">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db8fe-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<variables>**](variables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variable>**  
  
## <a name="syntax"></a><span data-ttu-id="db8fe-104">構文</span><span class="sxs-lookup"><span data-stu-id="db8fe-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db8fe-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="db8fe-105">Attributes and Elements</span></span>  

 <span data-ttu-id="db8fe-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="db8fe-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db8fe-107">属性</span><span class="sxs-lookup"><span data-stu-id="db8fe-107">Attributes</span></span>  
  
|<span data-ttu-id="db8fe-108">属性</span><span class="sxs-lookup"><span data-stu-id="db8fe-108">Attribute</span></span>|<span data-ttu-id="db8fe-109">説明</span><span class="sxs-lookup"><span data-stu-id="db8fe-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db8fe-110">name</span><span class="sxs-lookup"><span data-stu-id="db8fe-110">name</span></span>|<span data-ttu-id="db8fe-111">変数の名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="db8fe-111">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db8fe-112">子要素</span><span class="sxs-lookup"><span data-stu-id="db8fe-112">Child Elements</span></span>  

 <span data-ttu-id="db8fe-113">なし。</span><span class="sxs-lookup"><span data-stu-id="db8fe-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db8fe-114">親要素</span><span class="sxs-lookup"><span data-stu-id="db8fe-114">Parent Elements</span></span>  
  
|<span data-ttu-id="db8fe-115">要素</span><span class="sxs-lookup"><span data-stu-id="db8fe-115">Element</span></span>|<span data-ttu-id="db8fe-116">説明</span><span class="sxs-lookup"><span data-stu-id="db8fe-116">Description</span></span>|  
|-------------|-----------------|  
|[\<variable>](variable.md)|<span data-ttu-id="db8fe-117">アクティビティ状態クエリに関連付けられている変数。</span><span class="sxs-lookup"><span data-stu-id="db8fe-117">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db8fe-118">解説</span><span class="sxs-lookup"><span data-stu-id="db8fe-118">Remarks</span></span>  

 <span data-ttu-id="db8fe-119">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="db8fe-119">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="db8fe-120">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="db8fe-120">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="db8fe-121">、、およびの各要素を使用して、 [\<arguments>](arguments.md) [\<states>](states.md) [\<states>](states.md) ワークフロー内の任意のアクティビティから任意の変数または引数を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="db8fe-121">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="db8fe-122">次の例は、アクティビティの `Closed` 追跡レコードが生成されたときに変数と引数を抽出するアクティビティ状態クエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="db8fe-122">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="db8fe-123">変数と引数は、ActivityStateRecord でのみ抽出できるため、を使用して追跡プロファイル内でサブスクライブされ [\<activityStateQuery>](activitystatequery.md) ます。</span><span class="sxs-lookup"><span data-stu-id="db8fe-123">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db8fe-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="db8fe-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="db8fe-125">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="db8fe-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="db8fe-126">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="db8fe-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
