---
description: '詳細については、次のページを参照してください: 216-"通知"'
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: 34c10fbbf61adde102641cb44db6645ea648a646
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794378"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="83ae2-103">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="83ae2-103">216 - MessageSentByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="83ae2-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="83ae2-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="83ae2-105">id</span><span class="sxs-lookup"><span data-stu-id="83ae2-105">ID</span></span>|<span data-ttu-id="83ae2-106">216</span><span class="sxs-lookup"><span data-stu-id="83ae2-106">216</span></span>|  
|<span data-ttu-id="83ae2-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="83ae2-107">Keywords</span></span>|<span data-ttu-id="83ae2-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="83ae2-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="83ae2-109">Level</span><span class="sxs-lookup"><span data-stu-id="83ae2-109">Level</span></span>|<span data-ttu-id="83ae2-110">Information</span><span class="sxs-lookup"><span data-stu-id="83ae2-110">Information</span></span>|  
|<span data-ttu-id="83ae2-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="83ae2-111">Channel</span></span>|<span data-ttu-id="83ae2-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="83ae2-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="83ae2-113">説明</span><span class="sxs-lookup"><span data-stu-id="83ae2-113">Description</span></span>  

 <span data-ttu-id="83ae2-114">このイベントは、TCP ベースのトランスポートがメッセージを送信するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="83ae2-114">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="83ae2-115">トランスポート レベルでは、1 つの操作に対して複数のメッセージが、クライアントとサービス間で交換されることがあります。</span><span class="sxs-lookup"><span data-stu-id="83ae2-115">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="83ae2-116">これはインフラストラクチャの動作によるもので、セキュリティがその一例です。</span><span class="sxs-lookup"><span data-stu-id="83ae2-116">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="83ae2-117">このため、出力さ **れるイベントの** 数は、サービスのバインドとその構成によって異なります。</span><span class="sxs-lookup"><span data-stu-id="83ae2-117">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="83ae2-118">Message</span><span class="sxs-lookup"><span data-stu-id="83ae2-118">Message</span></span>  

 <span data-ttu-id="83ae2-119">トランスポートが '%1' にメッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="83ae2-119">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="83ae2-120">詳細</span><span class="sxs-lookup"><span data-stu-id="83ae2-120">Details</span></span>  
  
|<span data-ttu-id="83ae2-121">データ項目名</span><span class="sxs-lookup"><span data-stu-id="83ae2-121">Data Item Name</span></span>|<span data-ttu-id="83ae2-122">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="83ae2-122">Data Item Type</span></span>|<span data-ttu-id="83ae2-123">説明</span><span class="sxs-lookup"><span data-stu-id="83ae2-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="83ae2-124">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="83ae2-124">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="83ae2-125">要求メッセージが送信されたアドレス。</span><span class="sxs-lookup"><span data-stu-id="83ae2-125">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="83ae2-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="83ae2-126">HostReference</span></span>|<span data-ttu-id="83ae2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="83ae2-127">xs:string</span></span>|<span data-ttu-id="83ae2-128">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="83ae2-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="83ae2-129">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="83ae2-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="83ae2-130">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="83ae2-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="83ae2-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="83ae2-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="83ae2-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="83ae2-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
