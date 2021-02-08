---
description: '詳細情報: 225-TraceCorrelationKeys'
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: c5fdb9305815cdc4df6bbae3e54209d2b5cffd9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778114"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="3940c-103">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="3940c-103">225 - TraceCorrelationKeys</span></span>

## <a name="properties"></a><span data-ttu-id="3940c-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3940c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3940c-105">id</span><span class="sxs-lookup"><span data-stu-id="3940c-105">ID</span></span>|<span data-ttu-id="3940c-106">225</span><span class="sxs-lookup"><span data-stu-id="3940c-106">225</span></span>|  
|<span data-ttu-id="3940c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="3940c-107">Keywords</span></span>|<span data-ttu-id="3940c-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3940c-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="3940c-109">Level</span><span class="sxs-lookup"><span data-stu-id="3940c-109">Level</span></span>|<span data-ttu-id="3940c-110">Information</span><span class="sxs-lookup"><span data-stu-id="3940c-110">Information</span></span>|  
|<span data-ttu-id="3940c-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="3940c-111">Channel</span></span>|<span data-ttu-id="3940c-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="3940c-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3940c-113">説明</span><span class="sxs-lookup"><span data-stu-id="3940c-113">Description</span></span>  

 <span data-ttu-id="3940c-114">このイベントは、ワークフロー サービスでコンテンツ ベースの相関関係が使用されるときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="3940c-114">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="3940c-115">これには、メッセージとインスタンスの相関関係を定義するために適用されている相関関係キーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3940c-115">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3940c-116">Message</span><span class="sxs-lookup"><span data-stu-id="3940c-116">Message</span></span>  

 <span data-ttu-id="3940c-117">親スコープ '%3' の値 '%2' を使用して相関関係キー '%1' が計算されました。</span><span class="sxs-lookup"><span data-stu-id="3940c-117">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3940c-118">詳細</span><span class="sxs-lookup"><span data-stu-id="3940c-118">Details</span></span>  
  
|<span data-ttu-id="3940c-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="3940c-119">Data Item Name</span></span>|<span data-ttu-id="3940c-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="3940c-120">Data Item Type</span></span>|<span data-ttu-id="3940c-121">説明</span><span class="sxs-lookup"><span data-stu-id="3940c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3940c-122">Instance Key</span><span class="sxs-lookup"><span data-stu-id="3940c-122">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="3940c-123">相関関係値から生成されたキー。</span><span class="sxs-lookup"><span data-stu-id="3940c-123">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="3940c-124">値</span><span class="sxs-lookup"><span data-stu-id="3940c-124">Values</span></span>|`xs:string`|<span data-ttu-id="3940c-125">相関関係インスタンス キーの計算に使用された値。</span><span class="sxs-lookup"><span data-stu-id="3940c-125">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="3940c-126">Parent Scope</span><span class="sxs-lookup"><span data-stu-id="3940c-126">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="3940c-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="3940c-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="3940c-128">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="3940c-128">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3940c-129">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="3940c-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3940c-130">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="3940c-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3940c-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3940c-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3940c-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="3940c-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
