---
description: '詳細情報: 3551-BufferOutOfOrderMessageNoBookmark'
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 573056fed1753ac55c51d9a074047e8eea15e229
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777997"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="09daa-103">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="09daa-103">3551 - BufferOutOfOrderMessageNoBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="09daa-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="09daa-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="09daa-105">id</span><span class="sxs-lookup"><span data-stu-id="09daa-105">ID</span></span>|<span data-ttu-id="09daa-106">3551</span><span class="sxs-lookup"><span data-stu-id="09daa-106">3551</span></span>|  
|<span data-ttu-id="09daa-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="09daa-107">Keywords</span></span>|<span data-ttu-id="09daa-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="09daa-108">WFServices</span></span>|  
|<span data-ttu-id="09daa-109">Level</span><span class="sxs-lookup"><span data-stu-id="09daa-109">Level</span></span>|<span data-ttu-id="09daa-110">Information</span><span class="sxs-lookup"><span data-stu-id="09daa-110">Information</span></span>|  
|<span data-ttu-id="09daa-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="09daa-111">Channel</span></span>|<span data-ttu-id="09daa-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="09daa-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="09daa-113">説明</span><span class="sxs-lookup"><span data-stu-id="09daa-113">Description</span></span>  

 <span data-ttu-id="09daa-114">ブックマークの再開が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="09daa-114">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="09daa-115">サービス インスタンスがこの特定の操作を処理する準備が整ったら、バッファーされた受信操作が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="09daa-115">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="09daa-116">Message</span><span class="sxs-lookup"><span data-stu-id="09daa-116">Message</span></span>  

 <span data-ttu-id="09daa-117">サービス インスタンス '%1' での操作 '%2' は現時点では実行できません。</span><span class="sxs-lookup"><span data-stu-id="09daa-117">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="09daa-118">サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。</span><span class="sxs-lookup"><span data-stu-id="09daa-118">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="09daa-119">詳細</span><span class="sxs-lookup"><span data-stu-id="09daa-119">Details</span></span>  
  
|<span data-ttu-id="09daa-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="09daa-120">Data Item Name</span></span>|<span data-ttu-id="09daa-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="09daa-121">Data Item Type</span></span>|<span data-ttu-id="09daa-122">説明</span><span class="sxs-lookup"><span data-stu-id="09daa-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="09daa-123">OperationName</span><span class="sxs-lookup"><span data-stu-id="09daa-123">OperationName</span></span>|<span data-ttu-id="09daa-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="09daa-124">xs:string</span></span>|<span data-ttu-id="09daa-125">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="09daa-125">The name of the operation.</span></span>|  
|<span data-ttu-id="09daa-126">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="09daa-126">ServiceInstanceId</span></span>|<span data-ttu-id="09daa-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="09daa-127">xs:string</span></span>|<span data-ttu-id="09daa-128">サービス インスタンスの ID。</span><span class="sxs-lookup"><span data-stu-id="09daa-128">The id of the service instance.</span></span>|  
|<span data-ttu-id="09daa-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="09daa-129">AppDomain</span></span>|<span data-ttu-id="09daa-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="09daa-130">xs:string</span></span>|<span data-ttu-id="09daa-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="09daa-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
