---
description: '詳細情報: 215-MessageReceivedByTransport'
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: e9645cfc8c4013f8891cb645db7df35477a57412
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794365"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="8b19f-103">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="8b19f-103">215 - MessageReceivedByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="8b19f-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8b19f-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b19f-105">id</span><span class="sxs-lookup"><span data-stu-id="8b19f-105">ID</span></span>|<span data-ttu-id="8b19f-106">215</span><span class="sxs-lookup"><span data-stu-id="8b19f-106">215</span></span>|  
|<span data-ttu-id="8b19f-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="8b19f-107">Keywords</span></span>|<span data-ttu-id="8b19f-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8b19f-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8b19f-109">Level</span><span class="sxs-lookup"><span data-stu-id="8b19f-109">Level</span></span>|<span data-ttu-id="8b19f-110">Information</span><span class="sxs-lookup"><span data-stu-id="8b19f-110">Information</span></span>|  
|<span data-ttu-id="8b19f-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="8b19f-111">Channel</span></span>|<span data-ttu-id="8b19f-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8b19f-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8b19f-113">説明</span><span class="sxs-lookup"><span data-stu-id="8b19f-113">Description</span></span>  

 <span data-ttu-id="8b19f-114">このイベントは、TCP ベースのトランスポートがメッセージを受信するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8b19f-114">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="8b19f-115">トランスポート レベルでは、1 つの操作に対して複数のメッセージが、クライアントとサービス間で交換されることがあります。</span><span class="sxs-lookup"><span data-stu-id="8b19f-115">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="8b19f-116">これはインフラストラクチャの動作によるもので、セキュリティがその一例です。</span><span class="sxs-lookup"><span data-stu-id="8b19f-116">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="8b19f-117">そのため、生成される `MessageReceivedByTransport` イベントの数が、サービスのバインディングとその構成に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="8b19f-117">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b19f-118">一方向トランスポートでは、このイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="8b19f-118">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8b19f-119">Message</span><span class="sxs-lookup"><span data-stu-id="8b19f-119">Message</span></span>  

 <span data-ttu-id="8b19f-120">トランスポートが '%1' からメッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8b19f-120">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8b19f-121">詳細</span><span class="sxs-lookup"><span data-stu-id="8b19f-121">Details</span></span>  
  
|<span data-ttu-id="8b19f-122">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8b19f-122">Data Item Name</span></span>|<span data-ttu-id="8b19f-123">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8b19f-123">Data Item Type</span></span>|<span data-ttu-id="8b19f-124">説明</span><span class="sxs-lookup"><span data-stu-id="8b19f-124">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8b19f-125">Listen Address</span><span class="sxs-lookup"><span data-stu-id="8b19f-125">Listen Address</span></span>|`xs:string`|<span data-ttu-id="8b19f-126">メッセージを受信したアドレス。</span><span class="sxs-lookup"><span data-stu-id="8b19f-126">The address that received the message.</span></span>|  
|<span data-ttu-id="8b19f-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="8b19f-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="8b19f-128">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="8b19f-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8b19f-129">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="8b19f-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8b19f-130">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="8b19f-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8b19f-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8b19f-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8b19f-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8b19f-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
