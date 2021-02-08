---
description: '詳細情報: 1016-CompleteCompletionWorkItem'
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 849e192d63b5db19e5beea31befcdc38d4340c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792909"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="3fa1c-103">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="3fa1c-103">1016 - CompleteCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="3fa1c-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3fa1c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3fa1c-105">id</span><span class="sxs-lookup"><span data-stu-id="3fa1c-105">ID</span></span>|<span data-ttu-id="3fa1c-106">1016</span><span class="sxs-lookup"><span data-stu-id="3fa1c-106">1016</span></span>|  
|<span data-ttu-id="3fa1c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="3fa1c-107">Keywords</span></span>|<span data-ttu-id="3fa1c-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3fa1c-108">WFRuntime</span></span>|  
|<span data-ttu-id="3fa1c-109">Level</span><span class="sxs-lookup"><span data-stu-id="3fa1c-109">Level</span></span>|<span data-ttu-id="3fa1c-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="3fa1c-110">Verbose</span></span>|  
|<span data-ttu-id="3fa1c-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="3fa1c-111">Channel</span></span>|<span data-ttu-id="3fa1c-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3fa1c-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3fa1c-113">説明</span><span class="sxs-lookup"><span data-stu-id="3fa1c-113">Description</span></span>  

 <span data-ttu-id="3fa1c-114">CompletionWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="3fa1c-114">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3fa1c-115">Message</span><span class="sxs-lookup"><span data-stu-id="3fa1c-115">Message</span></span>  

 <span data-ttu-id="3fa1c-116">親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="3fa1c-116">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="3fa1c-117">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="3fa1c-117">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3fa1c-118">詳細</span><span class="sxs-lookup"><span data-stu-id="3fa1c-118">Details</span></span>  
  
|<span data-ttu-id="3fa1c-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="3fa1c-119">Data Item Name</span></span>|<span data-ttu-id="3fa1c-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="3fa1c-120">Data Item Type</span></span>|<span data-ttu-id="3fa1c-121">説明</span><span class="sxs-lookup"><span data-stu-id="3fa1c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3fa1c-122">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="3fa1c-122">ParentActivity</span></span>|<span data-ttu-id="3fa1c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="3fa1c-123">xs:string</span></span>|<span data-ttu-id="3fa1c-124">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="3fa1c-124">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="3fa1c-125">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="3fa1c-125">ParentDisplayName</span></span>|<span data-ttu-id="3fa1c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="3fa1c-126">xs:string</span></span>|<span data-ttu-id="3fa1c-127">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="3fa1c-127">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="3fa1c-128">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="3fa1c-128">ParentInstanceId</span></span>|<span data-ttu-id="3fa1c-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="3fa1c-129">xs:string</span></span>|<span data-ttu-id="3fa1c-130">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="3fa1c-130">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="3fa1c-131">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="3fa1c-131">CompletedActivity</span></span>|<span data-ttu-id="3fa1c-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="3fa1c-132">xs:string</span></span>|<span data-ttu-id="3fa1c-133">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="3fa1c-133">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="3fa1c-134">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3fa1c-134">CompletedActivityDisplayName</span></span>|<span data-ttu-id="3fa1c-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="3fa1c-135">xs:string</span></span>|<span data-ttu-id="3fa1c-136">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="3fa1c-136">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="3fa1c-137">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3fa1c-137">CompletedActivityInstanceId</span></span>|<span data-ttu-id="3fa1c-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="3fa1c-138">xs:string</span></span>|<span data-ttu-id="3fa1c-139">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="3fa1c-139">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="3fa1c-140">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3fa1c-140">AppDomain</span></span>|<span data-ttu-id="3fa1c-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="3fa1c-141">xs:string</span></span>|<span data-ttu-id="3fa1c-142">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="3fa1c-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
