---
description: '詳細情報: 1013-CompleteExecuteActivityWorkItem'
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: 815f859c40a02e8c06e44603a80ab964dc4e64bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792948"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="62ce1-103">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="62ce1-103">1013 - CompleteExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="62ce1-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="62ce1-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62ce1-105">id</span><span class="sxs-lookup"><span data-stu-id="62ce1-105">ID</span></span>|<span data-ttu-id="62ce1-106">1013</span><span class="sxs-lookup"><span data-stu-id="62ce1-106">1013</span></span>|  
|<span data-ttu-id="62ce1-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="62ce1-107">Keywords</span></span>|<span data-ttu-id="62ce1-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="62ce1-108">WFRuntime</span></span>|  
|<span data-ttu-id="62ce1-109">Level</span><span class="sxs-lookup"><span data-stu-id="62ce1-109">Level</span></span>|<span data-ttu-id="62ce1-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="62ce1-110">Verbose</span></span>|  
|<span data-ttu-id="62ce1-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="62ce1-111">Channel</span></span>|<span data-ttu-id="62ce1-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="62ce1-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="62ce1-113">説明</span><span class="sxs-lookup"><span data-stu-id="62ce1-113">Description</span></span>  

 <span data-ttu-id="62ce1-114">ExecuteActivityWorkItem が完了したことを示します</span><span class="sxs-lookup"><span data-stu-id="62ce1-114">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="62ce1-115">Message</span><span class="sxs-lookup"><span data-stu-id="62ce1-115">Message</span></span>  

 <span data-ttu-id="62ce1-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の ExecuteActivityWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="62ce1-116">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="62ce1-117">詳細</span><span class="sxs-lookup"><span data-stu-id="62ce1-117">Details</span></span>  
  
|<span data-ttu-id="62ce1-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="62ce1-118">Data Item Name</span></span>|<span data-ttu-id="62ce1-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="62ce1-119">Data Item Type</span></span>|<span data-ttu-id="62ce1-120">説明</span><span class="sxs-lookup"><span data-stu-id="62ce1-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="62ce1-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="62ce1-121">Activity</span></span>|<span data-ttu-id="62ce1-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="62ce1-122">xs:string</span></span>|<span data-ttu-id="62ce1-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="62ce1-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="62ce1-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="62ce1-124">DisplayName</span></span>|<span data-ttu-id="62ce1-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="62ce1-125">xs:string</span></span>|<span data-ttu-id="62ce1-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="62ce1-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="62ce1-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="62ce1-127">InstanceId</span></span>|<span data-ttu-id="62ce1-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="62ce1-128">xs:string</span></span>|<span data-ttu-id="62ce1-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="62ce1-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="62ce1-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="62ce1-130">AppDomain</span></span>|<span data-ttu-id="62ce1-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="62ce1-131">xs:string</span></span>|<span data-ttu-id="62ce1-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="62ce1-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
