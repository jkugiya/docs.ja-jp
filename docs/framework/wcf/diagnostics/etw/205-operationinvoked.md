---
description: '詳細情報: 205-OperationInvoked'
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: 09afe4c29c5f56b06bbf524dd13d88ddf2319063
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644971"
---
# <a name="205---operationinvoked"></a><span data-ttu-id="86c7a-103">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="86c7a-103">205 - OperationInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="86c7a-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="86c7a-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86c7a-105">id</span><span class="sxs-lookup"><span data-stu-id="86c7a-105">ID</span></span>|<span data-ttu-id="86c7a-106">205</span><span class="sxs-lookup"><span data-stu-id="86c7a-106">205</span></span>|  
|<span data-ttu-id="86c7a-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="86c7a-107">Keywords</span></span>|<span data-ttu-id="86c7a-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="86c7a-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="86c7a-109">Level</span><span class="sxs-lookup"><span data-stu-id="86c7a-109">Level</span></span>|<span data-ttu-id="86c7a-110">Information</span><span class="sxs-lookup"><span data-stu-id="86c7a-110">Information</span></span>|  
|<span data-ttu-id="86c7a-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="86c7a-111">Channel</span></span>|<span data-ttu-id="86c7a-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="86c7a-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="86c7a-113">説明</span><span class="sxs-lookup"><span data-stu-id="86c7a-113">Description</span></span>  

 <span data-ttu-id="86c7a-114">このイベントは、サービス モデルの既定の `OperationInvoker` がメソッドの呼び出しを開始する直前に生成されます。</span><span class="sxs-lookup"><span data-stu-id="86c7a-114">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="86c7a-115">Message</span><span class="sxs-lookup"><span data-stu-id="86c7a-115">Message</span></span>  

 <span data-ttu-id="86c7a-116">OperationInvoker が '%1' メソッドを呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="86c7a-116">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="86c7a-117">呼び出し元の情報: '%2'。</span><span class="sxs-lookup"><span data-stu-id="86c7a-117">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="86c7a-118">詳細</span><span class="sxs-lookup"><span data-stu-id="86c7a-118">Details</span></span>  
  
|<span data-ttu-id="86c7a-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="86c7a-119">Data Item Name</span></span>|<span data-ttu-id="86c7a-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="86c7a-120">Data Item Type</span></span>|<span data-ttu-id="86c7a-121">説明</span><span class="sxs-lookup"><span data-stu-id="86c7a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="86c7a-122">メソッド名</span><span class="sxs-lookup"><span data-stu-id="86c7a-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="86c7a-123">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="86c7a-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="86c7a-124">呼び出し元情報</span><span class="sxs-lookup"><span data-stu-id="86c7a-124">Caller Information</span></span>|`xs:string`|<span data-ttu-id="86c7a-125">クライアントの IP アドレスとポート番号。'&lt;IP アドレス&gt;:&lt;ポート番号&gt;' の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="86c7a-125">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="86c7a-126">この 2 つの値は、操作コンテキスト内の 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' メッセージ プロパティから取得します。</span><span class="sxs-lookup"><span data-stu-id="86c7a-126">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="86c7a-127">TCP 以外のバインドの場合、この値は `null` になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="86c7a-127">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="86c7a-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="86c7a-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="86c7a-129">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="86c7a-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="86c7a-130">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="86c7a-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="86c7a-131">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="86c7a-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="86c7a-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="86c7a-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="86c7a-133">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="86c7a-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
