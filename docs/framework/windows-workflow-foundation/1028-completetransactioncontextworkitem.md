---
description: '詳細情報: 1028-CompleteTransactionContextWorkItem'
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: ae66072769c24ce8d44f92a88cd4232d20bde5f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755461"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="6c59c-103">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="6c59c-103">1028 - CompleteTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="6c59c-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6c59c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6c59c-105">id</span><span class="sxs-lookup"><span data-stu-id="6c59c-105">ID</span></span>|<span data-ttu-id="6c59c-106">1028</span><span class="sxs-lookup"><span data-stu-id="6c59c-106">1028</span></span>|  
|<span data-ttu-id="6c59c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="6c59c-107">Keywords</span></span>|<span data-ttu-id="6c59c-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6c59c-108">WFRuntime</span></span>|  
|<span data-ttu-id="6c59c-109">Level</span><span class="sxs-lookup"><span data-stu-id="6c59c-109">Level</span></span>|<span data-ttu-id="6c59c-110">"詳細"</span><span class="sxs-lookup"><span data-stu-id="6c59c-110">Verbose</span></span>|  
|<span data-ttu-id="6c59c-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="6c59c-111">Channel</span></span>|<span data-ttu-id="6c59c-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6c59c-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6c59c-113">説明</span><span class="sxs-lookup"><span data-stu-id="6c59c-113">Description</span></span>  

 <span data-ttu-id="6c59c-114">TransactionContextWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="6c59c-114">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6c59c-115">Message</span><span class="sxs-lookup"><span data-stu-id="6c59c-115">Message</span></span>  

 <span data-ttu-id="6c59c-116">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の TransactionContextWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="6c59c-116">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6c59c-117">詳細</span><span class="sxs-lookup"><span data-stu-id="6c59c-117">Details</span></span>  
  
|<span data-ttu-id="6c59c-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6c59c-118">Data Item Name</span></span>|<span data-ttu-id="6c59c-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6c59c-119">Data Item Type</span></span>|<span data-ttu-id="6c59c-120">説明</span><span class="sxs-lookup"><span data-stu-id="6c59c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6c59c-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="6c59c-121">Activity</span></span>|<span data-ttu-id="6c59c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="6c59c-122">xs:string</span></span>|<span data-ttu-id="6c59c-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="6c59c-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="6c59c-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6c59c-124">DisplayName</span></span>|<span data-ttu-id="6c59c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="6c59c-125">xs:string</span></span>|<span data-ttu-id="6c59c-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="6c59c-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="6c59c-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6c59c-127">InstanceId</span></span>|<span data-ttu-id="6c59c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="6c59c-128">xs:string</span></span>|<span data-ttu-id="6c59c-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="6c59c-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6c59c-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6c59c-130">AppDomain</span></span>|<span data-ttu-id="6c59c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="6c59c-131">xs:string</span></span>|<span data-ttu-id="6c59c-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6c59c-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
