---
description: '詳細情報: 1030-StartFaultWorkItem'
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 2d148277b2d593cfcf75e17662626f1f486e7c1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668098"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="fc30c-103">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="fc30c-103">1030 - StartFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="fc30c-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fc30c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fc30c-105">id</span><span class="sxs-lookup"><span data-stu-id="fc30c-105">ID</span></span>|<span data-ttu-id="fc30c-106">1030</span><span class="sxs-lookup"><span data-stu-id="fc30c-106">1030</span></span>|  
|<span data-ttu-id="fc30c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="fc30c-107">Keywords</span></span>|<span data-ttu-id="fc30c-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fc30c-108">WFRuntime</span></span>|  
|<span data-ttu-id="fc30c-109">Level</span><span class="sxs-lookup"><span data-stu-id="fc30c-109">Level</span></span>|<span data-ttu-id="fc30c-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="fc30c-110">Verbose</span></span>|  
|<span data-ttu-id="fc30c-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="fc30c-111">Channel</span></span>|<span data-ttu-id="fc30c-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="fc30c-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fc30c-113">説明</span><span class="sxs-lookup"><span data-stu-id="fc30c-113">Description</span></span>  

 <span data-ttu-id="fc30c-114">FaultWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="fc30c-114">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fc30c-115">Message</span><span class="sxs-lookup"><span data-stu-id="fc30c-115">Message</span></span>  

 <span data-ttu-id="fc30c-116">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' の FaultWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="fc30c-116">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="fc30c-117">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="fc30c-117">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fc30c-118">詳細</span><span class="sxs-lookup"><span data-stu-id="fc30c-118">Details</span></span>  
  
|<span data-ttu-id="fc30c-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="fc30c-119">Data Item Name</span></span>|<span data-ttu-id="fc30c-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="fc30c-120">Data Item Type</span></span>|<span data-ttu-id="fc30c-121">説明</span><span class="sxs-lookup"><span data-stu-id="fc30c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fc30c-122">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="fc30c-122">FaultActivity</span></span>|<span data-ttu-id="fc30c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="fc30c-123">xs:string</span></span>|<span data-ttu-id="fc30c-124">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="fc30c-124">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="fc30c-125">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="fc30c-125">FaultActivityDisplayName</span></span>|<span data-ttu-id="fc30c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="fc30c-126">xs:string</span></span>|<span data-ttu-id="fc30c-127">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="fc30c-127">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="fc30c-128">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="fc30c-128">FaultActivityInstanceId</span></span>|<span data-ttu-id="fc30c-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="fc30c-129">xs:string</span></span>|<span data-ttu-id="fc30c-130">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="fc30c-130">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="fc30c-131">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="fc30c-131">ExceptionActivity</span></span>|<span data-ttu-id="fc30c-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="fc30c-132">xs:string</span></span>|<span data-ttu-id="fc30c-133">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="fc30c-133">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fc30c-134">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="fc30c-134">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="fc30c-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="fc30c-135">xs:string</span></span>|<span data-ttu-id="fc30c-136">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="fc30c-136">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fc30c-137">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="fc30c-137">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="fc30c-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="fc30c-138">xs:string</span></span>|<span data-ttu-id="fc30c-139">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="fc30c-139">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fc30c-140">例外</span><span class="sxs-lookup"><span data-stu-id="fc30c-140">Exception</span></span>|<span data-ttu-id="fc30c-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="fc30c-141">xs:string</span></span>|<span data-ttu-id="fc30c-142">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="fc30c-142">The exception details for the exception</span></span>|  
|<span data-ttu-id="fc30c-143">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fc30c-143">AppDomain</span></span>|<span data-ttu-id="fc30c-144">xs:string</span><span class="sxs-lookup"><span data-stu-id="fc30c-144">xs:string</span></span>|<span data-ttu-id="fc30c-145">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="fc30c-145">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
