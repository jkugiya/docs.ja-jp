---
description: '詳細について: 1027-StartTransactionContextWorkItem'
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: e7f81a5998d948d3042b51dcdf20fbb1c88ad266
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755474"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="319e0-103">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="319e0-103">1027 - StartTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="319e0-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="319e0-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="319e0-105">id</span><span class="sxs-lookup"><span data-stu-id="319e0-105">ID</span></span>|<span data-ttu-id="319e0-106">1027</span><span class="sxs-lookup"><span data-stu-id="319e0-106">1027</span></span>|  
|<span data-ttu-id="319e0-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="319e0-107">Keywords</span></span>|<span data-ttu-id="319e0-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="319e0-108">WFRuntime</span></span>|  
|<span data-ttu-id="319e0-109">Level</span><span class="sxs-lookup"><span data-stu-id="319e0-109">Level</span></span>|<span data-ttu-id="319e0-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="319e0-110">Verbose</span></span>|  
|<span data-ttu-id="319e0-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="319e0-111">Channel</span></span>|<span data-ttu-id="319e0-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="319e0-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="319e0-113">説明</span><span class="sxs-lookup"><span data-stu-id="319e0-113">Description</span></span>  

 <span data-ttu-id="319e0-114">TransactionContextWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="319e0-114">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="319e0-115">Message</span><span class="sxs-lookup"><span data-stu-id="319e0-115">Message</span></span>  

 <span data-ttu-id="319e0-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の TransactionContextWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="319e0-116">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="319e0-117">詳細</span><span class="sxs-lookup"><span data-stu-id="319e0-117">Details</span></span>  
  
|<span data-ttu-id="319e0-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="319e0-118">Data Item Name</span></span>|<span data-ttu-id="319e0-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="319e0-119">Data Item Type</span></span>|<span data-ttu-id="319e0-120">説明</span><span class="sxs-lookup"><span data-stu-id="319e0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="319e0-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="319e0-121">Activity</span></span>|<span data-ttu-id="319e0-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="319e0-122">xs:string</span></span>|<span data-ttu-id="319e0-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="319e0-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="319e0-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="319e0-124">DisplayName</span></span>|<span data-ttu-id="319e0-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="319e0-125">xs:string</span></span>|<span data-ttu-id="319e0-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="319e0-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="319e0-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="319e0-127">InstanceId</span></span>|<span data-ttu-id="319e0-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="319e0-128">xs:string</span></span>|<span data-ttu-id="319e0-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="319e0-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="319e0-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="319e0-130">AppDomain</span></span>|<span data-ttu-id="319e0-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="319e0-131">xs:string</span></span>|<span data-ttu-id="319e0-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="319e0-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
