---
description: 詳細については、「1010-ActivityCompleted」を参照してください。
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: c72339449b94b0ea5d6d8fa227b606cc25c29704
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755539"
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="94bcd-103">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="94bcd-103">1010 - ActivityCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="94bcd-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="94bcd-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94bcd-105">id</span><span class="sxs-lookup"><span data-stu-id="94bcd-105">ID</span></span>|<span data-ttu-id="94bcd-106">1010</span><span class="sxs-lookup"><span data-stu-id="94bcd-106">1010</span></span>|  
|<span data-ttu-id="94bcd-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="94bcd-107">Keywords</span></span>|<span data-ttu-id="94bcd-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="94bcd-108">WFRuntime</span></span>|  
|<span data-ttu-id="94bcd-109">Level</span><span class="sxs-lookup"><span data-stu-id="94bcd-109">Level</span></span>|<span data-ttu-id="94bcd-110">Information</span><span class="sxs-lookup"><span data-stu-id="94bcd-110">Information</span></span>|  
|<span data-ttu-id="94bcd-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="94bcd-111">Channel</span></span>|<span data-ttu-id="94bcd-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="94bcd-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="94bcd-113">説明</span><span class="sxs-lookup"><span data-stu-id="94bcd-113">Description</span></span>  

 <span data-ttu-id="94bcd-114">アクティビティが実行を完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="94bcd-114">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="94bcd-115">Message</span><span class="sxs-lookup"><span data-stu-id="94bcd-115">Message</span></span>  

 <span data-ttu-id="94bcd-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' が状態 '%4' で完了しました。</span><span class="sxs-lookup"><span data-stu-id="94bcd-116">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="94bcd-117">詳細</span><span class="sxs-lookup"><span data-stu-id="94bcd-117">Details</span></span>  
  
|<span data-ttu-id="94bcd-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="94bcd-118">Data Item Name</span></span>|<span data-ttu-id="94bcd-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="94bcd-119">Data Item Type</span></span>|<span data-ttu-id="94bcd-120">説明</span><span class="sxs-lookup"><span data-stu-id="94bcd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="94bcd-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="94bcd-121">Activity</span></span>|<span data-ttu-id="94bcd-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="94bcd-122">xs:string</span></span>|<span data-ttu-id="94bcd-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="94bcd-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="94bcd-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="94bcd-124">DisplayName</span></span>|<span data-ttu-id="94bcd-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="94bcd-125">xs:string</span></span>|<span data-ttu-id="94bcd-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="94bcd-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="94bcd-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="94bcd-127">InstanceId</span></span>|<span data-ttu-id="94bcd-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="94bcd-128">xs:string</span></span>|<span data-ttu-id="94bcd-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="94bcd-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="94bcd-130">State</span><span class="sxs-lookup"><span data-stu-id="94bcd-130">State</span></span>|<span data-ttu-id="94bcd-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="94bcd-131">xs:string</span></span>|<span data-ttu-id="94bcd-132">アクティビティの状態。</span><span class="sxs-lookup"><span data-stu-id="94bcd-132">The state of the activity.</span></span>|  
|<span data-ttu-id="94bcd-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="94bcd-133">AppDomain</span></span>|<span data-ttu-id="94bcd-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="94bcd-134">xs:string</span></span>|<span data-ttu-id="94bcd-135">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="94bcd-135">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
