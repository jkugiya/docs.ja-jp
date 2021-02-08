---
description: 詳細については、「4210-SqlExceptionCaught」を参照してください。
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 58846d02b6d1e388e3aef2bff76f51cba4990f2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777880"
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="b7ce8-103">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="b7ce8-103">4210 - SqlExceptionCaught</span></span>

## <a name="properties"></a><span data-ttu-id="b7ce8-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b7ce8-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7ce8-105">id</span><span class="sxs-lookup"><span data-stu-id="b7ce8-105">ID</span></span>|<span data-ttu-id="b7ce8-106">4210</span><span class="sxs-lookup"><span data-stu-id="b7ce8-106">4210</span></span>|  
|<span data-ttu-id="b7ce8-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="b7ce8-107">Keywords</span></span>|<span data-ttu-id="b7ce8-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="b7ce8-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="b7ce8-109">Level</span><span class="sxs-lookup"><span data-stu-id="b7ce8-109">Level</span></span>|<span data-ttu-id="b7ce8-110">警告</span><span class="sxs-lookup"><span data-stu-id="b7ce8-110">Warning</span></span>|  
|<span data-ttu-id="b7ce8-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="b7ce8-111">Channel</span></span>|<span data-ttu-id="b7ce8-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b7ce8-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7ce8-113">説明</span><span class="sxs-lookup"><span data-stu-id="b7ce8-113">Description</span></span>  

 <span data-ttu-id="b7ce8-114">SQL 例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="b7ce8-114">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7ce8-115">Message</span><span class="sxs-lookup"><span data-stu-id="b7ce8-115">Message</span></span>  

 <span data-ttu-id="b7ce8-116">SQL 例外番号 %1 メッセージ %2 がキャッチされました。</span><span class="sxs-lookup"><span data-stu-id="b7ce8-116">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7ce8-117">詳細</span><span class="sxs-lookup"><span data-stu-id="b7ce8-117">Details</span></span>  
  
|<span data-ttu-id="b7ce8-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b7ce8-118">Data Item Name</span></span>|<span data-ttu-id="b7ce8-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b7ce8-119">Data Item Type</span></span>|<span data-ttu-id="b7ce8-120">説明</span><span class="sxs-lookup"><span data-stu-id="b7ce8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7ce8-121">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="b7ce8-121">ErrorNumber</span></span>|<span data-ttu-id="b7ce8-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="b7ce8-122">xs:string</span></span>|<span data-ttu-id="b7ce8-123">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="b7ce8-123">The SQL error number.</span></span>|  
|<span data-ttu-id="b7ce8-124">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="b7ce8-124">ExceptionMessage</span></span>|<span data-ttu-id="b7ce8-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b7ce8-125">xs:string</span></span>|<span data-ttu-id="b7ce8-126">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b7ce8-126">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="b7ce8-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b7ce8-127">AppDomain</span></span>|<span data-ttu-id="b7ce8-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="b7ce8-128">xs:string</span></span>|<span data-ttu-id="b7ce8-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b7ce8-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
