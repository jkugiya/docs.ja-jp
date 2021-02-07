---
description: '詳細情報: 1011-ScheduleExecuteActivityWorkItem'
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 81010390de2ad01ec3063f2ac89608b97dcb713e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703355"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="ce9b2-103">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="ce9b2-103">1011 - ScheduleExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="ce9b2-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ce9b2-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce9b2-105">id</span><span class="sxs-lookup"><span data-stu-id="ce9b2-105">ID</span></span>|<span data-ttu-id="ce9b2-106">1011</span><span class="sxs-lookup"><span data-stu-id="ce9b2-106">1011</span></span>|  
|<span data-ttu-id="ce9b2-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="ce9b2-107">Keywords</span></span>|<span data-ttu-id="ce9b2-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ce9b2-108">WFRuntime</span></span>|  
|<span data-ttu-id="ce9b2-109">Level</span><span class="sxs-lookup"><span data-stu-id="ce9b2-109">Level</span></span>|<span data-ttu-id="ce9b2-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="ce9b2-110">Verbose</span></span>|  
|<span data-ttu-id="ce9b2-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="ce9b2-111">Channel</span></span>|<span data-ttu-id="ce9b2-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ce9b2-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ce9b2-113">説明</span><span class="sxs-lookup"><span data-stu-id="ce9b2-113">Description</span></span>  

 <span data-ttu-id="ce9b2-114">ExecuteActivityWorkItem がスケジュールされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-114">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ce9b2-115">Message</span><span class="sxs-lookup"><span data-stu-id="ce9b2-115">Message</span></span>  

 <span data-ttu-id="ce9b2-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して ExecuteActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-116">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ce9b2-117">詳細</span><span class="sxs-lookup"><span data-stu-id="ce9b2-117">Details</span></span>  
  
|<span data-ttu-id="ce9b2-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ce9b2-118">Data Item Name</span></span>|<span data-ttu-id="ce9b2-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ce9b2-119">Data Item Type</span></span>|<span data-ttu-id="ce9b2-120">説明</span><span class="sxs-lookup"><span data-stu-id="ce9b2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ce9b2-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="ce9b2-121">Activity</span></span>|<span data-ttu-id="ce9b2-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce9b2-122">xs:string</span></span>|<span data-ttu-id="ce9b2-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="ce9b2-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ce9b2-124">DisplayName</span></span>|<span data-ttu-id="ce9b2-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce9b2-125">xs:string</span></span>|<span data-ttu-id="ce9b2-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="ce9b2-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ce9b2-127">InstanceId</span></span>|<span data-ttu-id="ce9b2-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce9b2-128">xs:string</span></span>|<span data-ttu-id="ce9b2-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ce9b2-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ce9b2-130">AppDomain</span></span>|<span data-ttu-id="ce9b2-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce9b2-131">xs:string</span></span>|<span data-ttu-id="ce9b2-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ce9b2-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
