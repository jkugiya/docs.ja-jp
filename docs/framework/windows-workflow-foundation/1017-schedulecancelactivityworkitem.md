---
description: '詳細情報: 1017-ScheduleCancelActivityWorkItem'
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 04dc4f663ceed1d7350dd14867e4926042bd11af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792896"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="64a9a-103">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="64a9a-103">1017 - ScheduleCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="64a9a-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="64a9a-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64a9a-105">id</span><span class="sxs-lookup"><span data-stu-id="64a9a-105">ID</span></span>|<span data-ttu-id="64a9a-106">1017</span><span class="sxs-lookup"><span data-stu-id="64a9a-106">1017</span></span>|  
|<span data-ttu-id="64a9a-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="64a9a-107">Keywords</span></span>|<span data-ttu-id="64a9a-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="64a9a-108">WFRuntime</span></span>|  
|<span data-ttu-id="64a9a-109">Level</span><span class="sxs-lookup"><span data-stu-id="64a9a-109">Level</span></span>|<span data-ttu-id="64a9a-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="64a9a-110">Verbose</span></span>|  
|<span data-ttu-id="64a9a-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="64a9a-111">Channel</span></span>|<span data-ttu-id="64a9a-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="64a9a-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="64a9a-113">説明</span><span class="sxs-lookup"><span data-stu-id="64a9a-113">Description</span></span>  

 <span data-ttu-id="64a9a-114">CancelActivityWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="64a9a-114">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="64a9a-115">Message</span><span class="sxs-lookup"><span data-stu-id="64a9a-115">Message</span></span>  

 <span data-ttu-id="64a9a-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して CancelActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="64a9a-116">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="64a9a-117">詳細</span><span class="sxs-lookup"><span data-stu-id="64a9a-117">Details</span></span>  
  
|<span data-ttu-id="64a9a-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="64a9a-118">Data Item Name</span></span>|<span data-ttu-id="64a9a-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="64a9a-119">Data Item Type</span></span>|<span data-ttu-id="64a9a-120">説明</span><span class="sxs-lookup"><span data-stu-id="64a9a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="64a9a-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="64a9a-121">Activity</span></span>|<span data-ttu-id="64a9a-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="64a9a-122">xs:string</span></span>|<span data-ttu-id="64a9a-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="64a9a-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="64a9a-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="64a9a-124">DisplayName</span></span>|<span data-ttu-id="64a9a-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="64a9a-125">xs:string</span></span>|<span data-ttu-id="64a9a-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="64a9a-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="64a9a-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="64a9a-127">InstanceId</span></span>|<span data-ttu-id="64a9a-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="64a9a-128">xs:string</span></span>|<span data-ttu-id="64a9a-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="64a9a-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="64a9a-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="64a9a-130">AppDomain</span></span>|<span data-ttu-id="64a9a-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="64a9a-131">xs:string</span></span>|<span data-ttu-id="64a9a-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="64a9a-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
