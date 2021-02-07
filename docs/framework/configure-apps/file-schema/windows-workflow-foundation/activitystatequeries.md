---
description: '詳細情報: <activityStateQueries>'
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: ad324d88c481016d85b8e58ccc0857b7773d8328
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748961"
---
# \<activityStateQueries>

<span data-ttu-id="cf251-102">ワークフロー インスタンスを構成するアクティビティのライフサイクルの変化を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="cf251-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="cf251-103">たとえば、ワークフローインスタンス内で "電子メールの送信" アクティビティが完了するたびに追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="cf251-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="cf251-104">追跡参加要素がアクティビティ状態レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="cf251-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="cf251-105">定期受信可能な状態は ActivityStates で指定します。</span><span class="sxs-lookup"><span data-stu-id="cf251-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="cf251-106">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf251-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="cf251-107">構文</span><span class="sxs-lookup"><span data-stu-id="cf251-107">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf251-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cf251-108">Attributes and Elements</span></span>  

 <span data-ttu-id="cf251-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf251-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf251-110">属性</span><span class="sxs-lookup"><span data-stu-id="cf251-110">Attributes</span></span>  

 <span data-ttu-id="cf251-111">なし。</span><span class="sxs-lookup"><span data-stu-id="cf251-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf251-112">子要素</span><span class="sxs-lookup"><span data-stu-id="cf251-112">Child Elements</span></span>  
  
|<span data-ttu-id="cf251-113">要素</span><span class="sxs-lookup"><span data-stu-id="cf251-113">Element</span></span>|<span data-ttu-id="cf251-114">説明</span><span class="sxs-lookup"><span data-stu-id="cf251-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="cf251-115">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="cf251-115">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="cf251-116">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="cf251-116">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf251-117">親要素</span><span class="sxs-lookup"><span data-stu-id="cf251-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cf251-118">要素</span><span class="sxs-lookup"><span data-stu-id="cf251-118">Element</span></span>|<span data-ttu-id="cf251-119">説明</span><span class="sxs-lookup"><span data-stu-id="cf251-119">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="cf251-120">**ActivityDefinitionId** プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="cf251-120">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf251-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf251-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cf251-122">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="cf251-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cf251-123">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="cf251-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
