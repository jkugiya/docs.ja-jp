---
description: '詳細情報: 3503-DuplicateCorrelationQuery'
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: a8e1e41aad3aa1b273d8f8a5d7b0768fabe4e658
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778075"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="6e73b-103">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="6e73b-103">3503 - DuplicateCorrelationQuery</span></span>

## <a name="properties"></a><span data-ttu-id="6e73b-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6e73b-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e73b-105">id</span><span class="sxs-lookup"><span data-stu-id="6e73b-105">ID</span></span>|<span data-ttu-id="6e73b-106">3503</span><span class="sxs-lookup"><span data-stu-id="6e73b-106">3503</span></span>|  
|<span data-ttu-id="6e73b-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="6e73b-107">Keywords</span></span>|<span data-ttu-id="6e73b-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="6e73b-108">WFServices</span></span>|  
|<span data-ttu-id="6e73b-109">Level</span><span class="sxs-lookup"><span data-stu-id="6e73b-109">Level</span></span>|<span data-ttu-id="6e73b-110">警告</span><span class="sxs-lookup"><span data-stu-id="6e73b-110">Warning</span></span>|  
|<span data-ttu-id="6e73b-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="6e73b-111">Channel</span></span>|<span data-ttu-id="6e73b-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6e73b-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6e73b-113">説明</span><span class="sxs-lookup"><span data-stu-id="6e73b-113">Description</span></span>  

 <span data-ttu-id="6e73b-114">重複する CorrelationQuery が見つかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="6e73b-114">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="6e73b-115">相関の計算時には、重複するクエリは使用されません。</span><span class="sxs-lookup"><span data-stu-id="6e73b-115">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6e73b-116">Message</span><span class="sxs-lookup"><span data-stu-id="6e73b-116">Message</span></span>  

 <span data-ttu-id="6e73b-117">Where='%1' で重複する CorrelationQuery が見つかりました。</span><span class="sxs-lookup"><span data-stu-id="6e73b-117">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="6e73b-118">相関の計算時には、この重複するクエリは使用されません。</span><span class="sxs-lookup"><span data-stu-id="6e73b-118">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6e73b-119">詳細</span><span class="sxs-lookup"><span data-stu-id="6e73b-119">Details</span></span>  
  
|<span data-ttu-id="6e73b-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6e73b-120">Data Item Name</span></span>|<span data-ttu-id="6e73b-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6e73b-121">Data Item Type</span></span>|<span data-ttu-id="6e73b-122">説明</span><span class="sxs-lookup"><span data-stu-id="6e73b-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6e73b-123">Where</span><span class="sxs-lookup"><span data-stu-id="6e73b-123">Where</span></span>|<span data-ttu-id="6e73b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e73b-124">xs:string</span></span>|<span data-ttu-id="6e73b-125">関連付けクエリの Where 部分。</span><span class="sxs-lookup"><span data-stu-id="6e73b-125">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="6e73b-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6e73b-126">AppDomain</span></span>|<span data-ttu-id="6e73b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e73b-127">xs:string</span></span>|<span data-ttu-id="6e73b-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6e73b-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
