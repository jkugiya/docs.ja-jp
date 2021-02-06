---
description: '詳細情報: 202-ClientMessageInspectorBeforeSendInvoked'
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 0267304ba805c8f23109c820c8516a27958c3040
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645049"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="40efa-103">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="40efa-103">202 - ClientMessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="40efa-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="40efa-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40efa-105">id</span><span class="sxs-lookup"><span data-stu-id="40efa-105">ID</span></span>|<span data-ttu-id="40efa-106">202</span><span class="sxs-lookup"><span data-stu-id="40efa-106">202</span></span>|  
|<span data-ttu-id="40efa-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="40efa-107">Keywords</span></span>|<span data-ttu-id="40efa-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="40efa-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="40efa-109">Level</span><span class="sxs-lookup"><span data-stu-id="40efa-109">Level</span></span>|<span data-ttu-id="40efa-110">Information</span><span class="sxs-lookup"><span data-stu-id="40efa-110">Information</span></span>|  
|<span data-ttu-id="40efa-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="40efa-111">Channel</span></span>|<span data-ttu-id="40efa-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="40efa-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="40efa-113">説明</span><span class="sxs-lookup"><span data-stu-id="40efa-113">Description</span></span>  

 <span data-ttu-id="40efa-114">このイベントは、クライアント メッセージ インスペクターで Service Model が `BeforeSendRequest` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="40efa-114">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="40efa-115">Message</span><span class="sxs-lookup"><span data-stu-id="40efa-115">Message</span></span>  

 <span data-ttu-id="40efa-116">ディスパッチャーが型 '%1' の ClientMessageInspector で 'BeforeSendRequest' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="40efa-116">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="40efa-117">詳細</span><span class="sxs-lookup"><span data-stu-id="40efa-117">Details</span></span>  
  
|<span data-ttu-id="40efa-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="40efa-118">Data Item Name</span></span>|<span data-ttu-id="40efa-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="40efa-119">Data Item Type</span></span>|<span data-ttu-id="40efa-120">説明</span><span class="sxs-lookup"><span data-stu-id="40efa-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="40efa-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="40efa-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="40efa-122">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="40efa-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="40efa-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="40efa-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="40efa-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="40efa-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="40efa-125">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="40efa-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="40efa-126">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="40efa-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="40efa-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="40efa-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="40efa-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="40efa-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
