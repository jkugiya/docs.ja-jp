---
description: '詳細情報: 57398-MaxInstancesExceeded'
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: 104c466cb2e0ee8156e2b268caf5e757353dfb09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720229"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="8d11c-103">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="8d11c-103">57398 - MaxInstancesExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="8d11c-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8d11c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8d11c-105">id</span><span class="sxs-lookup"><span data-stu-id="8d11c-105">ID</span></span>|<span data-ttu-id="8d11c-106">57398</span><span class="sxs-lookup"><span data-stu-id="8d11c-106">57398</span></span>|  
|<span data-ttu-id="8d11c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="8d11c-107">Keywords</span></span>|<span data-ttu-id="8d11c-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="8d11c-108">WFServices</span></span>|  
|<span data-ttu-id="8d11c-109">Level</span><span class="sxs-lookup"><span data-stu-id="8d11c-109">Level</span></span>|<span data-ttu-id="8d11c-110">警告</span><span class="sxs-lookup"><span data-stu-id="8d11c-110">Warning</span></span>|  
|<span data-ttu-id="8d11c-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="8d11c-111">Channel</span></span>|<span data-ttu-id="8d11c-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8d11c-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8d11c-113">説明</span><span class="sxs-lookup"><span data-stu-id="8d11c-113">Description</span></span>  

 <span data-ttu-id="8d11c-114">システムがスロットル 'MaxConcurrentInstances' に設定された制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8d11c-114">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8d11c-115">Message</span><span class="sxs-lookup"><span data-stu-id="8d11c-115">Message</span></span>  

 <span data-ttu-id="8d11c-116">システムはスロットル 'MaxConcurrentInstances' に設定された制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="8d11c-116">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="8d11c-117">このスロットルの制限は %1 に設定されました。</span><span class="sxs-lookup"><span data-stu-id="8d11c-117">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="8d11c-118">スロットル値を変更するには、serviceThrottle 要素の属性 'maxConcurrentInstances' を変更するか、動作 ServiceThrottlingBehavior の 'MaxConcurrentInstances' プロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d11c-118">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8d11c-119">詳細</span><span class="sxs-lookup"><span data-stu-id="8d11c-119">Details</span></span>  
  
|<span data-ttu-id="8d11c-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8d11c-120">Data Item Name</span></span>|<span data-ttu-id="8d11c-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8d11c-121">Data Item Type</span></span>|<span data-ttu-id="8d11c-122">説明</span><span class="sxs-lookup"><span data-stu-id="8d11c-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8d11c-123">名前</span><span class="sxs-lookup"><span data-stu-id="8d11c-123">Name</span></span>|<span data-ttu-id="8d11c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8d11c-124">xs:string</span></span>|<span data-ttu-id="8d11c-125">項目の名前。</span><span class="sxs-lookup"><span data-stu-id="8d11c-125">The name of the item.</span></span>|  
|<span data-ttu-id="8d11c-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8d11c-126">AppDomain</span></span>|<span data-ttu-id="8d11c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8d11c-127">xs:string</span></span>|<span data-ttu-id="8d11c-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8d11c-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
