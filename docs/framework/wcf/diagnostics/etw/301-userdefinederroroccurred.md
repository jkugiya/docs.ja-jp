---
description: '詳細情報: 301-UserDefinedErrorOccurred'
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 15e12bb27e3626f80747498a1387aa90fc461d28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794248"
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="efc73-103">301 - UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="efc73-103">301 - UserDefinedErrorOccurred</span></span>

## <a name="properties"></a><span data-ttu-id="efc73-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="efc73-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="efc73-105">id</span><span class="sxs-lookup"><span data-stu-id="efc73-105">ID</span></span>|<span data-ttu-id="efc73-106">301</span><span class="sxs-lookup"><span data-stu-id="efc73-106">301</span></span>|  
|<span data-ttu-id="efc73-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="efc73-107">Keywords</span></span>|<span data-ttu-id="efc73-108">Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="efc73-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="efc73-109">Level</span><span class="sxs-lookup"><span data-stu-id="efc73-109">Level</span></span>|<span data-ttu-id="efc73-110">エラー</span><span class="sxs-lookup"><span data-stu-id="efc73-110">Error</span></span>|  
|<span data-ttu-id="efc73-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="efc73-111">Channel</span></span>|<span data-ttu-id="efc73-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="efc73-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="efc73-113">説明</span><span class="sxs-lookup"><span data-stu-id="efc73-113">Description</span></span>  

 <span data-ttu-id="efc73-114">このイベントは、ユーザー コードから生成されます。</span><span class="sxs-lookup"><span data-stu-id="efc73-114">This event is emitted from user code.</span></span> <span data-ttu-id="efc73-115">開発者は、カスタム定義のエラー イベントがサービスで発生したときに、このイベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="efc73-115">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="efc73-116">これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="efc73-116">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="efc73-117">また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。</span><span class="sxs-lookup"><span data-stu-id="efc73-117">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="efc73-118">Message</span><span class="sxs-lookup"><span data-stu-id="efc73-118">Message</span></span>  

 <span data-ttu-id="efc73-119">名前:'%1'、参照:'%2'、ペイロード:%3</span><span class="sxs-lookup"><span data-stu-id="efc73-119">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="efc73-120">詳細</span><span class="sxs-lookup"><span data-stu-id="efc73-120">Details</span></span>  
  
|<span data-ttu-id="efc73-121">データ項目名</span><span class="sxs-lookup"><span data-stu-id="efc73-121">Data Item Name</span></span>|<span data-ttu-id="efc73-122">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="efc73-122">Data Item Type</span></span>|<span data-ttu-id="efc73-123">説明</span><span class="sxs-lookup"><span data-stu-id="efc73-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="efc73-124">名前</span><span class="sxs-lookup"><span data-stu-id="efc73-124">Name</span></span>|`xs:string`|<span data-ttu-id="efc73-125">イベントのユーザー定義名。</span><span class="sxs-lookup"><span data-stu-id="efc73-125">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="efc73-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="efc73-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="efc73-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="efc73-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="efc73-128">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="efc73-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="efc73-129">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="efc73-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="efc73-130">ペイロード</span><span class="sxs-lookup"><span data-stu-id="efc73-130">Payload</span></span>|`xs:string`|<span data-ttu-id="efc73-131">イベントのユーザー定義ペイロード。</span><span class="sxs-lookup"><span data-stu-id="efc73-131">The user-defined payload of the event.</span></span>|
