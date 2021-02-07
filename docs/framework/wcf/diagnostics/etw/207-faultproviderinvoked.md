---
description: '詳細情報: 207-FaultProviderInvoked 呼び出されました'
title: 207 - FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 03c4f1669fc61019ccf4d23d2994f136e231fbec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728068"
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="462d9-103">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="462d9-103">207 - FaultProviderInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="462d9-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="462d9-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="462d9-105">id</span><span class="sxs-lookup"><span data-stu-id="462d9-105">ID</span></span>|<span data-ttu-id="462d9-106">207</span><span class="sxs-lookup"><span data-stu-id="462d9-106">207</span></span>|  
|<span data-ttu-id="462d9-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="462d9-107">Keywords</span></span>|<span data-ttu-id="462d9-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="462d9-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="462d9-109">Level</span><span class="sxs-lookup"><span data-stu-id="462d9-109">Level</span></span>|<span data-ttu-id="462d9-110">Information</span><span class="sxs-lookup"><span data-stu-id="462d9-110">Information</span></span>|  
|<span data-ttu-id="462d9-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="462d9-111">Channel</span></span>|<span data-ttu-id="462d9-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="462d9-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="462d9-113">説明</span><span class="sxs-lookup"><span data-stu-id="462d9-113">Description</span></span>  

 <span data-ttu-id="462d9-114">このイベントは、`FaultProvider` が呼び出された後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="462d9-114">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="462d9-115">Message</span><span class="sxs-lookup"><span data-stu-id="462d9-115">Message</span></span>  

 <span data-ttu-id="462d9-116">ディスパッチャーが型 '%1' の FaultProvider を呼び出し、種類 '%2' の例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="462d9-116">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="462d9-117">詳細</span><span class="sxs-lookup"><span data-stu-id="462d9-117">Details</span></span>  
  
|<span data-ttu-id="462d9-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="462d9-118">Data Item Name</span></span>|<span data-ttu-id="462d9-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="462d9-119">Data Item Type</span></span>|<span data-ttu-id="462d9-120">説明</span><span class="sxs-lookup"><span data-stu-id="462d9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="462d9-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="462d9-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="462d9-122">呼び出された `FaultProvider` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="462d9-122">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="462d9-123">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="462d9-123">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="462d9-124">`FaultProvider` の操作対象である例外の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="462d9-124">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="462d9-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="462d9-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="462d9-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="462d9-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="462d9-127">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="462d9-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="462d9-128">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="462d9-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="462d9-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="462d9-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="462d9-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="462d9-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
