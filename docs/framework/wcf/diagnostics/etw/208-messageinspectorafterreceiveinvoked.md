---
description: '詳細情報: 208-MessageInspectorAfterReceiveInvoked'
title: 208 - MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 29935f5dc8c5dd53c0bf427bfdc9b3858d7fb8fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728055"
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="1e688-103">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="1e688-103">208 - MessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="1e688-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1e688-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e688-105">id</span><span class="sxs-lookup"><span data-stu-id="1e688-105">ID</span></span>|<span data-ttu-id="1e688-106">208</span><span class="sxs-lookup"><span data-stu-id="1e688-106">208</span></span>|  
|<span data-ttu-id="1e688-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="1e688-107">Keywords</span></span>|<span data-ttu-id="1e688-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1e688-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1e688-109">Level</span><span class="sxs-lookup"><span data-stu-id="1e688-109">Level</span></span>|<span data-ttu-id="1e688-110">Information</span><span class="sxs-lookup"><span data-stu-id="1e688-110">Information</span></span>|  
|<span data-ttu-id="1e688-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="1e688-111">Channel</span></span>|<span data-ttu-id="1e688-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1e688-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1e688-113">説明</span><span class="sxs-lookup"><span data-stu-id="1e688-113">Description</span></span>  

 <span data-ttu-id="1e688-114">このイベントは、メッセージ インスペクターで Service Model が `AfterReceive` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="1e688-114">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1e688-115">Message</span><span class="sxs-lookup"><span data-stu-id="1e688-115">Message</span></span>  

 <span data-ttu-id="1e688-116">ディスパッチャーが型 '%1' の MessageInspector で 'AfterReceiveReply' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="1e688-116">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1e688-117">詳細</span><span class="sxs-lookup"><span data-stu-id="1e688-117">Details</span></span>  
  
|<span data-ttu-id="1e688-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1e688-118">Data Item Name</span></span>|<span data-ttu-id="1e688-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1e688-119">Data Item Type</span></span>|<span data-ttu-id="1e688-120">説明</span><span class="sxs-lookup"><span data-stu-id="1e688-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1e688-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="1e688-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="1e688-122">呼び出された `MessageInspector` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="1e688-122">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="1e688-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="1e688-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="1e688-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="1e688-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1e688-125">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="1e688-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1e688-126">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="1e688-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1e688-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1e688-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1e688-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1e688-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
