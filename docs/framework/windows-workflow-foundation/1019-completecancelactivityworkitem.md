---
description: '詳細情報: 1019-CompleteCancelActivityWorkItem'
title: 1019 - CompleteCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
ms.openlocfilehash: 33e58931562d7244987dd8c0d9cf5d34fb894190
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792870"
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="75b0b-103">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="75b0b-103">1019 - CompleteCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="75b0b-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="75b0b-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75b0b-105">id</span><span class="sxs-lookup"><span data-stu-id="75b0b-105">ID</span></span>|<span data-ttu-id="75b0b-106">1019</span><span class="sxs-lookup"><span data-stu-id="75b0b-106">1019</span></span>|  
|<span data-ttu-id="75b0b-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="75b0b-107">Keywords</span></span>|<span data-ttu-id="75b0b-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="75b0b-108">WFRuntime</span></span>|  
|<span data-ttu-id="75b0b-109">Level</span><span class="sxs-lookup"><span data-stu-id="75b0b-109">Level</span></span>|<span data-ttu-id="75b0b-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="75b0b-110">Verbose</span></span>|  
|<span data-ttu-id="75b0b-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="75b0b-111">Channel</span></span>|<span data-ttu-id="75b0b-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="75b0b-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="75b0b-113">説明</span><span class="sxs-lookup"><span data-stu-id="75b0b-113">Description</span></span>  

 <span data-ttu-id="75b0b-114">CancelActivityWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="75b0b-114">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="75b0b-115">Message</span><span class="sxs-lookup"><span data-stu-id="75b0b-115">Message</span></span>  

 <span data-ttu-id="75b0b-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="75b0b-116">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="75b0b-117">詳細</span><span class="sxs-lookup"><span data-stu-id="75b0b-117">Details</span></span>  
  
|<span data-ttu-id="75b0b-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="75b0b-118">Data Item Name</span></span>|<span data-ttu-id="75b0b-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="75b0b-119">Data Item Type</span></span>|<span data-ttu-id="75b0b-120">説明</span><span class="sxs-lookup"><span data-stu-id="75b0b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="75b0b-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="75b0b-121">Activity</span></span>|<span data-ttu-id="75b0b-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="75b0b-122">xs:string</span></span>|<span data-ttu-id="75b0b-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="75b0b-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="75b0b-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="75b0b-124">DisplayName</span></span>|<span data-ttu-id="75b0b-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="75b0b-125">xs:string</span></span>|<span data-ttu-id="75b0b-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="75b0b-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="75b0b-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="75b0b-127">InstanceId</span></span>|<span data-ttu-id="75b0b-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="75b0b-128">xs:string</span></span>|<span data-ttu-id="75b0b-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="75b0b-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="75b0b-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="75b0b-130">AppDomain</span></span>|<span data-ttu-id="75b0b-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="75b0b-131">xs:string</span></span>|<span data-ttu-id="75b0b-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="75b0b-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
