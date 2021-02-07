---
description: '詳細情報: 1035-RuntimeTransactionSet'
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 513ba49962a8f02ab47b8e5b762949cd09154a3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667903"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="2a7f9-103">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="2a7f9-103">1035 - RuntimeTransactionSet</span></span>

## <a name="properties"></a><span data-ttu-id="2a7f9-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2a7f9-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a7f9-105">id</span><span class="sxs-lookup"><span data-stu-id="2a7f9-105">ID</span></span>|<span data-ttu-id="2a7f9-106">1035</span><span class="sxs-lookup"><span data-stu-id="2a7f9-106">1035</span></span>|  
|<span data-ttu-id="2a7f9-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="2a7f9-107">Keywords</span></span>|<span data-ttu-id="2a7f9-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2a7f9-108">WFRuntime</span></span>|  
|<span data-ttu-id="2a7f9-109">Level</span><span class="sxs-lookup"><span data-stu-id="2a7f9-109">Level</span></span>|<span data-ttu-id="2a7f9-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="2a7f9-110">Verbose</span></span>|  
|<span data-ttu-id="2a7f9-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="2a7f9-111">Channel</span></span>|<span data-ttu-id="2a7f9-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2a7f9-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2a7f9-113">説明</span><span class="sxs-lookup"><span data-stu-id="2a7f9-113">Description</span></span>  

 <span data-ttu-id="2a7f9-114">アクティビティがランタイムのトランザクションを設定したことを示します。</span><span class="sxs-lookup"><span data-stu-id="2a7f9-114">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2a7f9-115">Message</span><span class="sxs-lookup"><span data-stu-id="2a7f9-115">Message</span></span>  

 <span data-ttu-id="2a7f9-116">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' によってランタイムトランザクションが設定されました。</span><span class="sxs-lookup"><span data-stu-id="2a7f9-116">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="2a7f9-117">実行がアクティビティ ' %4 '、DisplayName: ' %5 '、InstanceId: ' %6 ' に分離されています。</span><span class="sxs-lookup"><span data-stu-id="2a7f9-117">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2a7f9-118">詳細</span><span class="sxs-lookup"><span data-stu-id="2a7f9-118">Details</span></span>  
  
|<span data-ttu-id="2a7f9-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2a7f9-119">Data Item Name</span></span>|<span data-ttu-id="2a7f9-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2a7f9-120">Data Item Type</span></span>|<span data-ttu-id="2a7f9-121">説明</span><span class="sxs-lookup"><span data-stu-id="2a7f9-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2a7f9-122">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="2a7f9-122">Activity</span></span>|<span data-ttu-id="2a7f9-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a7f9-123">xs:string</span></span>|<span data-ttu-id="2a7f9-124">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="2a7f9-124">The type name of the activity.</span></span>|  
|<span data-ttu-id="2a7f9-125">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2a7f9-125">DisplayName</span></span>|<span data-ttu-id="2a7f9-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a7f9-126">xs:string</span></span>|<span data-ttu-id="2a7f9-127">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="2a7f9-127">The display name of the activity.</span></span>|  
|<span data-ttu-id="2a7f9-128">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2a7f9-128">InstanceId</span></span>|<span data-ttu-id="2a7f9-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a7f9-129">xs:string</span></span>|<span data-ttu-id="2a7f9-130">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="2a7f9-130">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2a7f9-131">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="2a7f9-131">IsolatedActivity</span></span>|<span data-ttu-id="2a7f9-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a7f9-132">xs:string</span></span>|<span data-ttu-id="2a7f9-133">トランザクションが分離されるアクティビティの型の名前。</span><span class="sxs-lookup"><span data-stu-id="2a7f9-133">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="2a7f9-134">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="2a7f9-134">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="2a7f9-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a7f9-135">xs:string</span></span>|<span data-ttu-id="2a7f9-136">トランザクションが分離されるアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="2a7f9-136">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="2a7f9-137">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2a7f9-137">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="2a7f9-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a7f9-138">xs:string</span></span>|<span data-ttu-id="2a7f9-139">トランザクションが分離されるアクティビティのインスタンスの ID。</span><span class="sxs-lookup"><span data-stu-id="2a7f9-139">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="2a7f9-140">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2a7f9-140">AppDomain</span></span>|<span data-ttu-id="2a7f9-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="2a7f9-141">xs:string</span></span>|<span data-ttu-id="2a7f9-142">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2a7f9-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
