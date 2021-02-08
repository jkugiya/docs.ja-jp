---
description: '詳細情報: 223-OperationFaulted'
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: e4155516e07568d4ee4ca76d63754ec4171e1064
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794287"
---
# <a name="223---operationfaulted"></a><span data-ttu-id="eee88-103">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="eee88-103">223 - OperationFaulted</span></span>

## <a name="properties"></a><span data-ttu-id="eee88-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="eee88-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eee88-105">id</span><span class="sxs-lookup"><span data-stu-id="eee88-105">ID</span></span>|<span data-ttu-id="eee88-106">223</span><span class="sxs-lookup"><span data-stu-id="eee88-106">223</span></span>|  
|<span data-ttu-id="eee88-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="eee88-107">Keywords</span></span>|<span data-ttu-id="eee88-108">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="eee88-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="eee88-109">Level</span><span class="sxs-lookup"><span data-stu-id="eee88-109">Level</span></span>|<span data-ttu-id="eee88-110">警告</span><span class="sxs-lookup"><span data-stu-id="eee88-110">Warning</span></span>|  
|<span data-ttu-id="eee88-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="eee88-111">Channel</span></span>|<span data-ttu-id="eee88-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="eee88-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eee88-113">説明</span><span class="sxs-lookup"><span data-stu-id="eee88-113">Description</span></span>  

 <span data-ttu-id="eee88-114">このイベントは、サービス モデルの既定の `OperationInvoker` が、そのメソッドを呼び出している間に `FaultException` から派生する例外に遭遇すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="eee88-114">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eee88-115">Message</span><span class="sxs-lookup"><span data-stu-id="eee88-115">Message</span></span>  

 <span data-ttu-id="eee88-116">OperationInvoker によって呼び出されたメソッド '%1' で FaultException がスローされました。</span><span class="sxs-lookup"><span data-stu-id="eee88-116">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="eee88-117">メソッド呼び出し時間は '%2' ミリ秒でした。</span><span class="sxs-lookup"><span data-stu-id="eee88-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eee88-118">詳細</span><span class="sxs-lookup"><span data-stu-id="eee88-118">Details</span></span>  
  
|<span data-ttu-id="eee88-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="eee88-119">Data Item Name</span></span>|<span data-ttu-id="eee88-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="eee88-120">Data Item Type</span></span>|<span data-ttu-id="eee88-121">説明</span><span class="sxs-lookup"><span data-stu-id="eee88-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eee88-122">MethodName</span><span class="sxs-lookup"><span data-stu-id="eee88-122">MethodName</span></span>|`xs:string`|<span data-ttu-id="eee88-123">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="eee88-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="eee88-124">Duration</span><span class="sxs-lookup"><span data-stu-id="eee88-124">Duration</span></span>|`xs:long`|<span data-ttu-id="eee88-125">`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="eee88-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="eee88-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="eee88-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="eee88-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="eee88-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="eee88-128">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="eee88-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="eee88-129">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="eee88-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="eee88-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eee88-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="eee88-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="eee88-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
