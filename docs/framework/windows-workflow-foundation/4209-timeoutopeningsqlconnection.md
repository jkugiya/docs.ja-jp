---
description: '詳細情報: 4209-TimeoutOpeningSqlConnection'
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: 9c7540e328530fdc01b9f065dfb75b92c467bd43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787995"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="abbe2-103">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="abbe2-103">4209 - TimeoutOpeningSqlConnection</span></span>

## <a name="properties"></a><span data-ttu-id="abbe2-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="abbe2-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="abbe2-105">id</span><span class="sxs-lookup"><span data-stu-id="abbe2-105">ID</span></span>|<span data-ttu-id="abbe2-106">4209</span><span class="sxs-lookup"><span data-stu-id="abbe2-106">4209</span></span>|  
|<span data-ttu-id="abbe2-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="abbe2-107">Keywords</span></span>|<span data-ttu-id="abbe2-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="abbe2-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="abbe2-109">Level</span><span class="sxs-lookup"><span data-stu-id="abbe2-109">Level</span></span>|<span data-ttu-id="abbe2-110">エラー</span><span class="sxs-lookup"><span data-stu-id="abbe2-110">Error</span></span>|  
|<span data-ttu-id="abbe2-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="abbe2-111">Channel</span></span>|<span data-ttu-id="abbe2-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="abbe2-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="abbe2-113">説明</span><span class="sxs-lookup"><span data-stu-id="abbe2-113">Description</span></span>  

 <span data-ttu-id="abbe2-114">SQL 接続を開こうとしてタイムアウトが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="abbe2-114">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="abbe2-115">Message</span><span class="sxs-lookup"><span data-stu-id="abbe2-115">Message</span></span>  

 <span data-ttu-id="abbe2-116">SQL 接続を開こうとしてタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="abbe2-116">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="abbe2-117">割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="abbe2-117">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="abbe2-118">この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="abbe2-118">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="abbe2-119">詳細</span><span class="sxs-lookup"><span data-stu-id="abbe2-119">Details</span></span>  
  
|<span data-ttu-id="abbe2-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="abbe2-120">Data Item Name</span></span>|<span data-ttu-id="abbe2-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="abbe2-121">Data Item Type</span></span>|<span data-ttu-id="abbe2-122">説明</span><span class="sxs-lookup"><span data-stu-id="abbe2-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="abbe2-123">タイムアウト</span><span class="sxs-lookup"><span data-stu-id="abbe2-123">Timeout</span></span>|<span data-ttu-id="abbe2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="abbe2-124">xs:string</span></span>|<span data-ttu-id="abbe2-125">SQL 接続を開く場合のタイムアウト値。</span><span class="sxs-lookup"><span data-stu-id="abbe2-125">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="abbe2-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="abbe2-126">AppDomain</span></span>|<span data-ttu-id="abbe2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="abbe2-127">xs:string</span></span>|<span data-ttu-id="abbe2-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="abbe2-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
