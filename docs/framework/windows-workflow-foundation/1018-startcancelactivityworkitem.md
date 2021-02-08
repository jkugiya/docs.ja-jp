---
description: '詳細情報: 1018-StartCancelActivityWorkItem'
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 99da17bd2fb75d9ed3a41e95ec1929df66964ffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792883"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="4d691-103">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="4d691-103">1018 - StartCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="4d691-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4d691-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4d691-105">id</span><span class="sxs-lookup"><span data-stu-id="4d691-105">ID</span></span>|<span data-ttu-id="4d691-106">1018</span><span class="sxs-lookup"><span data-stu-id="4d691-106">1018</span></span>|  
|<span data-ttu-id="4d691-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="4d691-107">Keywords</span></span>|<span data-ttu-id="4d691-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4d691-108">WFRuntime</span></span>|  
|<span data-ttu-id="4d691-109">Level</span><span class="sxs-lookup"><span data-stu-id="4d691-109">Level</span></span>|<span data-ttu-id="4d691-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="4d691-110">Verbose</span></span>|  
|<span data-ttu-id="4d691-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="4d691-111">Channel</span></span>|<span data-ttu-id="4d691-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4d691-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4d691-113">説明</span><span class="sxs-lookup"><span data-stu-id="4d691-113">Description</span></span>  

 <span data-ttu-id="4d691-114">CancelActivityWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="4d691-114">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4d691-115">Message</span><span class="sxs-lookup"><span data-stu-id="4d691-115">Message</span></span>  

 <span data-ttu-id="4d691-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="4d691-116">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4d691-117">詳細</span><span class="sxs-lookup"><span data-stu-id="4d691-117">Details</span></span>  
  
|<span data-ttu-id="4d691-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="4d691-118">Data Item Name</span></span>|<span data-ttu-id="4d691-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="4d691-119">Data Item Type</span></span>|<span data-ttu-id="4d691-120">説明</span><span class="sxs-lookup"><span data-stu-id="4d691-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4d691-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="4d691-121">Activity</span></span>|<span data-ttu-id="4d691-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d691-122">xs:string</span></span>|<span data-ttu-id="4d691-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="4d691-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="4d691-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4d691-124">DisplayName</span></span>|<span data-ttu-id="4d691-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d691-125">xs:string</span></span>|<span data-ttu-id="4d691-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="4d691-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="4d691-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4d691-127">InstanceId</span></span>|<span data-ttu-id="4d691-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d691-128">xs:string</span></span>|<span data-ttu-id="4d691-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="4d691-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4d691-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4d691-130">AppDomain</span></span>|<span data-ttu-id="4d691-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d691-131">xs:string</span></span>|<span data-ttu-id="4d691-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="4d691-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
