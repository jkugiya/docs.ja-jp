---
description: 詳細については、「1032-スケジューラ Untimeworkitem」を参照してください。
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: d96226b4ab0f856218d292c9c2481bca6c463c8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668046"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="00651-103">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="00651-103">1032 - ScheduleRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="00651-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="00651-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="00651-105">id</span><span class="sxs-lookup"><span data-stu-id="00651-105">ID</span></span>|<span data-ttu-id="00651-106">1032</span><span class="sxs-lookup"><span data-stu-id="00651-106">1032</span></span>|  
|<span data-ttu-id="00651-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="00651-107">Keywords</span></span>|<span data-ttu-id="00651-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="00651-108">WFRuntime</span></span>|  
|<span data-ttu-id="00651-109">Level</span><span class="sxs-lookup"><span data-stu-id="00651-109">Level</span></span>|<span data-ttu-id="00651-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="00651-110">Verbose</span></span>|  
|<span data-ttu-id="00651-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="00651-111">Channel</span></span>|<span data-ttu-id="00651-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="00651-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="00651-113">説明</span><span class="sxs-lookup"><span data-stu-id="00651-113">Description</span></span>  

 <span data-ttu-id="00651-114">RuntimeWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="00651-114">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="00651-115">Message</span><span class="sxs-lookup"><span data-stu-id="00651-115">Message</span></span>  

 <span data-ttu-id="00651-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対してランタイム作業項目がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="00651-116">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="00651-117">詳細</span><span class="sxs-lookup"><span data-stu-id="00651-117">Details</span></span>  
  
|<span data-ttu-id="00651-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="00651-118">Data Item Name</span></span>|<span data-ttu-id="00651-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="00651-119">Data Item Type</span></span>|<span data-ttu-id="00651-120">説明</span><span class="sxs-lookup"><span data-stu-id="00651-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="00651-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="00651-121">Activity</span></span>|<span data-ttu-id="00651-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="00651-122">xs:string</span></span>|<span data-ttu-id="00651-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="00651-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="00651-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="00651-124">DisplayName</span></span>|<span data-ttu-id="00651-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="00651-125">xs:string</span></span>|<span data-ttu-id="00651-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="00651-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="00651-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="00651-127">InstanceId</span></span>|<span data-ttu-id="00651-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="00651-128">xs:string</span></span>|<span data-ttu-id="00651-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="00651-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="00651-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="00651-130">AppDomain</span></span>|<span data-ttu-id="00651-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="00651-131">xs:string</span></span>|<span data-ttu-id="00651-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="00651-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
