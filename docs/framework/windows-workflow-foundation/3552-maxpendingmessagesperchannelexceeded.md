---
description: '詳細情報: 3552-MaxPendingMessagesPerChannelExceeded'
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: 5fb2d27f7d68716cebf2cfaafd21851226a456e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631438"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="a52f6-103">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="a52f6-103">3552 - MaxPendingMessagesPerChannelExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="a52f6-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a52f6-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a52f6-105">id</span><span class="sxs-lookup"><span data-stu-id="a52f6-105">ID</span></span>|<span data-ttu-id="a52f6-106">3552</span><span class="sxs-lookup"><span data-stu-id="a52f6-106">3552</span></span>|  
|<span data-ttu-id="a52f6-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="a52f6-107">Keywords</span></span>|<span data-ttu-id="a52f6-108">クォータ、WFServices</span><span class="sxs-lookup"><span data-stu-id="a52f6-108">Quota, WFServices</span></span>|  
|<span data-ttu-id="a52f6-109">Level</span><span class="sxs-lookup"><span data-stu-id="a52f6-109">Level</span></span>|<span data-ttu-id="a52f6-110">警告</span><span class="sxs-lookup"><span data-stu-id="a52f6-110">Warning</span></span>|  
|<span data-ttu-id="a52f6-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="a52f6-111">Channel</span></span>|<span data-ttu-id="a52f6-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a52f6-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a52f6-113">説明</span><span class="sxs-lookup"><span data-stu-id="a52f6-113">Description</span></span>  

 <span data-ttu-id="a52f6-114">スロットル 'MaxPendingMessagesPerChannel' の制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="a52f6-114">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a52f6-115">Message</span><span class="sxs-lookup"><span data-stu-id="a52f6-115">Message</span></span>  

 <span data-ttu-id="a52f6-116">'%1' のスロットル 'MaxPendingMessagesPerChannel' の制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="a52f6-116">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="a52f6-117">この制限を引き上げるには、BufferedReceiveServiceBehavior の MaxPendingMessagesPerChannel プロパティを調整してください。</span><span class="sxs-lookup"><span data-stu-id="a52f6-117">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a52f6-118">詳細</span><span class="sxs-lookup"><span data-stu-id="a52f6-118">Details</span></span>  
  
|<span data-ttu-id="a52f6-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a52f6-119">Data Item Name</span></span>|<span data-ttu-id="a52f6-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a52f6-120">Data Item Type</span></span>|<span data-ttu-id="a52f6-121">説明</span><span class="sxs-lookup"><span data-stu-id="a52f6-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a52f6-122">制限</span><span class="sxs-lookup"><span data-stu-id="a52f6-122">Limit</span></span>|<span data-ttu-id="a52f6-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="a52f6-123">xs:string</span></span>|<span data-ttu-id="a52f6-124">MaxPendingMessagesPerChannel スロットルの制限。</span><span class="sxs-lookup"><span data-stu-id="a52f6-124">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="a52f6-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a52f6-125">AppDomain</span></span>|<span data-ttu-id="a52f6-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="a52f6-126">xs:string</span></span>|<span data-ttu-id="a52f6-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a52f6-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
