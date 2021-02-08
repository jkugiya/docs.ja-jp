---
description: '詳細情報: 211-ParameterInspectorAfterCallInvoked'
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: 6168528fb001b5669e80595c8327dc57651e815e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794430"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="8c8a8-103">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="8c8a8-103">211 - ParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="8c8a8-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c8a8-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c8a8-105">id</span><span class="sxs-lookup"><span data-stu-id="8c8a8-105">ID</span></span>|<span data-ttu-id="8c8a8-106">211</span><span class="sxs-lookup"><span data-stu-id="8c8a8-106">211</span></span>|  
|<span data-ttu-id="8c8a8-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="8c8a8-107">Keywords</span></span>|<span data-ttu-id="8c8a8-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8c8a8-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8c8a8-109">Level</span><span class="sxs-lookup"><span data-stu-id="8c8a8-109">Level</span></span>|<span data-ttu-id="8c8a8-110">Information</span><span class="sxs-lookup"><span data-stu-id="8c8a8-110">Information</span></span>|  
|<span data-ttu-id="8c8a8-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="8c8a8-111">Channel</span></span>|<span data-ttu-id="8c8a8-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8c8a8-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c8a8-113">説明</span><span class="sxs-lookup"><span data-stu-id="8c8a8-113">Description</span></span>  

 <span data-ttu-id="8c8a8-114">このイベントは、Service Model が `AfterCall` メソッドを `ParameterInspector` で呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="8c8a8-114">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8c8a8-115">Message</span><span class="sxs-lookup"><span data-stu-id="8c8a8-115">Message</span></span>  

 <span data-ttu-id="8c8a8-116">ディスパッチャーが型 '%1' の ParameterInspector で 'AfterCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="8c8a8-116">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8c8a8-117">詳細</span><span class="sxs-lookup"><span data-stu-id="8c8a8-117">Details</span></span>  
  
|<span data-ttu-id="8c8a8-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8c8a8-118">Data Item Name</span></span>|<span data-ttu-id="8c8a8-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8c8a8-119">Data Item Type</span></span>|<span data-ttu-id="8c8a8-120">説明</span><span class="sxs-lookup"><span data-stu-id="8c8a8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8c8a8-121">種類名</span><span class="sxs-lookup"><span data-stu-id="8c8a8-121">Type Name</span></span>|`xs:string`|<span data-ttu-id="8c8a8-122">呼び出された `ParameterInspector` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="8c8a8-122">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="8c8a8-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="8c8a8-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="8c8a8-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="8c8a8-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8c8a8-125">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="8c8a8-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8c8a8-126">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="8c8a8-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8c8a8-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8c8a8-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8c8a8-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8c8a8-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
