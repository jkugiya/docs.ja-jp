---
description: '詳細情報: 218-ClientOperationCompleted'
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 3719b77ce653c5177cf7b92901ecd51982504b83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794339"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="f8ae9-103">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="f8ae9-103">218 - ClientOperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="f8ae9-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f8ae9-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f8ae9-105">id</span><span class="sxs-lookup"><span data-stu-id="f8ae9-105">ID</span></span>|<span data-ttu-id="f8ae9-106">218</span><span class="sxs-lookup"><span data-stu-id="f8ae9-106">218</span></span>|  
|<span data-ttu-id="f8ae9-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="f8ae9-107">Keywords</span></span>|<span data-ttu-id="f8ae9-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f8ae9-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f8ae9-109">Level</span><span class="sxs-lookup"><span data-stu-id="f8ae9-109">Level</span></span>|<span data-ttu-id="f8ae9-110">Information</span><span class="sxs-lookup"><span data-stu-id="f8ae9-110">Information</span></span>|  
|<span data-ttu-id="f8ae9-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="f8ae9-111">Channel</span></span>|<span data-ttu-id="f8ae9-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f8ae9-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f8ae9-113">説明</span><span class="sxs-lookup"><span data-stu-id="f8ae9-113">Description</span></span>  

 <span data-ttu-id="f8ae9-114">このイベントは、ある操作が完了した直後にクライアントによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-114">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="f8ae9-115">一方向の操作の場合は、メッセージが正常に送信された直後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-115">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="f8ae9-116">要求 - 応答の操作の場合は、応答の受信後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-116">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f8ae9-117">Message</span><span class="sxs-lookup"><span data-stu-id="f8ae9-117">Message</span></span>  

 <span data-ttu-id="f8ae9-118">クライアントは '%2' コントラクトと関連付けられている Action '%1' の実行を完了しました。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-118">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="f8ae9-119">メッセージは '%3' に送信されました。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-119">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f8ae9-120">詳細</span><span class="sxs-lookup"><span data-stu-id="f8ae9-120">Details</span></span>  
  
|<span data-ttu-id="f8ae9-121">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f8ae9-121">Data Item Name</span></span>|<span data-ttu-id="f8ae9-122">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f8ae9-122">Data Item Type</span></span>|<span data-ttu-id="f8ae9-123">説明</span><span class="sxs-lookup"><span data-stu-id="f8ae9-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f8ae9-124">アクション</span><span class="sxs-lookup"><span data-stu-id="f8ae9-124">Action</span></span>|<span data-ttu-id="f8ae9-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="f8ae9-125">xs:string</span></span>|<span data-ttu-id="f8ae9-126">送信メッセージの SOAP アクション ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-126">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="f8ae9-127">Contract Name</span><span class="sxs-lookup"><span data-stu-id="f8ae9-127">Contract Name</span></span>|`xs:string`|<span data-ttu-id="f8ae9-128">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-128">The name of the contract.</span></span> <span data-ttu-id="f8ae9-129">例: ICalculator。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-129">Example: ICalculator.</span></span>|  
|<span data-ttu-id="f8ae9-130">宛先</span><span class="sxs-lookup"><span data-stu-id="f8ae9-130">Destination</span></span>|`xs:string`|<span data-ttu-id="f8ae9-131">メッセージの送信先のサービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-131">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="f8ae9-132">HostReference</span><span class="sxs-lookup"><span data-stu-id="f8ae9-132">HostReference</span></span>|`xs:string`|<span data-ttu-id="f8ae9-133">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-133">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f8ae9-134">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-134">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f8ae9-135">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-135">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f8ae9-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f8ae9-136">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f8ae9-137">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f8ae9-137">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
