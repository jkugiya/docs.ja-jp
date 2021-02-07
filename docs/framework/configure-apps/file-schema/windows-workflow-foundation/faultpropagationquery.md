---
description: '詳細情報: <faultPropagationQuery>'
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 08786bfa66d74f5f29353c4d6a86a2abd34df8f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748701"
---
# \<faultPropagationQuery>

<span data-ttu-id="e403f-102">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="e403f-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e403f-103">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="e403f-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e403f-104">1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e403f-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e403f-105">追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="e403f-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="e403f-106">追跡プロファイルのクエリの詳細については、「 [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e403f-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**

## <a name="syntax"></a><span data-ttu-id="e403f-107">構文</span><span class="sxs-lookup"><span data-stu-id="e403f-107">Syntax</span></span>

```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e403f-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e403f-108">Attributes and Elements</span></span>

<span data-ttu-id="e403f-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e403f-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e403f-110">属性</span><span class="sxs-lookup"><span data-stu-id="e403f-110">Attributes</span></span>

|<span data-ttu-id="e403f-111">属性</span><span class="sxs-lookup"><span data-stu-id="e403f-111">Attribute</span></span>|<span data-ttu-id="e403f-112">説明</span><span class="sxs-lookup"><span data-stu-id="e403f-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="e403f-113">activityName</span><span class="sxs-lookup"><span data-stu-id="e403f-113">activityName</span></span>|<span data-ttu-id="e403f-114">エラーを伝達したエラーハンドラーアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="e403f-114">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="e403f-115">既定値は \* で、すべてのアクティビティについてエラー伝達レコードが返されることを示します。</span><span class="sxs-lookup"><span data-stu-id="e403f-115">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="e403f-116">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="e403f-116">faultHandlerActivityName</span></span>|<span data-ttu-id="e403f-117">エラーの原因となったアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="e403f-117">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e403f-118">子要素</span><span class="sxs-lookup"><span data-stu-id="e403f-118">Child Elements</span></span>

<span data-ttu-id="e403f-119">なし。</span><span class="sxs-lookup"><span data-stu-id="e403f-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e403f-120">親要素</span><span class="sxs-lookup"><span data-stu-id="e403f-120">Parent Elements</span></span>

|<span data-ttu-id="e403f-121">要素</span><span class="sxs-lookup"><span data-stu-id="e403f-121">Element</span></span>|<span data-ttu-id="e403f-122">説明</span><span class="sxs-lookup"><span data-stu-id="e403f-122">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="e403f-123">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="e403f-123">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e403f-124">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="e403f-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e403f-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e403f-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e403f-126">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="e403f-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e403f-127">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="e403f-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
