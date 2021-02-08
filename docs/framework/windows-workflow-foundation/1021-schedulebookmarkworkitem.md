---
description: '詳細情報: 1021-ScheduleBookmarkWorkItem'
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: 5153d2e90a75bab90c76ee8786dc82d4ddac19a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792818"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="8e64c-103">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="8e64c-103">1021 - ScheduleBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="8e64c-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8e64c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e64c-105">id</span><span class="sxs-lookup"><span data-stu-id="8e64c-105">ID</span></span>|<span data-ttu-id="8e64c-106">1021</span><span class="sxs-lookup"><span data-stu-id="8e64c-106">1021</span></span>|  
|<span data-ttu-id="8e64c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="8e64c-107">Keywords</span></span>|<span data-ttu-id="8e64c-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8e64c-108">WFRuntime</span></span>|  
|<span data-ttu-id="8e64c-109">Level</span><span class="sxs-lookup"><span data-stu-id="8e64c-109">Level</span></span>|<span data-ttu-id="8e64c-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="8e64c-110">Verbose</span></span>|  
|<span data-ttu-id="8e64c-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="8e64c-111">Channel</span></span>|<span data-ttu-id="8e64c-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8e64c-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8e64c-113">説明</span><span class="sxs-lookup"><span data-stu-id="8e64c-113">Description</span></span>  

 <span data-ttu-id="8e64c-114">BookmarkWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="8e64c-114">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8e64c-115">Message</span><span class="sxs-lookup"><span data-stu-id="8e64c-115">Message</span></span>  

 <span data-ttu-id="8e64c-116">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' に対して BookmarkWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="8e64c-116">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="8e64c-117">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="8e64c-117">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8e64c-118">詳細</span><span class="sxs-lookup"><span data-stu-id="8e64c-118">Details</span></span>  
  
|<span data-ttu-id="8e64c-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8e64c-119">Data Item Name</span></span>|<span data-ttu-id="8e64c-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8e64c-120">Data Item Type</span></span>|<span data-ttu-id="8e64c-121">説明</span><span class="sxs-lookup"><span data-stu-id="8e64c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8e64c-122">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="8e64c-122">Activity</span></span>|<span data-ttu-id="8e64c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e64c-123">xs:string</span></span>|<span data-ttu-id="8e64c-124">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="8e64c-124">The type name of the activity.</span></span>|  
|<span data-ttu-id="8e64c-125">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8e64c-125">DisplayName</span></span>|<span data-ttu-id="8e64c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e64c-126">xs:string</span></span>|<span data-ttu-id="8e64c-127">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="8e64c-127">The display name of the activity.</span></span>|  
|<span data-ttu-id="8e64c-128">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8e64c-128">InstanceId</span></span>|<span data-ttu-id="8e64c-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e64c-129">xs:string</span></span>|<span data-ttu-id="8e64c-130">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="8e64c-130">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8e64c-131">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="8e64c-131">BookmarkName</span></span>|<span data-ttu-id="8e64c-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e64c-132">xs:string</span></span>|<span data-ttu-id="8e64c-133">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="8e64c-133">The name of the bookmark.</span></span>|  
|<span data-ttu-id="8e64c-134">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="8e64c-134">BookmarkScope</span></span>|<span data-ttu-id="8e64c-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e64c-135">xs:string</span></span>|<span data-ttu-id="8e64c-136">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="8e64c-136">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="8e64c-137">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8e64c-137">AppDomain</span></span>|<span data-ttu-id="8e64c-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e64c-138">xs:string</span></span>|<span data-ttu-id="8e64c-139">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8e64c-139">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
