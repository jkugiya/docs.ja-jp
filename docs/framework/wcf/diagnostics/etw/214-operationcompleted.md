---
description: '詳細情報: 214-OperationCompleted'
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: aad1ac49667a2ebbf172b5132507584e05d0f03e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794391"
---
# <a name="214---operationcompleted"></a><span data-ttu-id="611f4-103">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="611f4-103">214 - OperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="611f4-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="611f4-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="611f4-105">id</span><span class="sxs-lookup"><span data-stu-id="611f4-105">ID</span></span>|<span data-ttu-id="611f4-106">214</span><span class="sxs-lookup"><span data-stu-id="611f4-106">214</span></span>|  
|<span data-ttu-id="611f4-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="611f4-107">Keywords</span></span>|<span data-ttu-id="611f4-108">HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="611f4-108">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="611f4-109">Level</span><span class="sxs-lookup"><span data-stu-id="611f4-109">Level</span></span>|<span data-ttu-id="611f4-110">Information</span><span class="sxs-lookup"><span data-stu-id="611f4-110">Information</span></span>|  
|<span data-ttu-id="611f4-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="611f4-111">Channel</span></span>|<span data-ttu-id="611f4-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="611f4-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="611f4-113">説明</span><span class="sxs-lookup"><span data-stu-id="611f4-113">Description</span></span>  

 <span data-ttu-id="611f4-114">このイベントは、サービス モデルの既定の `OperationInvoker` が、メソッドから例外がスローされることなく、メソッドへの呼び出しを完了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="611f4-114">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="611f4-115">Message</span><span class="sxs-lookup"><span data-stu-id="611f4-115">Message</span></span>  

 <span data-ttu-id="611f4-116">OperationInvoker がメソッド '%1' への呼び出しを完了しました。</span><span class="sxs-lookup"><span data-stu-id="611f4-116">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="611f4-117">メソッド呼び出し時間は '%2' ミリ秒でした。</span><span class="sxs-lookup"><span data-stu-id="611f4-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="611f4-118">詳細</span><span class="sxs-lookup"><span data-stu-id="611f4-118">Details</span></span>  
  
|<span data-ttu-id="611f4-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="611f4-119">Data Item Name</span></span>|<span data-ttu-id="611f4-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="611f4-120">Data Item Type</span></span>|<span data-ttu-id="611f4-121">説明</span><span class="sxs-lookup"><span data-stu-id="611f4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="611f4-122">メソッド名</span><span class="sxs-lookup"><span data-stu-id="611f4-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="611f4-123">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="611f4-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="611f4-124">Duration</span><span class="sxs-lookup"><span data-stu-id="611f4-124">Duration</span></span>|`xs:long`|<span data-ttu-id="611f4-125">`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="611f4-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="611f4-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="611f4-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="611f4-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="611f4-127">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="611f4-128">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="611f4-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="611f4-129">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="611f4-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="611f4-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="611f4-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="611f4-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="611f4-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
