---
description: 詳細については、「39456-TrackingRecordDropped」を参照してください。
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: 0f6920ef85327318f4ea8662ae36f26c7494bcb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631295"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="fc5c7-103">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="fc5c7-103">39456 - TrackingRecordDropped</span></span>

## <a name="properties"></a><span data-ttu-id="fc5c7-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fc5c7-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fc5c7-105">id</span><span class="sxs-lookup"><span data-stu-id="fc5c7-105">ID</span></span>|<span data-ttu-id="fc5c7-106">39456</span><span class="sxs-lookup"><span data-stu-id="fc5c7-106">39456</span></span>|  
|<span data-ttu-id="fc5c7-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="fc5c7-107">Keywords</span></span>|<span data-ttu-id="fc5c7-108">WFTracking</span><span class="sxs-lookup"><span data-stu-id="fc5c7-108">WFTracking</span></span>|  
|<span data-ttu-id="fc5c7-109">Level</span><span class="sxs-lookup"><span data-stu-id="fc5c7-109">Level</span></span>|<span data-ttu-id="fc5c7-110">警告</span><span class="sxs-lookup"><span data-stu-id="fc5c7-110">Warning</span></span>|  
|<span data-ttu-id="fc5c7-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="fc5c7-111">Channel</span></span>|<span data-ttu-id="fc5c7-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="fc5c7-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fc5c7-113">説明</span><span class="sxs-lookup"><span data-stu-id="fc5c7-113">Description</span></span>  

 <span data-ttu-id="fc5c7-114">サイズが ETW セッション プロバイダーによって許可される最大値を超えているため、追跡レコードが削除されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-114">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fc5c7-115">Message</span><span class="sxs-lookup"><span data-stu-id="fc5c7-115">Message</span></span>  

 <span data-ttu-id="fc5c7-116">追跡レコード %1 のサイズが、プロバイダー %2 の ETW セッションで許可される最大サイズを超えています</span><span class="sxs-lookup"><span data-stu-id="fc5c7-116">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="fc5c7-117">詳細</span><span class="sxs-lookup"><span data-stu-id="fc5c7-117">Details</span></span>  
  
|<span data-ttu-id="fc5c7-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="fc5c7-118">Data Item Name</span></span>|<span data-ttu-id="fc5c7-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="fc5c7-119">Data Item Type</span></span>|<span data-ttu-id="fc5c7-120">説明</span><span class="sxs-lookup"><span data-stu-id="fc5c7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fc5c7-121">例外</span><span class="sxs-lookup"><span data-stu-id="fc5c7-121">Exception</span></span>|<span data-ttu-id="fc5c7-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="fc5c7-122">xs:string</span></span>|<span data-ttu-id="fc5c7-123">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="fc5c7-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="fc5c7-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fc5c7-124">AppDomain</span></span>|<span data-ttu-id="fc5c7-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="fc5c7-125">xs:string</span></span>|<span data-ttu-id="fc5c7-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
