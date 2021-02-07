---
description: '詳細情報: 1124-InvokeMethodIsStatic'
title: 1124 - InvokeMethodIsStatic
ms.date: 03/30/2017
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
ms.openlocfilehash: 86febd9c94c2e4c533eb5ab4349855f6d048a5ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667383"
---
# <a name="1124---invokemethodisstatic"></a><span data-ttu-id="cacf2-103">1124 - InvokeMethodIsStatic</span><span class="sxs-lookup"><span data-stu-id="cacf2-103">1124 - InvokeMethodIsStatic</span></span>

## <a name="properties"></a><span data-ttu-id="cacf2-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cacf2-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cacf2-105">id</span><span class="sxs-lookup"><span data-stu-id="cacf2-105">ID</span></span>|<span data-ttu-id="cacf2-106">1124</span><span class="sxs-lookup"><span data-stu-id="cacf2-106">1124</span></span>|  
|<span data-ttu-id="cacf2-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="cacf2-107">Keywords</span></span>|<span data-ttu-id="cacf2-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cacf2-108">WFRuntime</span></span>|  
|<span data-ttu-id="cacf2-109">Level</span><span class="sxs-lookup"><span data-stu-id="cacf2-109">Level</span></span>|<span data-ttu-id="cacf2-110">Information</span><span class="sxs-lookup"><span data-stu-id="cacf2-110">Information</span></span>|  
|<span data-ttu-id="cacf2-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="cacf2-111">Channel</span></span>|<span data-ttu-id="cacf2-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="cacf2-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cacf2-113">説明</span><span class="sxs-lookup"><span data-stu-id="cacf2-113">Description</span></span>  

 <span data-ttu-id="cacf2-114">CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的であることを示します。</span><span class="sxs-lookup"><span data-stu-id="cacf2-114">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cacf2-115">Message</span><span class="sxs-lookup"><span data-stu-id="cacf2-115">Message</span></span>  

 <span data-ttu-id="cacf2-116">InvokeMethod '%1' - メソッドは Static です。</span><span class="sxs-lookup"><span data-stu-id="cacf2-116">InvokeMethod '%1' - method is Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cacf2-117">詳細</span><span class="sxs-lookup"><span data-stu-id="cacf2-117">Details</span></span>  
  
|<span data-ttu-id="cacf2-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="cacf2-118">Data Item Name</span></span>|<span data-ttu-id="cacf2-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="cacf2-119">Data Item Type</span></span>|<span data-ttu-id="cacf2-120">説明</span><span class="sxs-lookup"><span data-stu-id="cacf2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cacf2-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="cacf2-121">InvokeMethod</span></span>|<span data-ttu-id="cacf2-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="cacf2-122">xs:string</span></span>|<span data-ttu-id="cacf2-123">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="cacf2-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="cacf2-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cacf2-124">AppDomain</span></span>|<span data-ttu-id="cacf2-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="cacf2-125">xs:string</span></span>|<span data-ttu-id="cacf2-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="cacf2-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
