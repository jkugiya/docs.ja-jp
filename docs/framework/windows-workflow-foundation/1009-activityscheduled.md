---
description: '詳細については、次を参照してください: 1009-ActivityScheduled'
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 80ee250955a03927fb9db2b1242d420be77a6df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755552"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="c9fcb-103">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="c9fcb-103">1009 - ActivityScheduled</span></span>

## <a name="properties"></a><span data-ttu-id="c9fcb-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c9fcb-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9fcb-105">id</span><span class="sxs-lookup"><span data-stu-id="c9fcb-105">ID</span></span>|<span data-ttu-id="c9fcb-106">1009</span><span class="sxs-lookup"><span data-stu-id="c9fcb-106">1009</span></span>|  
|<span data-ttu-id="c9fcb-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="c9fcb-107">Keywords</span></span>|<span data-ttu-id="c9fcb-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c9fcb-108">WFRuntime</span></span>|  
|<span data-ttu-id="c9fcb-109">Level</span><span class="sxs-lookup"><span data-stu-id="c9fcb-109">Level</span></span>|<span data-ttu-id="c9fcb-110">Information</span><span class="sxs-lookup"><span data-stu-id="c9fcb-110">Information</span></span>|  
|<span data-ttu-id="c9fcb-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="c9fcb-111">Channel</span></span>|<span data-ttu-id="c9fcb-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c9fcb-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c9fcb-113">説明</span><span class="sxs-lookup"><span data-stu-id="c9fcb-113">Description</span></span>  

 <span data-ttu-id="c9fcb-114">アクティビティの実行がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c9fcb-114">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c9fcb-115">Message</span><span class="sxs-lookup"><span data-stu-id="c9fcb-115">Message</span></span>  

 <span data-ttu-id="c9fcb-116">Parent Activity '%1'、DisplayName: '%2'、InstanceId: '%3' scheduled child Activity '%4'、DisplayName: '%5'、InstanceId: '%6'。</span><span class="sxs-lookup"><span data-stu-id="c9fcb-116">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c9fcb-117">詳細</span><span class="sxs-lookup"><span data-stu-id="c9fcb-117">Details</span></span>  
  
|<span data-ttu-id="c9fcb-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c9fcb-118">Data Item Name</span></span>|<span data-ttu-id="c9fcb-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c9fcb-119">Data Item Type</span></span>|<span data-ttu-id="c9fcb-120">説明</span><span class="sxs-lookup"><span data-stu-id="c9fcb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c9fcb-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="c9fcb-121">ParentActivity</span></span>|<span data-ttu-id="c9fcb-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9fcb-122">xs:string</span></span>|<span data-ttu-id="c9fcb-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="c9fcb-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="c9fcb-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="c9fcb-124">ParentDisplayName</span></span>|<span data-ttu-id="c9fcb-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9fcb-125">xs:string</span></span>|<span data-ttu-id="c9fcb-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="c9fcb-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="c9fcb-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="c9fcb-127">ParentInstanceId</span></span>|<span data-ttu-id="c9fcb-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9fcb-128">xs:string</span></span>|<span data-ttu-id="c9fcb-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="c9fcb-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="c9fcb-130">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="c9fcb-130">ChildActivity</span></span>|<span data-ttu-id="c9fcb-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9fcb-131">xs:string</span></span>|<span data-ttu-id="c9fcb-132">スケジュール済みの子アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="c9fcb-132">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c9fcb-133">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="c9fcb-133">ChildDisplayName</span></span>|<span data-ttu-id="c9fcb-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9fcb-134">xs:string</span></span>|<span data-ttu-id="c9fcb-135">スケジュール済みの子アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="c9fcb-135">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c9fcb-136">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="c9fcb-136">ChildInstanceId</span></span>|<span data-ttu-id="c9fcb-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9fcb-137">xs:string</span></span>|<span data-ttu-id="c9fcb-138">スケジュール済み子アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="c9fcb-138">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c9fcb-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c9fcb-139">AppDomain</span></span>|<span data-ttu-id="c9fcb-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9fcb-140">xs:string</span></span>|<span data-ttu-id="c9fcb-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c9fcb-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
