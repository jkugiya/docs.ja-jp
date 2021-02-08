---
description: '詳細情報: 1020-CreateBookmark'
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 39796eaf68d9cb52e9faa2605fc21955a2c167ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792844"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="9237e-103">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="9237e-103">1020 - CreateBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="9237e-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9237e-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9237e-105">id</span><span class="sxs-lookup"><span data-stu-id="9237e-105">ID</span></span>|<span data-ttu-id="9237e-106">1020</span><span class="sxs-lookup"><span data-stu-id="9237e-106">1020</span></span>|  
|<span data-ttu-id="9237e-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="9237e-107">Keywords</span></span>|<span data-ttu-id="9237e-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9237e-108">WFRuntime</span></span>|  
|<span data-ttu-id="9237e-109">Level</span><span class="sxs-lookup"><span data-stu-id="9237e-109">Level</span></span>|<span data-ttu-id="9237e-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="9237e-110">Verbose</span></span>|  
|<span data-ttu-id="9237e-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="9237e-111">Channel</span></span>|<span data-ttu-id="9237e-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9237e-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9237e-113">説明</span><span class="sxs-lookup"><span data-stu-id="9237e-113">Description</span></span>  

 <span data-ttu-id="9237e-114">あるアクティビティ用のブックマークが作成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="9237e-114">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9237e-115">Message</span><span class="sxs-lookup"><span data-stu-id="9237e-115">Message</span></span>  

 <span data-ttu-id="9237e-116">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' のブックマークが作成されました。</span><span class="sxs-lookup"><span data-stu-id="9237e-116">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="9237e-117">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="9237e-117">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9237e-118">詳細</span><span class="sxs-lookup"><span data-stu-id="9237e-118">Details</span></span>  
  
|<span data-ttu-id="9237e-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9237e-119">Data Item Name</span></span>|<span data-ttu-id="9237e-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9237e-120">Data Item Type</span></span>|<span data-ttu-id="9237e-121">説明</span><span class="sxs-lookup"><span data-stu-id="9237e-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9237e-122">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="9237e-122">Activity</span></span>|<span data-ttu-id="9237e-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="9237e-123">xs:string</span></span>|<span data-ttu-id="9237e-124">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="9237e-124">The type name of the activity.</span></span>|  
|<span data-ttu-id="9237e-125">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9237e-125">DisplayName</span></span>|<span data-ttu-id="9237e-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="9237e-126">xs:string</span></span>|<span data-ttu-id="9237e-127">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="9237e-127">The display name of the activity.</span></span>|  
|<span data-ttu-id="9237e-128">InstanceId</span><span class="sxs-lookup"><span data-stu-id="9237e-128">InstanceId</span></span>|<span data-ttu-id="9237e-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="9237e-129">xs:string</span></span>|<span data-ttu-id="9237e-130">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="9237e-130">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9237e-131">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="9237e-131">BookmarkName</span></span>|<span data-ttu-id="9237e-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="9237e-132">xs:string</span></span>|<span data-ttu-id="9237e-133">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="9237e-133">The name of the bookmark.</span></span>|  
|<span data-ttu-id="9237e-134">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="9237e-134">BookmarkScope</span></span>|<span data-ttu-id="9237e-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="9237e-135">xs:string</span></span>|<span data-ttu-id="9237e-136">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="9237e-136">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="9237e-137">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9237e-137">AppDomain</span></span>|<span data-ttu-id="9237e-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="9237e-138">xs:string</span></span>|<span data-ttu-id="9237e-139">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="9237e-139">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
