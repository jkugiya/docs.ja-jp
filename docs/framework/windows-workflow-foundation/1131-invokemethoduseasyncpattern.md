---
description: '詳細情報: 1131-InvokeMethodUseAsyncPattern'
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 59d8e5e1fe7c5b038df6fce3211fd01977abc4f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667318"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="a1f1f-103">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="a1f1f-103">1131 - InvokeMethodUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="a1f1f-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a1f1f-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1f1f-105">id</span><span class="sxs-lookup"><span data-stu-id="a1f1f-105">ID</span></span>|<span data-ttu-id="a1f1f-106">1131</span><span class="sxs-lookup"><span data-stu-id="a1f1f-106">1131</span></span>|  
|<span data-ttu-id="a1f1f-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="a1f1f-107">Keywords</span></span>|<span data-ttu-id="a1f1f-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a1f1f-108">WFRuntime</span></span>|  
|<span data-ttu-id="a1f1f-109">Level</span><span class="sxs-lookup"><span data-stu-id="a1f1f-109">Level</span></span>|<span data-ttu-id="a1f1f-110">Information</span><span class="sxs-lookup"><span data-stu-id="a1f1f-110">Information</span></span>|  
|<span data-ttu-id="a1f1f-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="a1f1f-111">Channel</span></span>|<span data-ttu-id="a1f1f-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a1f1f-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a1f1f-113">説明</span><span class="sxs-lookup"><span data-stu-id="a1f1f-113">Description</span></span>  

 <span data-ttu-id="a1f1f-114">CacheMetadata の手順では、InvokeMethod アクティビティはメソッドを呼び出すときの非同期パターンを使用していることを示します。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-114">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a1f1f-115">Message</span><span class="sxs-lookup"><span data-stu-id="a1f1f-115">Message</span></span>  

 <span data-ttu-id="a1f1f-116">InvokeMethod '%1' - メソッドでは '%2' および '%3' の非同期パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-116">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a1f1f-117">詳細</span><span class="sxs-lookup"><span data-stu-id="a1f1f-117">Details</span></span>  
  
|<span data-ttu-id="a1f1f-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a1f1f-118">Data Item Name</span></span>|<span data-ttu-id="a1f1f-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a1f1f-119">Data Item Type</span></span>|<span data-ttu-id="a1f1f-120">説明</span><span class="sxs-lookup"><span data-stu-id="a1f1f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a1f1f-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="a1f1f-121">InvokeMethod</span></span>|<span data-ttu-id="a1f1f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1f1f-122">xs:string</span></span>|<span data-ttu-id="a1f1f-123">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="a1f1f-124">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="a1f1f-124">BeginMethod</span></span>|<span data-ttu-id="a1f1f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1f1f-125">xs:string</span></span>|<span data-ttu-id="a1f1f-126">begin メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-126">The name of the begin method.</span></span>|  
|<span data-ttu-id="a1f1f-127">EndMethod</span><span class="sxs-lookup"><span data-stu-id="a1f1f-127">EndMethod</span></span>|<span data-ttu-id="a1f1f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1f1f-128">xs:string</span></span>|<span data-ttu-id="a1f1f-129">end メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-129">The name of the end method.</span></span>|  
|<span data-ttu-id="a1f1f-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a1f1f-130">AppDomain</span></span>|<span data-ttu-id="a1f1f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1f1f-131">xs:string</span></span>|<span data-ttu-id="a1f1f-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a1f1f-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
