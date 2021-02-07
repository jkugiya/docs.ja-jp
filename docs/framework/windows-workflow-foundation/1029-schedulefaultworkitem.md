---
description: '詳細情報: 1029-ScheduleFaultWorkItem'
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: e5f0463626882d6c8c48412326582fafa7be4670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755448"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="d49cc-103">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="d49cc-103">1029 - ScheduleFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="d49cc-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d49cc-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d49cc-105">id</span><span class="sxs-lookup"><span data-stu-id="d49cc-105">ID</span></span>|<span data-ttu-id="d49cc-106">1029</span><span class="sxs-lookup"><span data-stu-id="d49cc-106">1029</span></span>|  
|<span data-ttu-id="d49cc-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="d49cc-107">Keywords</span></span>|<span data-ttu-id="d49cc-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d49cc-108">WFRuntime</span></span>|  
|<span data-ttu-id="d49cc-109">Level</span><span class="sxs-lookup"><span data-stu-id="d49cc-109">Level</span></span>|<span data-ttu-id="d49cc-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="d49cc-110">Verbose</span></span>|  
|<span data-ttu-id="d49cc-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="d49cc-111">Channel</span></span>|<span data-ttu-id="d49cc-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d49cc-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d49cc-113">説明</span><span class="sxs-lookup"><span data-stu-id="d49cc-113">Description</span></span>  

 <span data-ttu-id="d49cc-114">FaultWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="d49cc-114">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d49cc-115">Message</span><span class="sxs-lookup"><span data-stu-id="d49cc-115">Message</span></span>  

 <span data-ttu-id="d49cc-116">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' に対して FaultWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="d49cc-116">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="d49cc-117">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="d49cc-117">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d49cc-118">詳細</span><span class="sxs-lookup"><span data-stu-id="d49cc-118">Details</span></span>  
  
|<span data-ttu-id="d49cc-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d49cc-119">Data Item Name</span></span>|<span data-ttu-id="d49cc-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d49cc-120">Data Item Type</span></span>|<span data-ttu-id="d49cc-121">説明</span><span class="sxs-lookup"><span data-stu-id="d49cc-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d49cc-122">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="d49cc-122">FaultActivity</span></span>|<span data-ttu-id="d49cc-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="d49cc-123">xs:string</span></span>|<span data-ttu-id="d49cc-124">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="d49cc-124">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="d49cc-125">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="d49cc-125">FaultActivityDisplayName</span></span>|<span data-ttu-id="d49cc-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="d49cc-126">xs:string</span></span>|<span data-ttu-id="d49cc-127">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="d49cc-127">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="d49cc-128">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="d49cc-128">FaultActivityInstanceId</span></span>|<span data-ttu-id="d49cc-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="d49cc-129">xs:string</span></span>|<span data-ttu-id="d49cc-130">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="d49cc-130">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="d49cc-131">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="d49cc-131">ExceptionActivity</span></span>|<span data-ttu-id="d49cc-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="d49cc-132">xs:string</span></span>|<span data-ttu-id="d49cc-133">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="d49cc-133">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="d49cc-134">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="d49cc-134">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="d49cc-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="d49cc-135">xs:string</span></span>|<span data-ttu-id="d49cc-136">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="d49cc-136">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="d49cc-137">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="d49cc-137">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="d49cc-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="d49cc-138">xs:string</span></span>|<span data-ttu-id="d49cc-139">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="d49cc-139">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="d49cc-140">例外</span><span class="sxs-lookup"><span data-stu-id="d49cc-140">Exception</span></span>|<span data-ttu-id="d49cc-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="d49cc-141">xs:string</span></span>|<span data-ttu-id="d49cc-142">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="d49cc-142">The exception details for the exception</span></span>|  
|<span data-ttu-id="d49cc-143">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d49cc-143">AppDomain</span></span>|<span data-ttu-id="d49cc-144">xs:string</span><span class="sxs-lookup"><span data-stu-id="d49cc-144">xs:string</span></span>|<span data-ttu-id="d49cc-145">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d49cc-145">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
