---
description: '詳細情報: 213-ServiceHostStarted'
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 5e2b5b7c633ef053c449ad62c4f8fee40798a386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794417"
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="51c02-103">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="51c02-103">213 - ServiceHostStarted</span></span>

## <a name="properties"></a><span data-ttu-id="51c02-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="51c02-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51c02-105">id</span><span class="sxs-lookup"><span data-stu-id="51c02-105">ID</span></span>|<span data-ttu-id="51c02-106">213</span><span class="sxs-lookup"><span data-stu-id="51c02-106">213</span></span>|  
|<span data-ttu-id="51c02-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="51c02-107">Keywords</span></span>|<span data-ttu-id="51c02-108">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceHost</span><span class="sxs-lookup"><span data-stu-id="51c02-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="51c02-109">Level</span><span class="sxs-lookup"><span data-stu-id="51c02-109">Level</span></span>|<span data-ttu-id="51c02-110">LogAlways</span><span class="sxs-lookup"><span data-stu-id="51c02-110">LogAlways</span></span>|  
|<span data-ttu-id="51c02-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="51c02-111">Channel</span></span>|<span data-ttu-id="51c02-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="51c02-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="51c02-113">説明</span><span class="sxs-lookup"><span data-stu-id="51c02-113">Description</span></span>  

 <span data-ttu-id="51c02-114">このイベントは、Web でホストされているサービス ホストが起動されるときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="51c02-114">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="51c02-115">通常、サービスがメッセージによってアクティブにされた時点で発生します。</span><span class="sxs-lookup"><span data-stu-id="51c02-115">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="51c02-116">また、サービスが自動的に開始するように構成されている場合も発生します。</span><span class="sxs-lookup"><span data-stu-id="51c02-116">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="51c02-117">Message</span><span class="sxs-lookup"><span data-stu-id="51c02-117">Message</span></span>  

 <span data-ttu-id="51c02-118">ServiceHost は '%1' で開始されています。</span><span class="sxs-lookup"><span data-stu-id="51c02-118">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="51c02-119">詳細</span><span class="sxs-lookup"><span data-stu-id="51c02-119">Details</span></span>  
  
|<span data-ttu-id="51c02-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="51c02-120">Data Item Name</span></span>|<span data-ttu-id="51c02-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="51c02-121">Data Item Type</span></span>|<span data-ttu-id="51c02-122">説明</span><span class="sxs-lookup"><span data-stu-id="51c02-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="51c02-123">Service Type Name</span><span class="sxs-lookup"><span data-stu-id="51c02-123">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="51c02-124">サービス実装の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="51c02-124">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="51c02-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="51c02-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="51c02-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="51c02-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="51c02-127">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="51c02-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="51c02-128">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="51c02-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="51c02-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="51c02-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="51c02-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="51c02-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
