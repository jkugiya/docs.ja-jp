---
description: '詳細情報: 303-UserDefinedInformationEventOccured'
title: 303 - UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 51c4acd5d10a2d563dd7fbcebf90b75c64ff20ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794235"
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="7312f-103">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="7312f-103">303 - UserDefinedInformationEventOccured</span></span>

## <a name="properties"></a><span data-ttu-id="7312f-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7312f-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7312f-105">id</span><span class="sxs-lookup"><span data-stu-id="7312f-105">ID</span></span>|<span data-ttu-id="7312f-106">303</span><span class="sxs-lookup"><span data-stu-id="7312f-106">303</span></span>|  
|<span data-ttu-id="7312f-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="7312f-107">Keywords</span></span>|<span data-ttu-id="7312f-108">Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="7312f-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="7312f-109">Level</span><span class="sxs-lookup"><span data-stu-id="7312f-109">Level</span></span>|<span data-ttu-id="7312f-110">Information</span><span class="sxs-lookup"><span data-stu-id="7312f-110">Information</span></span>|  
|<span data-ttu-id="7312f-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="7312f-111">Channel</span></span>|<span data-ttu-id="7312f-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7312f-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7312f-113">説明</span><span class="sxs-lookup"><span data-stu-id="7312f-113">Description</span></span>  

 <span data-ttu-id="7312f-114">このイベントは、ユーザー コードから生成されます。</span><span class="sxs-lookup"><span data-stu-id="7312f-114">This event is emitted from user code.</span></span> <span data-ttu-id="7312f-115">開発者は、カスタム定義の情報イベントがサービスで発生したときに、このイベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="7312f-115">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="7312f-116">これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="7312f-116">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="7312f-117">また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。</span><span class="sxs-lookup"><span data-stu-id="7312f-117">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7312f-118">Message</span><span class="sxs-lookup"><span data-stu-id="7312f-118">Message</span></span>  

 <span data-ttu-id="7312f-119">名前:'%1'、参照:'%2'、ペイロード:%3</span><span class="sxs-lookup"><span data-stu-id="7312f-119">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="7312f-120">詳細</span><span class="sxs-lookup"><span data-stu-id="7312f-120">Details</span></span>  
  
|<span data-ttu-id="7312f-121">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7312f-121">Data Item Name</span></span>|<span data-ttu-id="7312f-122">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7312f-122">Data Item Type</span></span>|<span data-ttu-id="7312f-123">説明</span><span class="sxs-lookup"><span data-stu-id="7312f-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7312f-124">名前</span><span class="sxs-lookup"><span data-stu-id="7312f-124">Name</span></span>|`xs:string`|<span data-ttu-id="7312f-125">イベントのユーザー定義名。</span><span class="sxs-lookup"><span data-stu-id="7312f-125">The user-defined name of the event</span></span>|  
|<span data-ttu-id="7312f-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="7312f-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="7312f-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="7312f-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7312f-128">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="7312f-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7312f-129">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="7312f-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7312f-130">ペイロード</span><span class="sxs-lookup"><span data-stu-id="7312f-130">Payload</span></span>|`xs:string`|<span data-ttu-id="7312f-131">イベントのユーザー定義ペイロード。</span><span class="sxs-lookup"><span data-stu-id="7312f-131">The user-defined payload of the event.</span></span>|
