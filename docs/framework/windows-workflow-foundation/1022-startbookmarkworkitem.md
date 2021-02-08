---
description: '詳細情報: 1022-StartBookmarkWorkItem'
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: 37d1ec1216df26a928b39189ca299dbb5b6c3d4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792831"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="54945-103">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="54945-103">1022 - StartBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="54945-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="54945-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54945-105">id</span><span class="sxs-lookup"><span data-stu-id="54945-105">ID</span></span>|<span data-ttu-id="54945-106">1022</span><span class="sxs-lookup"><span data-stu-id="54945-106">1022</span></span>|  
|<span data-ttu-id="54945-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="54945-107">Keywords</span></span>|<span data-ttu-id="54945-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="54945-108">WFRuntime</span></span>|  
|<span data-ttu-id="54945-109">Level</span><span class="sxs-lookup"><span data-stu-id="54945-109">Level</span></span>|<span data-ttu-id="54945-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="54945-110">Verbose</span></span>|  
|<span data-ttu-id="54945-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="54945-111">Channel</span></span>|<span data-ttu-id="54945-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="54945-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="54945-113">説明</span><span class="sxs-lookup"><span data-stu-id="54945-113">Description</span></span>  

 <span data-ttu-id="54945-114">BookmarkWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="54945-114">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="54945-115">Message</span><span class="sxs-lookup"><span data-stu-id="54945-115">Message</span></span>  

 <span data-ttu-id="54945-116">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' の BookmarkWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="54945-116">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="54945-117">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="54945-117">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="54945-118">詳細</span><span class="sxs-lookup"><span data-stu-id="54945-118">Details</span></span>  
  
|<span data-ttu-id="54945-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="54945-119">Data Item Name</span></span>|<span data-ttu-id="54945-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="54945-120">Data Item Type</span></span>|<span data-ttu-id="54945-121">説明</span><span class="sxs-lookup"><span data-stu-id="54945-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="54945-122">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="54945-122">Activity</span></span>|<span data-ttu-id="54945-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="54945-123">xs:string</span></span>|<span data-ttu-id="54945-124">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="54945-124">The type name of the activity.</span></span>|  
|<span data-ttu-id="54945-125">DisplayName</span><span class="sxs-lookup"><span data-stu-id="54945-125">DisplayName</span></span>|<span data-ttu-id="54945-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="54945-126">xs:string</span></span>|<span data-ttu-id="54945-127">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="54945-127">The display name of the activity.</span></span>|  
|<span data-ttu-id="54945-128">InstanceId</span><span class="sxs-lookup"><span data-stu-id="54945-128">InstanceId</span></span>|<span data-ttu-id="54945-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="54945-129">xs:string</span></span>|<span data-ttu-id="54945-130">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="54945-130">The instance id of the activity.</span></span>|  
|<span data-ttu-id="54945-131">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="54945-131">BookmarkName</span></span>|<span data-ttu-id="54945-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="54945-132">xs:string</span></span>|<span data-ttu-id="54945-133">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="54945-133">The name of the bookmark.</span></span>|  
|<span data-ttu-id="54945-134">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="54945-134">BookmarkScope</span></span>|<span data-ttu-id="54945-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="54945-135">xs:string</span></span>|<span data-ttu-id="54945-136">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="54945-136">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="54945-137">AppDomain</span><span class="sxs-lookup"><span data-stu-id="54945-137">AppDomain</span></span>|<span data-ttu-id="54945-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="54945-138">xs:string</span></span>|<span data-ttu-id="54945-139">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="54945-139">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
