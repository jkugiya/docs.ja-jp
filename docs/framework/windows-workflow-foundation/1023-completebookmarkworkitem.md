---
description: '詳細情報: 1023-CompleteBookmarkWorkItem'
title: 1023 - CompleteBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
ms.openlocfilehash: c83972b41a844747c47b97a0dd2bd37c26ae78a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755526"
---
# <a name="1023---completebookmarkworkitem"></a><span data-ttu-id="63a22-103">1023 - CompleteBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="63a22-103">1023 - CompleteBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="63a22-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="63a22-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63a22-105">id</span><span class="sxs-lookup"><span data-stu-id="63a22-105">ID</span></span>|<span data-ttu-id="63a22-106">1023</span><span class="sxs-lookup"><span data-stu-id="63a22-106">1023</span></span>|  
|<span data-ttu-id="63a22-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="63a22-107">Keywords</span></span>|<span data-ttu-id="63a22-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="63a22-108">WFRuntime</span></span>|  
|<span data-ttu-id="63a22-109">Level</span><span class="sxs-lookup"><span data-stu-id="63a22-109">Level</span></span>|<span data-ttu-id="63a22-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="63a22-110">Verbose</span></span>|  
|<span data-ttu-id="63a22-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="63a22-111">Channel</span></span>|<span data-ttu-id="63a22-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="63a22-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="63a22-113">説明</span><span class="sxs-lookup"><span data-stu-id="63a22-113">Description</span></span>  

 <span data-ttu-id="63a22-114">BookmarkWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="63a22-114">Indicates a BookmarkWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="63a22-115">Message</span><span class="sxs-lookup"><span data-stu-id="63a22-115">Message</span></span>  

 <span data-ttu-id="63a22-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の BookmarkWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="63a22-116">A BookmarkWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="63a22-117">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="63a22-117">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="63a22-118">詳細</span><span class="sxs-lookup"><span data-stu-id="63a22-118">Details</span></span>  
  
|<span data-ttu-id="63a22-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="63a22-119">Data Item Name</span></span>|<span data-ttu-id="63a22-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="63a22-120">Data Item Type</span></span>|<span data-ttu-id="63a22-121">説明</span><span class="sxs-lookup"><span data-stu-id="63a22-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="63a22-122">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="63a22-122">Activity</span></span>|<span data-ttu-id="63a22-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="63a22-123">xs:string</span></span>|<span data-ttu-id="63a22-124">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="63a22-124">The type name of the activity.</span></span>|  
|<span data-ttu-id="63a22-125">DisplayName</span><span class="sxs-lookup"><span data-stu-id="63a22-125">DisplayName</span></span>|<span data-ttu-id="63a22-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="63a22-126">xs:string</span></span>|<span data-ttu-id="63a22-127">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="63a22-127">The display name of the activity.</span></span>|  
|<span data-ttu-id="63a22-128">InstanceId</span><span class="sxs-lookup"><span data-stu-id="63a22-128">InstanceId</span></span>|<span data-ttu-id="63a22-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="63a22-129">xs:string</span></span>|<span data-ttu-id="63a22-130">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="63a22-130">The instance id of the activity.</span></span>|  
|<span data-ttu-id="63a22-131">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="63a22-131">BookmarkName</span></span>|<span data-ttu-id="63a22-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="63a22-132">xs:string</span></span>|<span data-ttu-id="63a22-133">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="63a22-133">The name of the bookmark.</span></span>|  
|<span data-ttu-id="63a22-134">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="63a22-134">BookmarkScope</span></span>|<span data-ttu-id="63a22-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="63a22-135">xs:string</span></span>|<span data-ttu-id="63a22-136">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="63a22-136">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="63a22-137">AppDomain</span><span class="sxs-lookup"><span data-stu-id="63a22-137">AppDomain</span></span>|<span data-ttu-id="63a22-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="63a22-138">xs:string</span></span>|<span data-ttu-id="63a22-139">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="63a22-139">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
