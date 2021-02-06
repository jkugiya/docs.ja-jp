---
description: '詳細情報: 3550-BufferOutOfOrderMessageNoInstance'
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: cb51f9fa32de1b56560f9593dae2ec82c100dc65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631451"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="70ee3-103">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="70ee3-103">3550 - BufferOutOfOrderMessageNoInstance</span></span>

## <a name="properties"></a><span data-ttu-id="70ee3-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="70ee3-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70ee3-105">id</span><span class="sxs-lookup"><span data-stu-id="70ee3-105">ID</span></span>|<span data-ttu-id="70ee3-106">3550</span><span class="sxs-lookup"><span data-stu-id="70ee3-106">3550</span></span>|  
|<span data-ttu-id="70ee3-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="70ee3-107">Keywords</span></span>|<span data-ttu-id="70ee3-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="70ee3-108">WFServices</span></span>|  
|<span data-ttu-id="70ee3-109">Level</span><span class="sxs-lookup"><span data-stu-id="70ee3-109">Level</span></span>|<span data-ttu-id="70ee3-110">Information</span><span class="sxs-lookup"><span data-stu-id="70ee3-110">Information</span></span>|  
|<span data-ttu-id="70ee3-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="70ee3-111">Channel</span></span>|<span data-ttu-id="70ee3-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="70ee3-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="70ee3-113">説明</span><span class="sxs-lookup"><span data-stu-id="70ee3-113">Description</span></span>  

 <span data-ttu-id="70ee3-114">バッファーされた受信機能が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="70ee3-114">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="70ee3-115">サービス インスタンスがこの特定の操作を処理する準備が整った場合、操作が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="70ee3-115">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="70ee3-116">Message</span><span class="sxs-lookup"><span data-stu-id="70ee3-116">Message</span></span>  

 <span data-ttu-id="70ee3-117">操作 '%1' は現時点では実行できません。</span><span class="sxs-lookup"><span data-stu-id="70ee3-117">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="70ee3-118">サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。</span><span class="sxs-lookup"><span data-stu-id="70ee3-118">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="70ee3-119">詳細</span><span class="sxs-lookup"><span data-stu-id="70ee3-119">Details</span></span>  
  
|<span data-ttu-id="70ee3-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="70ee3-120">Data Item Name</span></span>|<span data-ttu-id="70ee3-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="70ee3-121">Data Item Type</span></span>|<span data-ttu-id="70ee3-122">説明</span><span class="sxs-lookup"><span data-stu-id="70ee3-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="70ee3-123">OperationName</span><span class="sxs-lookup"><span data-stu-id="70ee3-123">OperationName</span></span>|<span data-ttu-id="70ee3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="70ee3-124">xs:string</span></span>|<span data-ttu-id="70ee3-125">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="70ee3-125">The name of the operation.</span></span>|  
|<span data-ttu-id="70ee3-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="70ee3-126">AppDomain</span></span>|<span data-ttu-id="70ee3-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="70ee3-127">xs:string</span></span>|<span data-ttu-id="70ee3-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="70ee3-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
