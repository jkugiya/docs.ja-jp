---
description: '詳細については、次を参照してください: 220-通知 Enttotransport'
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 8d76f147c8a31a5aa08c21073cd03e63436095ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794313"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="f0171-103">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="f0171-103">220 - MessageSentToTransport</span></span>

## <a name="properties"></a><span data-ttu-id="f0171-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f0171-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0171-105">Id</span><span class="sxs-lookup"><span data-stu-id="f0171-105">Id</span></span>|<span data-ttu-id="f0171-106">220</span><span class="sxs-lookup"><span data-stu-id="f0171-106">220</span></span>|  
|<span data-ttu-id="f0171-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="f0171-107">Keywords</span></span>|<span data-ttu-id="f0171-108">EndToEndMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f0171-108">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f0171-109">Level</span><span class="sxs-lookup"><span data-stu-id="f0171-109">Level</span></span>|<span data-ttu-id="f0171-110">Information</span><span class="sxs-lookup"><span data-stu-id="f0171-110">Information</span></span>|  
|<span data-ttu-id="f0171-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="f0171-111">Channel</span></span>|<span data-ttu-id="f0171-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f0171-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f0171-113">説明</span><span class="sxs-lookup"><span data-stu-id="f0171-113">Description</span></span>  

 <span data-ttu-id="f0171-114">このイベントは、サービス モデルがトランスポートにメッセージを送信すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="f0171-114">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0171-115">一方向トランスポートでは、このイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="f0171-115">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f0171-116">Message</span><span class="sxs-lookup"><span data-stu-id="f0171-116">Message</span></span>  

 <span data-ttu-id="f0171-117">ディスパッチャーがトランスポートにメッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="f0171-117">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="f0171-118">関連付け ID == '%1'。</span><span class="sxs-lookup"><span data-stu-id="f0171-118">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f0171-119">詳細</span><span class="sxs-lookup"><span data-stu-id="f0171-119">Details</span></span>  
  
|<span data-ttu-id="f0171-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f0171-120">Data Item Name</span></span>|<span data-ttu-id="f0171-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f0171-121">Data Item Type</span></span>|<span data-ttu-id="f0171-122">説明</span><span class="sxs-lookup"><span data-stu-id="f0171-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f0171-123">関連付け ID</span><span class="sxs-lookup"><span data-stu-id="f0171-123">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="f0171-124">サービスまたはクライアントからの `MessageSentToTransport` イベントを、反対側の対応する `MessageReceivedFromTransport` と関連付けるのに使用する、アクティビティ ID。</span><span class="sxs-lookup"><span data-stu-id="f0171-124">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="f0171-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="f0171-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="f0171-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="f0171-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f0171-127">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="f0171-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f0171-128">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="f0171-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f0171-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f0171-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f0171-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f0171-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
