---
description: '詳細情報: 203-ClientParameterInspectorAfterCallInvoked'
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: bacdc2a74fc2cef6d7e473fa58c0cbbcffffcf16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645023"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="21a97-103">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="21a97-103">203 - ClientParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="21a97-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21a97-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21a97-105">id</span><span class="sxs-lookup"><span data-stu-id="21a97-105">ID</span></span>|<span data-ttu-id="21a97-106">203</span><span class="sxs-lookup"><span data-stu-id="21a97-106">203</span></span>|  
|<span data-ttu-id="21a97-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="21a97-107">Keywords</span></span>|<span data-ttu-id="21a97-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="21a97-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="21a97-109">Level</span><span class="sxs-lookup"><span data-stu-id="21a97-109">Level</span></span>|<span data-ttu-id="21a97-110">Information</span><span class="sxs-lookup"><span data-stu-id="21a97-110">Information</span></span>|  
|<span data-ttu-id="21a97-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="21a97-111">Channel</span></span>|<span data-ttu-id="21a97-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="21a97-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="21a97-113">説明</span><span class="sxs-lookup"><span data-stu-id="21a97-113">Description</span></span>  

 <span data-ttu-id="21a97-114">このイベントは、クライアント パラメーター インスペクターで Service Model が `AfterCall` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="21a97-114">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="21a97-115">Message</span><span class="sxs-lookup"><span data-stu-id="21a97-115">Message</span></span>  

 <span data-ttu-id="21a97-116">ディスパッチャーが型 '%1' の ClientParameterInspector で 'AfterCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="21a97-116">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="21a97-117">詳細</span><span class="sxs-lookup"><span data-stu-id="21a97-117">Details</span></span>  
  
|<span data-ttu-id="21a97-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="21a97-118">Data Item Name</span></span>|<span data-ttu-id="21a97-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="21a97-119">Data Item Type</span></span>|<span data-ttu-id="21a97-120">説明</span><span class="sxs-lookup"><span data-stu-id="21a97-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="21a97-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="21a97-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="21a97-122">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="21a97-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="21a97-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="21a97-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="21a97-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="21a97-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="21a97-125">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="21a97-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="21a97-126">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="21a97-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="21a97-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="21a97-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="21a97-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="21a97-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
