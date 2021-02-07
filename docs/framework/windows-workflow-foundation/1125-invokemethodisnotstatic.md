---
description: '詳細情報: 1125-InvokeMethodIsNotStatic'
title: 1125 - InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: cd63b7b75121a70f7d7bad6a799827971aa4eae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667370"
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="9b6a3-103">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="9b6a3-103">1125 - InvokeMethodIsNotStatic</span></span>

## <a name="properties"></a><span data-ttu-id="9b6a3-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9b6a3-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9b6a3-105">id</span><span class="sxs-lookup"><span data-stu-id="9b6a3-105">ID</span></span>|<span data-ttu-id="9b6a3-106">1125</span><span class="sxs-lookup"><span data-stu-id="9b6a3-106">1125</span></span>|  
|<span data-ttu-id="9b6a3-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="9b6a3-107">Keywords</span></span>|<span data-ttu-id="9b6a3-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9b6a3-108">WFRuntime</span></span>|  
|<span data-ttu-id="9b6a3-109">Level</span><span class="sxs-lookup"><span data-stu-id="9b6a3-109">Level</span></span>|<span data-ttu-id="9b6a3-110">Information</span><span class="sxs-lookup"><span data-stu-id="9b6a3-110">Information</span></span>|  
|<span data-ttu-id="9b6a3-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="9b6a3-111">Channel</span></span>|<span data-ttu-id="9b6a3-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9b6a3-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9b6a3-113">説明</span><span class="sxs-lookup"><span data-stu-id="9b6a3-113">Description</span></span>  

 <span data-ttu-id="9b6a3-114">CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="9b6a3-114">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9b6a3-115">Message</span><span class="sxs-lookup"><span data-stu-id="9b6a3-115">Message</span></span>  

 <span data-ttu-id="9b6a3-116">InvokeMethod '%1' - メソッドは Static ではありません。</span><span class="sxs-lookup"><span data-stu-id="9b6a3-116">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9b6a3-117">詳細</span><span class="sxs-lookup"><span data-stu-id="9b6a3-117">Details</span></span>  
  
|<span data-ttu-id="9b6a3-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9b6a3-118">Data Item Name</span></span>|<span data-ttu-id="9b6a3-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9b6a3-119">Data Item Type</span></span>|<span data-ttu-id="9b6a3-120">説明</span><span class="sxs-lookup"><span data-stu-id="9b6a3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9b6a3-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="9b6a3-121">InvokeMethod</span></span>|<span data-ttu-id="9b6a3-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9b6a3-122">xs:string</span></span>|<span data-ttu-id="9b6a3-123">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="9b6a3-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="9b6a3-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9b6a3-124">AppDomain</span></span>|<span data-ttu-id="9b6a3-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9b6a3-125">xs:string</span></span>|<span data-ttu-id="9b6a3-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="9b6a3-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
