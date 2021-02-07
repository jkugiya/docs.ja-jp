---
description: '詳細情報: 115-WorkflowInstanceAbortedRecordWithId'
title: 115 - WorkflowInstanceAbortedRecordWithId
ms.date: 03/30/2017
ms.assetid: 0293dd4e-e6ae-473a-b3d6-c2d38f9bd875
ms.openlocfilehash: 6d9eb387ba61a646cbf1423d01175b0230272ca5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755435"
---
# <a name="115---workflowinstanceabortedrecordwithid"></a><span data-ttu-id="709b2-103">115 - WorkflowInstanceAbortedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="709b2-103">115 - WorkflowInstanceAbortedRecordWithId</span></span>

## <a name="properties"></a><span data-ttu-id="709b2-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="709b2-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="709b2-105">id</span><span class="sxs-lookup"><span data-stu-id="709b2-105">ID</span></span>|<span data-ttu-id="709b2-106">115</span><span class="sxs-lookup"><span data-stu-id="709b2-106">115</span></span>|  
|<span data-ttu-id="709b2-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="709b2-107">Keywords</span></span>|<span data-ttu-id="709b2-108">HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="709b2-108">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="709b2-109">Level</span><span class="sxs-lookup"><span data-stu-id="709b2-109">Level</span></span>|<span data-ttu-id="709b2-110">警告</span><span class="sxs-lookup"><span data-stu-id="709b2-110">Warning</span></span>|  
|<span data-ttu-id="709b2-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="709b2-111">Channel</span></span>|<span data-ttu-id="709b2-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="709b2-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="709b2-113">説明</span><span class="sxs-lookup"><span data-stu-id="709b2-113">Description</span></span>  

 <span data-ttu-id="709b2-114">このイベントは、ワークフロー インスタンスが WorkflowInstanceAbortedRecord を生成したときに、ETW 追跡参加要素によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="709b2-114">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceAbortedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="709b2-115">Message</span><span class="sxs-lookup"><span data-stu-id="709b2-115">Message</span></span>  

 <span data-ttu-id="709b2-116">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="709b2-116">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="709b2-117">詳細</span><span class="sxs-lookup"><span data-stu-id="709b2-117">Details</span></span>  
  
|<span data-ttu-id="709b2-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="709b2-118">Data Item Name</span></span>|<span data-ttu-id="709b2-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="709b2-119">Data Item Type</span></span>|<span data-ttu-id="709b2-120">説明</span><span class="sxs-lookup"><span data-stu-id="709b2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="709b2-121">InstanceId</span><span class="sxs-lookup"><span data-stu-id="709b2-121">InstanceId</span></span>|<span data-ttu-id="709b2-122">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="709b2-122">xs:GUID</span></span>|<span data-ttu-id="709b2-123">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="709b2-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="709b2-124">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="709b2-124">RecordNumber</span></span>|<span data-ttu-id="709b2-125">xs:long</span><span class="sxs-lookup"><span data-stu-id="709b2-125">xs:long</span></span>|<span data-ttu-id="709b2-126">生成されたレコードのシーケンス番号</span><span class="sxs-lookup"><span data-stu-id="709b2-126">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="709b2-127">EventTime</span><span class="sxs-lookup"><span data-stu-id="709b2-127">EventTime</span></span>|<span data-ttu-id="709b2-128">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="709b2-128">xs:dateTime</span></span>|<span data-ttu-id="709b2-129">イベントの生成時刻 (UTC)</span><span class="sxs-lookup"><span data-stu-id="709b2-129">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="709b2-130">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="709b2-130">ActivityDefinitionId</span></span>|<span data-ttu-id="709b2-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="709b2-131">xs:string</span></span>|<span data-ttu-id="709b2-132">ワークフローのルート アクティビティの名前</span><span class="sxs-lookup"><span data-stu-id="709b2-132">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="709b2-133">State</span><span class="sxs-lookup"><span data-stu-id="709b2-133">State</span></span>|<span data-ttu-id="709b2-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="709b2-134">xs:string</span></span>|<span data-ttu-id="709b2-135">ワークフローの現在の状態。</span><span class="sxs-lookup"><span data-stu-id="709b2-135">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="709b2-136">注釈</span><span class="sxs-lookup"><span data-stu-id="709b2-136">Annotations</span></span>|<span data-ttu-id="709b2-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="709b2-137">xs:string</span></span>|<span data-ttu-id="709b2-138">このイベントに追加された注釈。</span><span class="sxs-lookup"><span data-stu-id="709b2-138">The annotations that were added to this event.</span></span> <span data-ttu-id="709b2-139">値は、annotationValue 形式の xml 要素に格納され \<items> \< item name = "annotationName" type="System.String"> \</item> \</items> ます。</span><span class="sxs-lookup"><span data-stu-id="709b2-139">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="709b2-140">注釈が指定されていない場合、文字列にはが含まれ \<items/> ます。</span><span class="sxs-lookup"><span data-stu-id="709b2-140">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="709b2-141">ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。</span><span class="sxs-lookup"><span data-stu-id="709b2-141">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="709b2-142">イベントのサイズが ETW の制限を超えると、注釈が削除され、注釈の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items></span><span class="sxs-lookup"><span data-stu-id="709b2-142">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="709b2-143">ProfileName</span><span class="sxs-lookup"><span data-stu-id="709b2-143">ProfileName</span></span>|<span data-ttu-id="709b2-144">xs:string</span><span class="sxs-lookup"><span data-stu-id="709b2-144">xs:string</span></span>|<span data-ttu-id="709b2-145">このイベントを生成した追跡プロファイルの名前</span><span class="sxs-lookup"><span data-stu-id="709b2-145">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="709b2-146">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="709b2-146">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="709b2-147">xs:string</span><span class="sxs-lookup"><span data-stu-id="709b2-147">xs:string</span></span>|<span data-ttu-id="709b2-148">ワークフロー定義 ID</span><span class="sxs-lookup"><span data-stu-id="709b2-148">The workflow definition id</span></span>|  
|<span data-ttu-id="709b2-149">AppDomain</span><span class="sxs-lookup"><span data-stu-id="709b2-149">AppDomain</span></span>|<span data-ttu-id="709b2-150">xs:string</span><span class="sxs-lookup"><span data-stu-id="709b2-150">xs:string</span></span>|<span data-ttu-id="709b2-151">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="709b2-151">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
