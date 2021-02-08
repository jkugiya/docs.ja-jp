---
description: '詳細情報: 222-OperationFailed'
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: ea07dbabb651413f213db6789f2af8059d2595c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794300"
---
# <a name="222---operationfailed"></a><span data-ttu-id="3e1a2-103">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="3e1a2-103">222 - OperationFailed</span></span>

## <a name="properties"></a><span data-ttu-id="3e1a2-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3e1a2-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3e1a2-105">id</span><span class="sxs-lookup"><span data-stu-id="3e1a2-105">ID</span></span>|<span data-ttu-id="3e1a2-106">222</span><span class="sxs-lookup"><span data-stu-id="3e1a2-106">222</span></span>|  
|<span data-ttu-id="3e1a2-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="3e1a2-107">Keywords</span></span>|<span data-ttu-id="3e1a2-108">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3e1a2-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="3e1a2-109">Level</span><span class="sxs-lookup"><span data-stu-id="3e1a2-109">Level</span></span>|<span data-ttu-id="3e1a2-110">警告</span><span class="sxs-lookup"><span data-stu-id="3e1a2-110">Warning</span></span>|  
|<span data-ttu-id="3e1a2-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="3e1a2-111">Channel</span></span>|<span data-ttu-id="3e1a2-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="3e1a2-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3e1a2-113">説明</span><span class="sxs-lookup"><span data-stu-id="3e1a2-113">Description</span></span>  

 <span data-ttu-id="3e1a2-114">このイベントは、サービス モデルの既定の `OperationInvoker` が、そのメソッドを呼び出している間に例外に遭遇すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="3e1a2-114">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="3e1a2-115">`FaultException` から派生する例外では、このイベントは生成されません。</span><span class="sxs-lookup"><span data-stu-id="3e1a2-115">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3e1a2-116">Message</span><span class="sxs-lookup"><span data-stu-id="3e1a2-116">Message</span></span>  

 <span data-ttu-id="3e1a2-117">OperationInvoker によって呼び出されたメソッド '%1' で、ハンドルされない例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="3e1a2-117">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="3e1a2-118">メソッド呼び出し時間は '%2' ミリ秒でした。</span><span class="sxs-lookup"><span data-stu-id="3e1a2-118">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3e1a2-119">詳細</span><span class="sxs-lookup"><span data-stu-id="3e1a2-119">Details</span></span>  
  
|<span data-ttu-id="3e1a2-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="3e1a2-120">Data Item Name</span></span>|<span data-ttu-id="3e1a2-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="3e1a2-121">Data Item Type</span></span>|<span data-ttu-id="3e1a2-122">説明</span><span class="sxs-lookup"><span data-stu-id="3e1a2-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3e1a2-123">メソッド名</span><span class="sxs-lookup"><span data-stu-id="3e1a2-123">Method Name</span></span>|`xs:string`|<span data-ttu-id="3e1a2-124">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="3e1a2-124">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="3e1a2-125">Duration</span><span class="sxs-lookup"><span data-stu-id="3e1a2-125">Duration</span></span>|`xs:long`|<span data-ttu-id="3e1a2-126">`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="3e1a2-126">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="3e1a2-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="3e1a2-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="3e1a2-128">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="3e1a2-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3e1a2-129">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="3e1a2-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3e1a2-130">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="3e1a2-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3e1a2-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3e1a2-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3e1a2-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="3e1a2-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
