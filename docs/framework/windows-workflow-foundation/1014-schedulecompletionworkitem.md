---
description: '詳細情報: 1014-ScheduleCompletionWorkItem'
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 85bbd9b749c1dd34d026d90d708ea7f880665fbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792935"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="19a01-103">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="19a01-103">1014 - ScheduleCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="19a01-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="19a01-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19a01-105">id</span><span class="sxs-lookup"><span data-stu-id="19a01-105">ID</span></span>|<span data-ttu-id="19a01-106">1014</span><span class="sxs-lookup"><span data-stu-id="19a01-106">1014</span></span>|  
|<span data-ttu-id="19a01-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="19a01-107">Keywords</span></span>|<span data-ttu-id="19a01-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="19a01-108">WFRuntime</span></span>|  
|<span data-ttu-id="19a01-109">Level</span><span class="sxs-lookup"><span data-stu-id="19a01-109">Level</span></span>|<span data-ttu-id="19a01-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="19a01-110">Verbose</span></span>|  
|<span data-ttu-id="19a01-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="19a01-111">Channel</span></span>|<span data-ttu-id="19a01-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="19a01-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="19a01-113">説明</span><span class="sxs-lookup"><span data-stu-id="19a01-113">Description</span></span>  

 <span data-ttu-id="19a01-114">CompletionWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="19a01-114">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="19a01-115">Message</span><span class="sxs-lookup"><span data-stu-id="19a01-115">Message</span></span>  

 <span data-ttu-id="19a01-116">親アクティビティ ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' に対して、完了作業項目がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="19a01-116">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="19a01-117">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="19a01-117">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="19a01-118">詳細</span><span class="sxs-lookup"><span data-stu-id="19a01-118">Details</span></span>  
  
|<span data-ttu-id="19a01-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="19a01-119">Data Item Name</span></span>|<span data-ttu-id="19a01-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="19a01-120">Data Item Type</span></span>|<span data-ttu-id="19a01-121">説明</span><span class="sxs-lookup"><span data-stu-id="19a01-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="19a01-122">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="19a01-122">ParentActivity</span></span>|<span data-ttu-id="19a01-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="19a01-123">xs:string</span></span>|<span data-ttu-id="19a01-124">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="19a01-124">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="19a01-125">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="19a01-125">ParentDisplayName</span></span>|<span data-ttu-id="19a01-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="19a01-126">xs:string</span></span>|<span data-ttu-id="19a01-127">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="19a01-127">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="19a01-128">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="19a01-128">ParentInstanceId</span></span>|<span data-ttu-id="19a01-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="19a01-129">xs:string</span></span>|<span data-ttu-id="19a01-130">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="19a01-130">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="19a01-131">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="19a01-131">CompletedActivity</span></span>|<span data-ttu-id="19a01-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="19a01-132">xs:string</span></span>|<span data-ttu-id="19a01-133">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="19a01-133">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="19a01-134">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="19a01-134">CompletedActivityDisplayName</span></span>|<span data-ttu-id="19a01-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="19a01-135">xs:string</span></span>|<span data-ttu-id="19a01-136">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="19a01-136">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="19a01-137">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="19a01-137">CompletedActivityInstanceId</span></span>|<span data-ttu-id="19a01-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="19a01-138">xs:string</span></span>|<span data-ttu-id="19a01-139">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="19a01-139">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="19a01-140">AppDomain</span><span class="sxs-lookup"><span data-stu-id="19a01-140">AppDomain</span></span>|<span data-ttu-id="19a01-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="19a01-141">xs:string</span></span>|<span data-ttu-id="19a01-142">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="19a01-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
