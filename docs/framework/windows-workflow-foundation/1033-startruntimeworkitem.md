---
description: '詳細情報: 1033-StartRuntimeWorkItem'
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: 31e664070b7592d3350a2f6f84f0493cc8f11ea1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668007"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="8ad11-103">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="8ad11-103">1033 - StartRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="8ad11-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8ad11-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ad11-105">id</span><span class="sxs-lookup"><span data-stu-id="8ad11-105">ID</span></span>|<span data-ttu-id="8ad11-106">1033</span><span class="sxs-lookup"><span data-stu-id="8ad11-106">1033</span></span>|  
|<span data-ttu-id="8ad11-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="8ad11-107">Keywords</span></span>|<span data-ttu-id="8ad11-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8ad11-108">WFRuntime</span></span>|  
|<span data-ttu-id="8ad11-109">Level</span><span class="sxs-lookup"><span data-stu-id="8ad11-109">Level</span></span>|<span data-ttu-id="8ad11-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="8ad11-110">Verbose</span></span>|  
|<span data-ttu-id="8ad11-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="8ad11-111">Channel</span></span>|<span data-ttu-id="8ad11-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8ad11-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8ad11-113">説明</span><span class="sxs-lookup"><span data-stu-id="8ad11-113">Description</span></span>  

 <span data-ttu-id="8ad11-114">RuntimeWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="8ad11-114">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8ad11-115">Message</span><span class="sxs-lookup"><span data-stu-id="8ad11-115">Message</span></span>  

 <span data-ttu-id="8ad11-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="8ad11-116">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8ad11-117">詳細</span><span class="sxs-lookup"><span data-stu-id="8ad11-117">Details</span></span>  
  
|<span data-ttu-id="8ad11-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8ad11-118">Data Item Name</span></span>|<span data-ttu-id="8ad11-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8ad11-119">Data Item Type</span></span>|<span data-ttu-id="8ad11-120">説明</span><span class="sxs-lookup"><span data-stu-id="8ad11-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8ad11-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="8ad11-121">Activity</span></span>|<span data-ttu-id="8ad11-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ad11-122">xs:string</span></span>|<span data-ttu-id="8ad11-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="8ad11-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="8ad11-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8ad11-124">DisplayName</span></span>|<span data-ttu-id="8ad11-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ad11-125">xs:string</span></span>|<span data-ttu-id="8ad11-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="8ad11-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="8ad11-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8ad11-127">InstanceId</span></span>|<span data-ttu-id="8ad11-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ad11-128">xs:string</span></span>|<span data-ttu-id="8ad11-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="8ad11-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8ad11-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8ad11-130">AppDomain</span></span>|<span data-ttu-id="8ad11-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ad11-131">xs:string</span></span>|<span data-ttu-id="8ad11-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8ad11-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
