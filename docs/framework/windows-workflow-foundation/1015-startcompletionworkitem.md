---
description: '詳細について: 1015-Start補完作業項目'
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6c79a02b144aa1176eb1cb334c8430c8f0babc3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792922"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="83f99-103">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="83f99-103">1015 - StartCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="83f99-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="83f99-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="83f99-105">id</span><span class="sxs-lookup"><span data-stu-id="83f99-105">ID</span></span>|<span data-ttu-id="83f99-106">1015</span><span class="sxs-lookup"><span data-stu-id="83f99-106">1015</span></span>|  
|<span data-ttu-id="83f99-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="83f99-107">Keywords</span></span>|<span data-ttu-id="83f99-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="83f99-108">WFRuntime</span></span>|  
|<span data-ttu-id="83f99-109">Level</span><span class="sxs-lookup"><span data-stu-id="83f99-109">Level</span></span>|<span data-ttu-id="83f99-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="83f99-110">Verbose</span></span>|  
|<span data-ttu-id="83f99-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="83f99-111">Channel</span></span>|<span data-ttu-id="83f99-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="83f99-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="83f99-113">説明</span><span class="sxs-lookup"><span data-stu-id="83f99-113">Description</span></span>  

 <span data-ttu-id="83f99-114">CompletionWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="83f99-114">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="83f99-115">Message</span><span class="sxs-lookup"><span data-stu-id="83f99-115">Message</span></span>  

 <span data-ttu-id="83f99-116">親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="83f99-116">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="83f99-117">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="83f99-117">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="83f99-118">詳細</span><span class="sxs-lookup"><span data-stu-id="83f99-118">Details</span></span>  
  
|<span data-ttu-id="83f99-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="83f99-119">Data Item Name</span></span>|<span data-ttu-id="83f99-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="83f99-120">Data Item Type</span></span>|<span data-ttu-id="83f99-121">説明</span><span class="sxs-lookup"><span data-stu-id="83f99-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="83f99-122">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="83f99-122">ParentActivity</span></span>|<span data-ttu-id="83f99-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="83f99-123">xs:string</span></span>|<span data-ttu-id="83f99-124">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="83f99-124">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="83f99-125">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="83f99-125">ParentDisplayName</span></span>|<span data-ttu-id="83f99-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="83f99-126">xs:string</span></span>|<span data-ttu-id="83f99-127">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="83f99-127">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="83f99-128">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="83f99-128">ParentInstanceId</span></span>|<span data-ttu-id="83f99-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="83f99-129">xs:string</span></span>|<span data-ttu-id="83f99-130">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="83f99-130">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="83f99-131">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="83f99-131">CompletedActivity</span></span>|<span data-ttu-id="83f99-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="83f99-132">xs:string</span></span>|<span data-ttu-id="83f99-133">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="83f99-133">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="83f99-134">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="83f99-134">CompletedActivityDisplayName</span></span>|<span data-ttu-id="83f99-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="83f99-135">xs:string</span></span>|<span data-ttu-id="83f99-136">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="83f99-136">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="83f99-137">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="83f99-137">CompletedActivityInstanceId</span></span>|<span data-ttu-id="83f99-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="83f99-138">xs:string</span></span>|<span data-ttu-id="83f99-139">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="83f99-139">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="83f99-140">AppDomain</span><span class="sxs-lookup"><span data-stu-id="83f99-140">AppDomain</span></span>|<span data-ttu-id="83f99-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="83f99-141">xs:string</span></span>|<span data-ttu-id="83f99-142">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="83f99-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
