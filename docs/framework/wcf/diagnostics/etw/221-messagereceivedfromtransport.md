---
description: '詳細情報: 221-MessageReceivedFromTransport'
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 0cc15fa95ae321083afa2792810807971e909e6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803504"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="34c97-103">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="34c97-103">221 - MessageReceivedFromTransport</span></span>

## <a name="properties"></a><span data-ttu-id="34c97-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="34c97-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34c97-105">id</span><span class="sxs-lookup"><span data-stu-id="34c97-105">ID</span></span>|<span data-ttu-id="34c97-106">221</span><span class="sxs-lookup"><span data-stu-id="34c97-106">221</span></span>|  
|<span data-ttu-id="34c97-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="34c97-107">Keywords</span></span>|<span data-ttu-id="34c97-108">EndToEndMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="34c97-108">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="34c97-109">Level</span><span class="sxs-lookup"><span data-stu-id="34c97-109">Level</span></span>|<span data-ttu-id="34c97-110">Information</span><span class="sxs-lookup"><span data-stu-id="34c97-110">Information</span></span>|  
|<span data-ttu-id="34c97-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="34c97-111">Channel</span></span>|<span data-ttu-id="34c97-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="34c97-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="34c97-113">説明</span><span class="sxs-lookup"><span data-stu-id="34c97-113">Description</span></span>  

 <span data-ttu-id="34c97-114">このイベントは、サービス モデルがトランスポートからメッセージを受信すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="34c97-114">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="34c97-115">Message</span><span class="sxs-lookup"><span data-stu-id="34c97-115">Message</span></span>  

 <span data-ttu-id="34c97-116">ディスパッチャーがトランスポートからメッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="34c97-116">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="34c97-117">関連付け ID == '%1'。</span><span class="sxs-lookup"><span data-stu-id="34c97-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="34c97-118">詳細</span><span class="sxs-lookup"><span data-stu-id="34c97-118">Details</span></span>  
  
|<span data-ttu-id="34c97-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="34c97-119">Data Item Name</span></span>|<span data-ttu-id="34c97-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="34c97-120">Data Item Type</span></span>|<span data-ttu-id="34c97-121">説明</span><span class="sxs-lookup"><span data-stu-id="34c97-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="34c97-122">関連付け ID</span><span class="sxs-lookup"><span data-stu-id="34c97-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="34c97-123">サービスまたはクライアントからの `MessageSentToTransport` イベントを、反対側の対応する `MessageReceivedFromTransport` と関連付けるのに使用する、アクティビティ ID。</span><span class="sxs-lookup"><span data-stu-id="34c97-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="34c97-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="34c97-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="34c97-125">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="34c97-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="34c97-126">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="34c97-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="34c97-127">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="34c97-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="34c97-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="34c97-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="34c97-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="34c97-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
