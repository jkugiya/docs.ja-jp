---
description: '詳細情報: 302-Userdefinedwarnings が発生しました'
title: 302 - UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: eb79e32d8993ec60c05e5aaaee1b5e15ee7e32e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794222"
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="f52ca-103">302 - UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="f52ca-103">302 - UserDefinedWarningOccurred</span></span>

## <a name="properties"></a><span data-ttu-id="f52ca-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f52ca-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f52ca-105">id</span><span class="sxs-lookup"><span data-stu-id="f52ca-105">ID</span></span>|<span data-ttu-id="f52ca-106">302</span><span class="sxs-lookup"><span data-stu-id="f52ca-106">302</span></span>|  
|<span data-ttu-id="f52ca-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="f52ca-107">Keywords</span></span>|<span data-ttu-id="f52ca-108">Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="f52ca-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="f52ca-109">Level</span><span class="sxs-lookup"><span data-stu-id="f52ca-109">Level</span></span>|<span data-ttu-id="f52ca-110">警告</span><span class="sxs-lookup"><span data-stu-id="f52ca-110">Warning</span></span>|  
|<span data-ttu-id="f52ca-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="f52ca-111">Channel</span></span>|<span data-ttu-id="f52ca-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f52ca-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f52ca-113">説明</span><span class="sxs-lookup"><span data-stu-id="f52ca-113">Description</span></span>  

 <span data-ttu-id="f52ca-114">このイベントは、ユーザー コードから生成されます。</span><span class="sxs-lookup"><span data-stu-id="f52ca-114">This event is emitted from user code.</span></span> <span data-ttu-id="f52ca-115">開発者は、カスタム定義の警告イベントがサービスで発生したときに、このイベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="f52ca-115">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="f52ca-116">これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="f52ca-116">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="f52ca-117">また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。</span><span class="sxs-lookup"><span data-stu-id="f52ca-117">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f52ca-118">Message</span><span class="sxs-lookup"><span data-stu-id="f52ca-118">Message</span></span>  

 <span data-ttu-id="f52ca-119">名前:'%1'、参照:'%2'、ペイロード:%3</span><span class="sxs-lookup"><span data-stu-id="f52ca-119">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="f52ca-120">詳細</span><span class="sxs-lookup"><span data-stu-id="f52ca-120">Details</span></span>  
  
|<span data-ttu-id="f52ca-121">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f52ca-121">Data Item Name</span></span>|<span data-ttu-id="f52ca-122">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f52ca-122">Data Item Type</span></span>|<span data-ttu-id="f52ca-123">説明</span><span class="sxs-lookup"><span data-stu-id="f52ca-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f52ca-124">名前</span><span class="sxs-lookup"><span data-stu-id="f52ca-124">Name</span></span>|`xs:string`|<span data-ttu-id="f52ca-125">イベントのユーザー定義名。</span><span class="sxs-lookup"><span data-stu-id="f52ca-125">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="f52ca-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="f52ca-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="f52ca-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="f52ca-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f52ca-128">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="f52ca-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f52ca-129">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="f52ca-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f52ca-130">ペイロード</span><span class="sxs-lookup"><span data-stu-id="f52ca-130">Payload</span></span>|`xs:string`|<span data-ttu-id="f52ca-131">イベントのユーザー定義ペイロード。</span><span class="sxs-lookup"><span data-stu-id="f52ca-131">The user-defined payload of the event.</span></span>|
