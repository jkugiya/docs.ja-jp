---
description: '詳細については、次を参照してください: 4211-QueuingSqlRetry'
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: 674914ee105bb0a48f8c32efbd573c685d22d9f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742707"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="13e8b-103">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="13e8b-103">4211 - QueuingSqlRetry</span></span>

## <a name="properties"></a><span data-ttu-id="13e8b-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="13e8b-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="13e8b-105">id</span><span class="sxs-lookup"><span data-stu-id="13e8b-105">ID</span></span>|<span data-ttu-id="13e8b-106">4211</span><span class="sxs-lookup"><span data-stu-id="13e8b-106">4211</span></span>|  
|<span data-ttu-id="13e8b-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="13e8b-107">Keywords</span></span>|<span data-ttu-id="13e8b-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="13e8b-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="13e8b-109">Level</span><span class="sxs-lookup"><span data-stu-id="13e8b-109">Level</span></span>|<span data-ttu-id="13e8b-110">警告</span><span class="sxs-lookup"><span data-stu-id="13e8b-110">Warning</span></span>|  
|<span data-ttu-id="13e8b-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="13e8b-111">Channel</span></span>|<span data-ttu-id="13e8b-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="13e8b-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="13e8b-113">説明</span><span class="sxs-lookup"><span data-stu-id="13e8b-113">Description</span></span>  

 <span data-ttu-id="13e8b-114">SQL の再試行をキューに登録していることを示します。</span><span class="sxs-lookup"><span data-stu-id="13e8b-114">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="13e8b-115">Message</span><span class="sxs-lookup"><span data-stu-id="13e8b-115">Message</span></span>  

 <span data-ttu-id="13e8b-116">%1 ミリ秒の遅延で SQL の再試行をキューに登録しています。</span><span class="sxs-lookup"><span data-stu-id="13e8b-116">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="13e8b-117">詳細</span><span class="sxs-lookup"><span data-stu-id="13e8b-117">Details</span></span>  
  
|<span data-ttu-id="13e8b-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="13e8b-118">Data Item Name</span></span>|<span data-ttu-id="13e8b-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="13e8b-119">Data Item Type</span></span>|<span data-ttu-id="13e8b-120">説明</span><span class="sxs-lookup"><span data-stu-id="13e8b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="13e8b-121">遅延</span><span class="sxs-lookup"><span data-stu-id="13e8b-121">Delay</span></span>|<span data-ttu-id="13e8b-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="13e8b-122">xs:string</span></span>|<span data-ttu-id="13e8b-123">再試行間の遅延。</span><span class="sxs-lookup"><span data-stu-id="13e8b-123">The delay between retries.</span></span>|  
|<span data-ttu-id="13e8b-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="13e8b-124">AppDomain</span></span>|<span data-ttu-id="13e8b-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="13e8b-125">xs:string</span></span>|<span data-ttu-id="13e8b-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="13e8b-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
