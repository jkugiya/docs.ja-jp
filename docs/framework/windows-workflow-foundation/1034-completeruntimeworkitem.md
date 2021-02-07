---
description: '詳細については、次を参照してください: 1034-フル Teruntimeworkitem'
title: 1034 - CompleteRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
ms.openlocfilehash: dd8a9fcb2fb692ab3b69df8f07f6a96cf48fc806
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667968"
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="c8fc0-103">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="c8fc0-103">1034 - CompleteRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="c8fc0-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c8fc0-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8fc0-105">id</span><span class="sxs-lookup"><span data-stu-id="c8fc0-105">ID</span></span>|<span data-ttu-id="c8fc0-106">1034</span><span class="sxs-lookup"><span data-stu-id="c8fc0-106">1034</span></span>|  
|<span data-ttu-id="c8fc0-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="c8fc0-107">Keywords</span></span>|<span data-ttu-id="c8fc0-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c8fc0-108">WFRuntime</span></span>|  
|<span data-ttu-id="c8fc0-109">Level</span><span class="sxs-lookup"><span data-stu-id="c8fc0-109">Level</span></span>|<span data-ttu-id="c8fc0-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="c8fc0-110">Verbose</span></span>|  
|<span data-ttu-id="c8fc0-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="c8fc0-111">Channel</span></span>|<span data-ttu-id="c8fc0-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c8fc0-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c8fc0-113">説明</span><span class="sxs-lookup"><span data-stu-id="c8fc0-113">Description</span></span>  

 <span data-ttu-id="c8fc0-114">RuntimeWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c8fc0-114">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c8fc0-115">Message</span><span class="sxs-lookup"><span data-stu-id="c8fc0-115">Message</span></span>  

 <span data-ttu-id="c8fc0-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目が完了しました。</span><span class="sxs-lookup"><span data-stu-id="c8fc0-116">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c8fc0-117">詳細</span><span class="sxs-lookup"><span data-stu-id="c8fc0-117">Details</span></span>  
  
|<span data-ttu-id="c8fc0-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c8fc0-118">Data Item Name</span></span>|<span data-ttu-id="c8fc0-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c8fc0-119">Data Item Type</span></span>|<span data-ttu-id="c8fc0-120">説明</span><span class="sxs-lookup"><span data-stu-id="c8fc0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c8fc0-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="c8fc0-121">Activity</span></span>|<span data-ttu-id="c8fc0-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c8fc0-122">xs:string</span></span>|<span data-ttu-id="c8fc0-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="c8fc0-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="c8fc0-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c8fc0-124">DisplayName</span></span>|<span data-ttu-id="c8fc0-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c8fc0-125">xs:string</span></span>|<span data-ttu-id="c8fc0-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="c8fc0-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="c8fc0-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c8fc0-127">InstanceId</span></span>|<span data-ttu-id="c8fc0-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="c8fc0-128">xs:string</span></span>|<span data-ttu-id="c8fc0-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="c8fc0-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c8fc0-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c8fc0-130">AppDomain</span></span>|<span data-ttu-id="c8fc0-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="c8fc0-131">xs:string</span></span>|<span data-ttu-id="c8fc0-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c8fc0-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
