---
description: '詳細について: 1026-ScheduleTransactionContextWorkItem'
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 913af6903d38cea8f5c8d3e6e72dff04ff706195
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755487"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="44552-103">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="44552-103">1026 - ScheduleTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="44552-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="44552-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="44552-105">id</span><span class="sxs-lookup"><span data-stu-id="44552-105">ID</span></span>|<span data-ttu-id="44552-106">1026</span><span class="sxs-lookup"><span data-stu-id="44552-106">1026</span></span>|  
|<span data-ttu-id="44552-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="44552-107">Keywords</span></span>|<span data-ttu-id="44552-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="44552-108">WFRuntime</span></span>|  
|<span data-ttu-id="44552-109">Level</span><span class="sxs-lookup"><span data-stu-id="44552-109">Level</span></span>|<span data-ttu-id="44552-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="44552-110">Verbose</span></span>|  
|<span data-ttu-id="44552-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="44552-111">Channel</span></span>|<span data-ttu-id="44552-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="44552-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="44552-113">説明</span><span class="sxs-lookup"><span data-stu-id="44552-113">Description</span></span>  

 <span data-ttu-id="44552-114">TransactionContextWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="44552-114">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="44552-115">Message</span><span class="sxs-lookup"><span data-stu-id="44552-115">Message</span></span>  

 <span data-ttu-id="44552-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して TransactionContextWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="44552-116">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="44552-117">詳細</span><span class="sxs-lookup"><span data-stu-id="44552-117">Details</span></span>  
  
|<span data-ttu-id="44552-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="44552-118">Data Item Name</span></span>|<span data-ttu-id="44552-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="44552-119">Data Item Type</span></span>|<span data-ttu-id="44552-120">説明</span><span class="sxs-lookup"><span data-stu-id="44552-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="44552-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="44552-121">Activity</span></span>|<span data-ttu-id="44552-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="44552-122">xs:string</span></span>|<span data-ttu-id="44552-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="44552-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="44552-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="44552-124">DisplayName</span></span>|<span data-ttu-id="44552-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="44552-125">xs:string</span></span>|<span data-ttu-id="44552-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="44552-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="44552-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="44552-127">InstanceId</span></span>|<span data-ttu-id="44552-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="44552-128">xs:string</span></span>|<span data-ttu-id="44552-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="44552-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="44552-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="44552-130">AppDomain</span></span>|<span data-ttu-id="44552-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="44552-131">xs:string</span></span>|<span data-ttu-id="44552-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="44552-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
