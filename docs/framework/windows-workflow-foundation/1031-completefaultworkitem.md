---
description: '詳細情報: 1031-CompleteFaultWorkItem'
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: dc5cb4988df2aab9710fd7ec875d9b4004bfa7af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668072"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="93b5b-103">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="93b5b-103">1031 - CompleteFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="93b5b-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="93b5b-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93b5b-105">id</span><span class="sxs-lookup"><span data-stu-id="93b5b-105">ID</span></span>|<span data-ttu-id="93b5b-106">1031</span><span class="sxs-lookup"><span data-stu-id="93b5b-106">1031</span></span>|  
|<span data-ttu-id="93b5b-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="93b5b-107">Keywords</span></span>|<span data-ttu-id="93b5b-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="93b5b-108">WFRuntime</span></span>|  
|<span data-ttu-id="93b5b-109">Level</span><span class="sxs-lookup"><span data-stu-id="93b5b-109">Level</span></span>|<span data-ttu-id="93b5b-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="93b5b-110">Verbose</span></span>|  
|<span data-ttu-id="93b5b-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="93b5b-111">Channel</span></span>|<span data-ttu-id="93b5b-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="93b5b-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="93b5b-113">説明</span><span class="sxs-lookup"><span data-stu-id="93b5b-113">Description</span></span>  

 <span data-ttu-id="93b5b-114">FaultWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="93b5b-114">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="93b5b-115">Message</span><span class="sxs-lookup"><span data-stu-id="93b5b-115">Message</span></span>  

 <span data-ttu-id="93b5b-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の FaultWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="93b5b-116">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="93b5b-117">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="93b5b-117">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="93b5b-118">詳細</span><span class="sxs-lookup"><span data-stu-id="93b5b-118">Details</span></span>  
  
|<span data-ttu-id="93b5b-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="93b5b-119">Data Item Name</span></span>|<span data-ttu-id="93b5b-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="93b5b-120">Data Item Type</span></span>|<span data-ttu-id="93b5b-121">説明</span><span class="sxs-lookup"><span data-stu-id="93b5b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="93b5b-122">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="93b5b-122">FaultActivity</span></span>|<span data-ttu-id="93b5b-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b5b-123">xs:string</span></span>|<span data-ttu-id="93b5b-124">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="93b5b-124">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="93b5b-125">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="93b5b-125">FaultActivityDisplayName</span></span>|<span data-ttu-id="93b5b-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b5b-126">xs:string</span></span>|<span data-ttu-id="93b5b-127">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="93b5b-127">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="93b5b-128">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="93b5b-128">FaultActivityInstanceId</span></span>|<span data-ttu-id="93b5b-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b5b-129">xs:string</span></span>|<span data-ttu-id="93b5b-130">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="93b5b-130">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="93b5b-131">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="93b5b-131">ExceptionActivity</span></span>|<span data-ttu-id="93b5b-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b5b-132">xs:string</span></span>|<span data-ttu-id="93b5b-133">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="93b5b-133">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="93b5b-134">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="93b5b-134">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="93b5b-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b5b-135">xs:string</span></span>|<span data-ttu-id="93b5b-136">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="93b5b-136">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="93b5b-137">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="93b5b-137">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="93b5b-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b5b-138">xs:string</span></span>|<span data-ttu-id="93b5b-139">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="93b5b-139">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="93b5b-140">例外</span><span class="sxs-lookup"><span data-stu-id="93b5b-140">Exception</span></span>|<span data-ttu-id="93b5b-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b5b-141">xs:string</span></span>|<span data-ttu-id="93b5b-142">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="93b5b-142">The exception details for the exception</span></span>|  
|<span data-ttu-id="93b5b-143">AppDomain</span><span class="sxs-lookup"><span data-stu-id="93b5b-143">AppDomain</span></span>|<span data-ttu-id="93b5b-144">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b5b-144">xs:string</span></span>|<span data-ttu-id="93b5b-145">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="93b5b-145">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
