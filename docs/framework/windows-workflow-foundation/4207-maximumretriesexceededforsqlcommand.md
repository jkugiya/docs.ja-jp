---
description: '詳細情報: 4207-MaximumRetriesExceededForSqlCommand'
title: 4207 - MaximumRetriesExceededForSqlCommand
ms.date: 03/30/2017
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
ms.openlocfilehash: e831da08e37010afaa33f3a52cd7cf7a9b4d713b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742720"
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="e1bfb-103">4207 - MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="e1bfb-103">4207 - MaximumRetriesExceededForSqlCommand</span></span>

## <a name="properties"></a><span data-ttu-id="e1bfb-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e1bfb-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1bfb-105">id</span><span class="sxs-lookup"><span data-stu-id="e1bfb-105">ID</span></span>|<span data-ttu-id="e1bfb-106">4207</span><span class="sxs-lookup"><span data-stu-id="e1bfb-106">4207</span></span>|  
|<span data-ttu-id="e1bfb-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="e1bfb-107">Keywords</span></span>|<span data-ttu-id="e1bfb-108">クオータ、WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="e1bfb-108">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="e1bfb-109">Level</span><span class="sxs-lookup"><span data-stu-id="e1bfb-109">Level</span></span>|<span data-ttu-id="e1bfb-110">Information</span><span class="sxs-lookup"><span data-stu-id="e1bfb-110">Information</span></span>|  
|<span data-ttu-id="e1bfb-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="e1bfb-111">Channel</span></span>|<span data-ttu-id="e1bfb-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e1bfb-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1bfb-113">説明</span><span class="sxs-lookup"><span data-stu-id="e1bfb-113">Description</span></span>  

 <span data-ttu-id="e1bfb-114">再試行が最大実行回数実行されたので、SQL プロバイダーは SQL コマンドの再試行を停止しようとしていることを示します。</span><span class="sxs-lookup"><span data-stu-id="e1bfb-114">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1bfb-115">Message</span><span class="sxs-lookup"><span data-stu-id="e1bfb-115">Message</span></span>  

 <span data-ttu-id="e1bfb-116">SQL コマンドが最大実行回数実行されたので、この SQL コマンドの再試行を停止します。</span><span class="sxs-lookup"><span data-stu-id="e1bfb-116">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1bfb-117">詳細</span><span class="sxs-lookup"><span data-stu-id="e1bfb-117">Details</span></span>  
  
|<span data-ttu-id="e1bfb-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e1bfb-118">Data Item Name</span></span>|<span data-ttu-id="e1bfb-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e1bfb-119">Data Item Type</span></span>|<span data-ttu-id="e1bfb-120">説明</span><span class="sxs-lookup"><span data-stu-id="e1bfb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1bfb-121">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e1bfb-121">AppDomain</span></span>|<span data-ttu-id="e1bfb-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1bfb-122">xs:string</span></span>|<span data-ttu-id="e1bfb-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e1bfb-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
