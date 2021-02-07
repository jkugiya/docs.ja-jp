---
description: 詳細については、「4212-LockRetryTimeout」を参照してください。
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: a2299d0d9643fb60ff420519fb43199e3f747c69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667084"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="26482-103">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="26482-103">4212 - LockRetryTimeout</span></span>

## <a name="properties"></a><span data-ttu-id="26482-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="26482-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26482-105">id</span><span class="sxs-lookup"><span data-stu-id="26482-105">ID</span></span>|<span data-ttu-id="26482-106">4212</span><span class="sxs-lookup"><span data-stu-id="26482-106">4212</span></span>|  
|<span data-ttu-id="26482-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="26482-107">Keywords</span></span>|<span data-ttu-id="26482-108">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="26482-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="26482-109">Level</span><span class="sxs-lookup"><span data-stu-id="26482-109">Level</span></span>|<span data-ttu-id="26482-110">警告</span><span class="sxs-lookup"><span data-stu-id="26482-110">Warning</span></span>|  
|<span data-ttu-id="26482-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="26482-111">Channel</span></span>|<span data-ttu-id="26482-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="26482-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="26482-113">説明</span><span class="sxs-lookup"><span data-stu-id="26482-113">Description</span></span>  

 <span data-ttu-id="26482-114">SQL プロバイダーはインスタンス ロックを取得しようとしてタイムアウトを検出しました。</span><span class="sxs-lookup"><span data-stu-id="26482-114">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="26482-115">Message</span><span class="sxs-lookup"><span data-stu-id="26482-115">Message</span></span>  

 <span data-ttu-id="26482-116">インスタンスのロックを取得しようとしてタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="26482-116">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="26482-117">割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="26482-117">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="26482-118">この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="26482-118">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="26482-119">詳細</span><span class="sxs-lookup"><span data-stu-id="26482-119">Details</span></span>  
  
|<span data-ttu-id="26482-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="26482-120">Data Item Name</span></span>|<span data-ttu-id="26482-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="26482-121">Data Item Type</span></span>|<span data-ttu-id="26482-122">説明</span><span class="sxs-lookup"><span data-stu-id="26482-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="26482-123">遅延</span><span class="sxs-lookup"><span data-stu-id="26482-123">Delay</span></span>|<span data-ttu-id="26482-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="26482-124">xs:string</span></span>|<span data-ttu-id="26482-125">再試行間の遅延。</span><span class="sxs-lookup"><span data-stu-id="26482-125">The delay between retries.</span></span>|  
|<span data-ttu-id="26482-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="26482-126">AppDomain</span></span>|<span data-ttu-id="26482-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="26482-127">xs:string</span></span>|<span data-ttu-id="26482-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="26482-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
