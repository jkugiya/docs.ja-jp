---
description: '詳細情報: 116-WorkflowInstanceSuspendedRecordWithId'
title: 116 - WorkflowInstanceSuspendedRecordWithId
ms.date: 03/30/2017
ms.assetid: 38232c03-6139-4494-a020-79bc83eb9dce
ms.openlocfilehash: 32746777d32ed0c8320d53da9f73ddb8d55a5573
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703251"
---
# <a name="116---workflowinstancesuspendedrecordwithid"></a><span data-ttu-id="bdd94-103">116 - WorkflowInstanceSuspendedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="bdd94-103">116 - WorkflowInstanceSuspendedRecordWithId</span></span>

## <a name="properties"></a><span data-ttu-id="bdd94-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bdd94-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bdd94-105">id</span><span class="sxs-lookup"><span data-stu-id="bdd94-105">ID</span></span>|<span data-ttu-id="bdd94-106">116</span><span class="sxs-lookup"><span data-stu-id="bdd94-106">116</span></span>|  
|<span data-ttu-id="bdd94-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="bdd94-107">Keywords</span></span>|<span data-ttu-id="bdd94-108">HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="bdd94-108">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="bdd94-109">Level</span><span class="sxs-lookup"><span data-stu-id="bdd94-109">Level</span></span>|<span data-ttu-id="bdd94-110">Information</span><span class="sxs-lookup"><span data-stu-id="bdd94-110">Information</span></span>|  
|<span data-ttu-id="bdd94-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="bdd94-111">Channel</span></span>|<span data-ttu-id="bdd94-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="bdd94-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bdd94-113">説明</span><span class="sxs-lookup"><span data-stu-id="bdd94-113">Description</span></span>  

 <span data-ttu-id="bdd94-114">このイベントは、ワークフロー インスタンスが WorkflowInstanceSuspended Record を生成したときに、ETW 追跡参加要素によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="bdd94-114">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceSuspended Record.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bdd94-115">Message</span><span class="sxs-lookup"><span data-stu-id="bdd94-115">Message</span></span>  

 <span data-ttu-id="bdd94-116">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="bdd94-116">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="bdd94-117">詳細</span><span class="sxs-lookup"><span data-stu-id="bdd94-117">Details</span></span>  
  
|<span data-ttu-id="bdd94-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bdd94-118">Data Item Name</span></span>|<span data-ttu-id="bdd94-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bdd94-119">Data Item Type</span></span>|<span data-ttu-id="bdd94-120">説明</span><span class="sxs-lookup"><span data-stu-id="bdd94-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bdd94-121">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bdd94-121">InstanceId</span></span>|<span data-ttu-id="bdd94-122">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="bdd94-122">xs:GUID</span></span>|<span data-ttu-id="bdd94-123">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="bdd94-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="bdd94-124">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="bdd94-124">RecordNumber</span></span>|<span data-ttu-id="bdd94-125">xs:long</span><span class="sxs-lookup"><span data-stu-id="bdd94-125">xs:long</span></span>|<span data-ttu-id="bdd94-126">生成されたレコードのシーケンス番号</span><span class="sxs-lookup"><span data-stu-id="bdd94-126">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="bdd94-127">EventTime</span><span class="sxs-lookup"><span data-stu-id="bdd94-127">EventTime</span></span>|<span data-ttu-id="bdd94-128">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="bdd94-128">xs:dateTime</span></span>|<span data-ttu-id="bdd94-129">イベントの生成時刻 (UTC)</span><span class="sxs-lookup"><span data-stu-id="bdd94-129">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="bdd94-130">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="bdd94-130">ActivityDefinitionId</span></span>|<span data-ttu-id="bdd94-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdd94-131">xs:string</span></span>|<span data-ttu-id="bdd94-132">ワークフローのルート アクティビティの名前</span><span class="sxs-lookup"><span data-stu-id="bdd94-132">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="bdd94-133">State</span><span class="sxs-lookup"><span data-stu-id="bdd94-133">State</span></span>|<span data-ttu-id="bdd94-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdd94-134">xs:string</span></span>|<span data-ttu-id="bdd94-135">ワークフローの現在の状態。</span><span class="sxs-lookup"><span data-stu-id="bdd94-135">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="bdd94-136">注釈</span><span class="sxs-lookup"><span data-stu-id="bdd94-136">Annotations</span></span>|<span data-ttu-id="bdd94-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdd94-137">xs:string</span></span>|<span data-ttu-id="bdd94-138">このイベントに追加された注釈。</span><span class="sxs-lookup"><span data-stu-id="bdd94-138">The annotations that were added to this event.</span></span> <span data-ttu-id="bdd94-139">値は、annotationValue 形式の xml 要素に格納され \<items> \< item name = "annotationName" type="System.String"> \</item> \</items> ます。</span><span class="sxs-lookup"><span data-stu-id="bdd94-139">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="bdd94-140">注釈が指定されていない場合、文字列にはが含まれ \<items/> ます。</span><span class="sxs-lookup"><span data-stu-id="bdd94-140">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="bdd94-141">ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。</span><span class="sxs-lookup"><span data-stu-id="bdd94-141">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="bdd94-142">イベントのサイズが ETW の制限を超えると、注釈が削除され、注釈の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items></span><span class="sxs-lookup"><span data-stu-id="bdd94-142">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="bdd94-143">ProfileName</span><span class="sxs-lookup"><span data-stu-id="bdd94-143">ProfileName</span></span>|<span data-ttu-id="bdd94-144">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdd94-144">xs:string</span></span>|<span data-ttu-id="bdd94-145">このイベントを生成した追跡プロファイルの名前</span><span class="sxs-lookup"><span data-stu-id="bdd94-145">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="bdd94-146">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="bdd94-146">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="bdd94-147">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdd94-147">xs:string</span></span>|<span data-ttu-id="bdd94-148">ワークフロー定義 ID</span><span class="sxs-lookup"><span data-stu-id="bdd94-148">The workflow definition id</span></span>|  
|<span data-ttu-id="bdd94-149">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bdd94-149">AppDomain</span></span>|<span data-ttu-id="bdd94-150">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdd94-150">xs:string</span></span>|<span data-ttu-id="bdd94-151">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bdd94-151">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
