---
description: '詳細情報: 204-ClientParameterInspectorBeforeCallInvoked'
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: fa5646da7c48f624dc40f4fcc54a890c0758b4ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644997"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="56491-103">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="56491-103">204 - ClientParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="56491-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="56491-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56491-105">id</span><span class="sxs-lookup"><span data-stu-id="56491-105">ID</span></span>|<span data-ttu-id="56491-106">204</span><span class="sxs-lookup"><span data-stu-id="56491-106">204</span></span>|  
|<span data-ttu-id="56491-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="56491-107">Keywords</span></span>|<span data-ttu-id="56491-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="56491-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="56491-109">Level</span><span class="sxs-lookup"><span data-stu-id="56491-109">Level</span></span>|<span data-ttu-id="56491-110">Information</span><span class="sxs-lookup"><span data-stu-id="56491-110">Information</span></span>|  
|<span data-ttu-id="56491-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="56491-111">Channel</span></span>|<span data-ttu-id="56491-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="56491-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="56491-113">説明</span><span class="sxs-lookup"><span data-stu-id="56491-113">Description</span></span>  

 <span data-ttu-id="56491-114">このイベントは、クライアント パラメーター インスペクターで Service Model が `BeforeCall` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="56491-114">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="56491-115">Message</span><span class="sxs-lookup"><span data-stu-id="56491-115">Message</span></span>  

 <span data-ttu-id="56491-116">ディスパッチャーが型 '%1' の ClientParameterInspector で 'BeforeCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="56491-116">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="56491-117">詳細</span><span class="sxs-lookup"><span data-stu-id="56491-117">Details</span></span>  
  
|<span data-ttu-id="56491-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="56491-118">Data Item Name</span></span>|<span data-ttu-id="56491-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="56491-119">Data Item Type</span></span>|<span data-ttu-id="56491-120">説明</span><span class="sxs-lookup"><span data-stu-id="56491-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="56491-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="56491-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="56491-122">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="56491-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="56491-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="56491-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="56491-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="56491-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="56491-125">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="56491-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="56491-126">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="56491-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="56491-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="56491-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="56491-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="56491-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
