---
description: '詳細情報: 212-ParameterInspectorBeforeCallInvoked'
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: aa02ff22b533855716c212d312396e6de23ace42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794404"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="b51a5-103">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="b51a5-103">212 - ParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="b51a5-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b51a5-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b51a5-105">id</span><span class="sxs-lookup"><span data-stu-id="b51a5-105">ID</span></span>|<span data-ttu-id="b51a5-106">212</span><span class="sxs-lookup"><span data-stu-id="b51a5-106">212</span></span>|  
|<span data-ttu-id="b51a5-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="b51a5-107">Keywords</span></span>|<span data-ttu-id="b51a5-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b51a5-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b51a5-109">Level</span><span class="sxs-lookup"><span data-stu-id="b51a5-109">Level</span></span>|<span data-ttu-id="b51a5-110">Information</span><span class="sxs-lookup"><span data-stu-id="b51a5-110">Information</span></span>|  
|<span data-ttu-id="b51a5-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="b51a5-111">Channel</span></span>|<span data-ttu-id="b51a5-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b51a5-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b51a5-113">説明</span><span class="sxs-lookup"><span data-stu-id="b51a5-113">Description</span></span>  

 <span data-ttu-id="b51a5-114">このイベントは、Service Model が `BeforeCall` メソッドを `ParameterInspector` で呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="b51a5-114">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b51a5-115">Message</span><span class="sxs-lookup"><span data-stu-id="b51a5-115">Message</span></span>  

 <span data-ttu-id="b51a5-116">ディスパッチャーが型 '%1' の ParameterInspector で 'BeforeCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="b51a5-116">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b51a5-117">詳細</span><span class="sxs-lookup"><span data-stu-id="b51a5-117">Details</span></span>  
  
|<span data-ttu-id="b51a5-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b51a5-118">Data Item Name</span></span>|<span data-ttu-id="b51a5-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b51a5-119">Data Item Type</span></span>|<span data-ttu-id="b51a5-120">説明</span><span class="sxs-lookup"><span data-stu-id="b51a5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b51a5-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="b51a5-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="b51a5-122">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="b51a5-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="b51a5-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="b51a5-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="b51a5-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="b51a5-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b51a5-125">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="b51a5-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b51a5-126">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="b51a5-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b51a5-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b51a5-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b51a5-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b51a5-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
