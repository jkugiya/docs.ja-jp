---
description: '詳細情報: 217-ClientOperationPrepared'
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: eab6a9a654e6e48a8831f238cdf3a3bf7a9f62d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794352"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="afa30-103">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="afa30-103">217 - ClientOperationPrepared</span></span>

## <a name="properties"></a><span data-ttu-id="afa30-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="afa30-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="afa30-105">id</span><span class="sxs-lookup"><span data-stu-id="afa30-105">ID</span></span>|<span data-ttu-id="afa30-106">217</span><span class="sxs-lookup"><span data-stu-id="afa30-106">217</span></span>|  
|<span data-ttu-id="afa30-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="afa30-107">Keywords</span></span>|<span data-ttu-id="afa30-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="afa30-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="afa30-109">Level</span><span class="sxs-lookup"><span data-stu-id="afa30-109">Level</span></span>|<span data-ttu-id="afa30-110">Information</span><span class="sxs-lookup"><span data-stu-id="afa30-110">Information</span></span>|  
|<span data-ttu-id="afa30-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="afa30-111">Channel</span></span>|<span data-ttu-id="afa30-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="afa30-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="afa30-113">説明</span><span class="sxs-lookup"><span data-stu-id="afa30-113">Description</span></span>  

 <span data-ttu-id="afa30-114">このイベントは、操作がサービスに送信される直前に、クライアントによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="afa30-114">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="afa30-115">Message</span><span class="sxs-lookup"><span data-stu-id="afa30-115">Message</span></span>  

 <span data-ttu-id="afa30-116">クライアントは '%2' コントラクトと関連付けられている Action '%1' を実行しています。</span><span class="sxs-lookup"><span data-stu-id="afa30-116">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="afa30-117">メッセージは '%3' に送信されます。</span><span class="sxs-lookup"><span data-stu-id="afa30-117">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="afa30-118">詳細</span><span class="sxs-lookup"><span data-stu-id="afa30-118">Details</span></span>  
  
|<span data-ttu-id="afa30-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="afa30-119">Data Item Name</span></span>|<span data-ttu-id="afa30-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="afa30-120">Data Item Type</span></span>|<span data-ttu-id="afa30-121">説明</span><span class="sxs-lookup"><span data-stu-id="afa30-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="afa30-122">アクション</span><span class="sxs-lookup"><span data-stu-id="afa30-122">Action</span></span>|`xs:string`|<span data-ttu-id="afa30-123">送信メッセージの SOAP アクション ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="afa30-123">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="afa30-124">Contract Name</span><span class="sxs-lookup"><span data-stu-id="afa30-124">Contract Name</span></span>|`xs:string`|<span data-ttu-id="afa30-125">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="afa30-125">The name of the contract.</span></span> <span data-ttu-id="afa30-126">例: ICalculator。</span><span class="sxs-lookup"><span data-stu-id="afa30-126">Example: ICalculator.</span></span>|  
|<span data-ttu-id="afa30-127">宛先</span><span class="sxs-lookup"><span data-stu-id="afa30-127">Destination</span></span>|`xs:string`|<span data-ttu-id="afa30-128">メッセージの送信先となるサービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="afa30-128">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="afa30-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="afa30-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="afa30-130">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="afa30-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="afa30-131">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="afa30-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="afa30-132">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="afa30-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="afa30-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="afa30-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="afa30-134">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="afa30-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
