---
description: '詳細情報: 1012-StartExecuteActivityWorkItem'
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: 3b57fc6d37a6708a4e22537de87a2566612088e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99714886"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="af17c-103">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="af17c-103">1012 - StartExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="af17c-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="af17c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="af17c-105">id</span><span class="sxs-lookup"><span data-stu-id="af17c-105">ID</span></span>|<span data-ttu-id="af17c-106">1012</span><span class="sxs-lookup"><span data-stu-id="af17c-106">1012</span></span>|  
|<span data-ttu-id="af17c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="af17c-107">Keywords</span></span>|<span data-ttu-id="af17c-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="af17c-108">WFRuntime</span></span>|  
|<span data-ttu-id="af17c-109">Level</span><span class="sxs-lookup"><span data-stu-id="af17c-109">Level</span></span>|<span data-ttu-id="af17c-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="af17c-110">Verbose</span></span>|  
|<span data-ttu-id="af17c-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="af17c-111">Channel</span></span>|<span data-ttu-id="af17c-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="af17c-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="af17c-113">説明</span><span class="sxs-lookup"><span data-stu-id="af17c-113">Description</span></span>  

 <span data-ttu-id="af17c-114">ExecuteActivityWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="af17c-114">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="af17c-115">Message</span><span class="sxs-lookup"><span data-stu-id="af17c-115">Message</span></span>  

 <span data-ttu-id="af17c-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の ExecuteActivityWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="af17c-116">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="af17c-117">詳細</span><span class="sxs-lookup"><span data-stu-id="af17c-117">Details</span></span>  
  
|<span data-ttu-id="af17c-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="af17c-118">Data Item Name</span></span>|<span data-ttu-id="af17c-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="af17c-119">Data Item Type</span></span>|<span data-ttu-id="af17c-120">説明</span><span class="sxs-lookup"><span data-stu-id="af17c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="af17c-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="af17c-121">Activity</span></span>|<span data-ttu-id="af17c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="af17c-122">xs:string</span></span>|<span data-ttu-id="af17c-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="af17c-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="af17c-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="af17c-124">DisplayName</span></span>|<span data-ttu-id="af17c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="af17c-125">xs:string</span></span>|<span data-ttu-id="af17c-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="af17c-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="af17c-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="af17c-127">InstanceId</span></span>|<span data-ttu-id="af17c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="af17c-128">xs:string</span></span>|<span data-ttu-id="af17c-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="af17c-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="af17c-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="af17c-130">AppDomain</span></span>|<span data-ttu-id="af17c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="af17c-131">xs:string</span></span>|<span data-ttu-id="af17c-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="af17c-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
