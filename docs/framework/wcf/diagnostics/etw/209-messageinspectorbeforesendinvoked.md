---
description: '詳細情報: 209-MessageInspectorBeforeSendInvoked'
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 337ed7d4c62d41d72cb2b4710c9f98f863305aee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728003"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="90f55-103">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="90f55-103">209 - MessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="90f55-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="90f55-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="90f55-105">id</span><span class="sxs-lookup"><span data-stu-id="90f55-105">ID</span></span>|<span data-ttu-id="90f55-106">209</span><span class="sxs-lookup"><span data-stu-id="90f55-106">209</span></span>|  
|<span data-ttu-id="90f55-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="90f55-107">Keywords</span></span>|<span data-ttu-id="90f55-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="90f55-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="90f55-109">Level</span><span class="sxs-lookup"><span data-stu-id="90f55-109">Level</span></span>|<span data-ttu-id="90f55-110">Information</span><span class="sxs-lookup"><span data-stu-id="90f55-110">Information</span></span>|  
|<span data-ttu-id="90f55-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="90f55-111">Channel</span></span>|<span data-ttu-id="90f55-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="90f55-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="90f55-113">説明</span><span class="sxs-lookup"><span data-stu-id="90f55-113">Description</span></span>  

 <span data-ttu-id="90f55-114">このイベントは、メッセージ インスペクターで Service Model が `BeforeSend` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="90f55-114">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="90f55-115">Message</span><span class="sxs-lookup"><span data-stu-id="90f55-115">Message</span></span>  

 <span data-ttu-id="90f55-116">ディスパッチャーが型 '%1' の MessageInspector で 'BeforeSendRequest' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="90f55-116">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="90f55-117">詳細</span><span class="sxs-lookup"><span data-stu-id="90f55-117">Details</span></span>  
  
|<span data-ttu-id="90f55-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="90f55-118">Data Item Name</span></span>|<span data-ttu-id="90f55-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="90f55-119">Data Item Type</span></span>|<span data-ttu-id="90f55-120">説明</span><span class="sxs-lookup"><span data-stu-id="90f55-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="90f55-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="90f55-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="90f55-122">呼び出された `MessageInspector` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="90f55-122">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="90f55-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="90f55-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="90f55-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="90f55-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="90f55-125">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="90f55-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="90f55-126">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="90f55-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="90f55-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="90f55-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="90f55-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="90f55-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
