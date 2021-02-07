---
description: '詳細情報: 1132-InvokeMethodDoesNotUseAsyncPattern'
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 05bbd1f6047ab4c6451d71a4f6007f3112f9630f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667279"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="439f2-103">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="439f2-103">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="439f2-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="439f2-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="439f2-105">id</span><span class="sxs-lookup"><span data-stu-id="439f2-105">ID</span></span>|<span data-ttu-id="439f2-106">1132</span><span class="sxs-lookup"><span data-stu-id="439f2-106">1132</span></span>|  
|<span data-ttu-id="439f2-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="439f2-107">Keywords</span></span>|<span data-ttu-id="439f2-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="439f2-108">WFRuntime</span></span>|  
|<span data-ttu-id="439f2-109">Level</span><span class="sxs-lookup"><span data-stu-id="439f2-109">Level</span></span>|<span data-ttu-id="439f2-110">Information</span><span class="sxs-lookup"><span data-stu-id="439f2-110">Information</span></span>|  
|<span data-ttu-id="439f2-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="439f2-111">Channel</span></span>|<span data-ttu-id="439f2-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="439f2-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="439f2-113">説明</span><span class="sxs-lookup"><span data-stu-id="439f2-113">Description</span></span>  

 <span data-ttu-id="439f2-114">CacheMetadata 手順内で、InvokeMethod アクティビティがメソッドを呼び出すときに非同期パターンを使用しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="439f2-114">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="439f2-115">Message</span><span class="sxs-lookup"><span data-stu-id="439f2-115">Message</span></span>  

 <span data-ttu-id="439f2-116">InvokeMethod '%1' - メソッドでは非同期パターンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="439f2-116">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="439f2-117">詳細</span><span class="sxs-lookup"><span data-stu-id="439f2-117">Details</span></span>  
  
|<span data-ttu-id="439f2-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="439f2-118">Data Item Name</span></span>|<span data-ttu-id="439f2-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="439f2-119">Data Item Type</span></span>|<span data-ttu-id="439f2-120">説明</span><span class="sxs-lookup"><span data-stu-id="439f2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="439f2-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="439f2-121">InvokeMethod</span></span>|<span data-ttu-id="439f2-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="439f2-122">xs:string</span></span>|<span data-ttu-id="439f2-123">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="439f2-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="439f2-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="439f2-124">AppDomain</span></span>|<span data-ttu-id="439f2-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="439f2-125">xs:string</span></span>|<span data-ttu-id="439f2-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="439f2-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
