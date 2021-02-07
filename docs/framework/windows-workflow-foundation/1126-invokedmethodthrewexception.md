---
description: '詳細情報: 1126-InvokedMethodThrewException'
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 35c4311a4ab7750cc54a5c9ffb379f34b1cb12aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667357"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="67e99-103">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="67e99-103">1126 - InvokedMethodThrewException</span></span>

## <a name="properties"></a><span data-ttu-id="67e99-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="67e99-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67e99-105">id</span><span class="sxs-lookup"><span data-stu-id="67e99-105">ID</span></span>|<span data-ttu-id="67e99-106">1126</span><span class="sxs-lookup"><span data-stu-id="67e99-106">1126</span></span>|  
|<span data-ttu-id="67e99-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="67e99-107">Keywords</span></span>|<span data-ttu-id="67e99-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="67e99-108">WFRuntime</span></span>|  
|<span data-ttu-id="67e99-109">Level</span><span class="sxs-lookup"><span data-stu-id="67e99-109">Level</span></span>|<span data-ttu-id="67e99-110">Information</span><span class="sxs-lookup"><span data-stu-id="67e99-110">Information</span></span>|  
|<span data-ttu-id="67e99-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="67e99-111">Channel</span></span>|<span data-ttu-id="67e99-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="67e99-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="67e99-113">説明</span><span class="sxs-lookup"><span data-stu-id="67e99-113">Description</span></span>  

 <span data-ttu-id="67e99-114">InvokeMethod アクティビティによって呼び出されたメソッドにより、例外がスローされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="67e99-114">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="67e99-115">Message</span><span class="sxs-lookup"><span data-stu-id="67e99-115">Message</span></span>  

 <span data-ttu-id="67e99-116">アクティビティ '%1' によって呼び出されたメソッドで例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="67e99-116">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="67e99-117">%2</span><span class="sxs-lookup"><span data-stu-id="67e99-117">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="67e99-118">詳細</span><span class="sxs-lookup"><span data-stu-id="67e99-118">Details</span></span>  
  
|<span data-ttu-id="67e99-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="67e99-119">Data Item Name</span></span>|<span data-ttu-id="67e99-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="67e99-120">Data Item Type</span></span>|<span data-ttu-id="67e99-121">説明</span><span class="sxs-lookup"><span data-stu-id="67e99-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="67e99-122">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="67e99-122">InvokeMethod</span></span>|<span data-ttu-id="67e99-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="67e99-123">xs:string</span></span>|<span data-ttu-id="67e99-124">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="67e99-124">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="67e99-125">例外</span><span class="sxs-lookup"><span data-stu-id="67e99-125">Exception</span></span>|<span data-ttu-id="67e99-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="67e99-126">xs:string</span></span>|<span data-ttu-id="67e99-127">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="67e99-127">The exception details for the exception</span></span>|  
|<span data-ttu-id="67e99-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="67e99-128">AppDomain</span></span>|<span data-ttu-id="67e99-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="67e99-129">xs:string</span></span>|<span data-ttu-id="67e99-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="67e99-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
