---
description: '詳細情報: 201-ClientMessageInspectorAfterReceiveInvoked'
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 511f8bd039219d031c311f7def7b360b74df1a0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645153"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="2d723-103">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="2d723-103">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="2d723-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2d723-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d723-105">id</span><span class="sxs-lookup"><span data-stu-id="2d723-105">ID</span></span>|<span data-ttu-id="2d723-106">201</span><span class="sxs-lookup"><span data-stu-id="2d723-106">201</span></span>|  
|<span data-ttu-id="2d723-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="2d723-107">Keywords</span></span>|<span data-ttu-id="2d723-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2d723-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2d723-109">Level</span><span class="sxs-lookup"><span data-stu-id="2d723-109">Level</span></span>|<span data-ttu-id="2d723-110">Information</span><span class="sxs-lookup"><span data-stu-id="2d723-110">Information</span></span>|  
|<span data-ttu-id="2d723-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="2d723-111">Channel</span></span>|<span data-ttu-id="2d723-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2d723-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2d723-113">説明</span><span class="sxs-lookup"><span data-stu-id="2d723-113">Description</span></span>  

 <span data-ttu-id="2d723-114">このイベントは、クライアント メッセージ インスペクターで Service Model が `AfterReceiveReply` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="2d723-114">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2d723-115">Message</span><span class="sxs-lookup"><span data-stu-id="2d723-115">Message</span></span>  

 <span data-ttu-id="2d723-116">ディスパッチャーが型 '%1' の ClientMessageInspector で 'AfterReceiveReply' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="2d723-116">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2d723-117">詳細</span><span class="sxs-lookup"><span data-stu-id="2d723-117">Details</span></span>  
  
|<span data-ttu-id="2d723-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2d723-118">Data Item Name</span></span>|<span data-ttu-id="2d723-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2d723-119">Data Item Type</span></span>|<span data-ttu-id="2d723-120">説明</span><span class="sxs-lookup"><span data-stu-id="2d723-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2d723-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="2d723-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="2d723-122">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="2d723-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="2d723-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="2d723-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="2d723-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="2d723-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2d723-125">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="2d723-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2d723-126">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="2d723-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2d723-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2d723-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2d723-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2d723-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
