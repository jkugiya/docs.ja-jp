---
description: '詳細情報: 39458-TrackingRecordTruncated'
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: bb9a46dc5bd9bc4f4709a740dd0e7ec47ca826e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631282"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="ce9b9-103">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="ce9b9-103">39458 - TrackingRecordTruncated</span></span>

## <a name="properties"></a><span data-ttu-id="ce9b9-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ce9b9-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce9b9-105">id</span><span class="sxs-lookup"><span data-stu-id="ce9b9-105">ID</span></span>|<span data-ttu-id="ce9b9-106">39458</span><span class="sxs-lookup"><span data-stu-id="ce9b9-106">39458</span></span>|  
|<span data-ttu-id="ce9b9-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="ce9b9-107">Keywords</span></span>|<span data-ttu-id="ce9b9-108">WFTracking</span><span class="sxs-lookup"><span data-stu-id="ce9b9-108">WFTracking</span></span>|  
|<span data-ttu-id="ce9b9-109">Level</span><span class="sxs-lookup"><span data-stu-id="ce9b9-109">Level</span></span>|<span data-ttu-id="ce9b9-110">警告</span><span class="sxs-lookup"><span data-stu-id="ce9b9-110">Warning</span></span>|  
|<span data-ttu-id="ce9b9-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="ce9b9-111">Channel</span></span>|<span data-ttu-id="ce9b9-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ce9b9-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ce9b9-113">説明</span><span class="sxs-lookup"><span data-stu-id="ce9b9-113">Description</span></span>  

 <span data-ttu-id="ce9b9-114">追跡レコードが省略されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-114">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="ce9b9-115">変数、注釈、ユーザー データは削除されています。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-115">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ce9b9-116">Message</span><span class="sxs-lookup"><span data-stu-id="ce9b9-116">Message</span></span>  

 <span data-ttu-id="ce9b9-117">プロバイダー %2 の ETW セッションに書き込まれた追跡レコード %1 が切り捨てられました。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-117">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="ce9b9-118">変数/注釈/ユーザー データは削除されました</span><span class="sxs-lookup"><span data-stu-id="ce9b9-118">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="ce9b9-119">詳細</span><span class="sxs-lookup"><span data-stu-id="ce9b9-119">Details</span></span>  
  
|<span data-ttu-id="ce9b9-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ce9b9-120">Data Item Name</span></span>|<span data-ttu-id="ce9b9-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ce9b9-121">Data Item Type</span></span>|<span data-ttu-id="ce9b9-122">説明</span><span class="sxs-lookup"><span data-stu-id="ce9b9-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ce9b9-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="ce9b9-123">RecordNumber</span></span>|<span data-ttu-id="ce9b9-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce9b9-124">xs:string</span></span>|<span data-ttu-id="ce9b9-125">追跡レコード番号。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-125">The tracking record number.</span></span>|  
|<span data-ttu-id="ce9b9-126">ProviderId</span><span class="sxs-lookup"><span data-stu-id="ce9b9-126">ProviderId</span></span>|<span data-ttu-id="ce9b9-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce9b9-127">xs:string</span></span>|<span data-ttu-id="ce9b9-128">ETW プロバイダー ID。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-128">The ETW provider id.</span></span>|  
|<span data-ttu-id="ce9b9-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ce9b9-129">AppDomain</span></span>|<span data-ttu-id="ce9b9-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="ce9b9-130">xs:string</span></span>|<span data-ttu-id="ce9b9-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ce9b9-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
