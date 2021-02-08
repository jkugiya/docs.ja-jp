---
description: '詳細については、次を参照してください: 206-Errorハンドラが呼び出されました'
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: addbcbdea25c7f8e7515b743e98e426476fa0b28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783782"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="d3b90-103">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="d3b90-103">206 - ErrorHandlerInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="d3b90-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d3b90-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3b90-105">id</span><span class="sxs-lookup"><span data-stu-id="d3b90-105">ID</span></span>|<span data-ttu-id="d3b90-106">206</span><span class="sxs-lookup"><span data-stu-id="d3b90-106">206</span></span>|  
|<span data-ttu-id="d3b90-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="d3b90-107">Keywords</span></span>|<span data-ttu-id="d3b90-108">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d3b90-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d3b90-109">Level</span><span class="sxs-lookup"><span data-stu-id="d3b90-109">Level</span></span>|<span data-ttu-id="d3b90-110">Information</span><span class="sxs-lookup"><span data-stu-id="d3b90-110">Information</span></span>|  
|<span data-ttu-id="d3b90-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="d3b90-111">Channel</span></span>|<span data-ttu-id="d3b90-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="d3b90-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d3b90-113">説明</span><span class="sxs-lookup"><span data-stu-id="d3b90-113">Description</span></span>  

 <span data-ttu-id="d3b90-114">このイベントは、サービス操作中に発生した例外を処理する機会が `ErrorHandler` に与えられた後に、生成されます。</span><span class="sxs-lookup"><span data-stu-id="d3b90-114">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d3b90-115">Message</span><span class="sxs-lookup"><span data-stu-id="d3b90-115">Message</span></span>  

 <span data-ttu-id="d3b90-116">ディスパッチャーが型 ' %1 ' の ErrorHandler を呼び出しましたが、型 ' %3 ' の例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="d3b90-116">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="d3b90-117">ErrorHandled == '%2'。</span><span class="sxs-lookup"><span data-stu-id="d3b90-117">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d3b90-118">詳細</span><span class="sxs-lookup"><span data-stu-id="d3b90-118">Details</span></span>  
  
|<span data-ttu-id="d3b90-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d3b90-119">Data Item Name</span></span>|<span data-ttu-id="d3b90-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d3b90-120">Data Item Type</span></span>|<span data-ttu-id="d3b90-121">説明</span><span class="sxs-lookup"><span data-stu-id="d3b90-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d3b90-122">TypeName</span><span class="sxs-lookup"><span data-stu-id="d3b90-122">TypeName</span></span>|`xs:string`|<span data-ttu-id="d3b90-123">呼び出された `ErrorHandler` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="d3b90-123">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="d3b90-124">処理済み</span><span class="sxs-lookup"><span data-stu-id="d3b90-124">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="d3b90-125">エラー ハンドラーがエラーを処理した場合は `true`。それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="d3b90-125">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="d3b90-126">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="d3b90-126">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="d3b90-127">処理対象である例外の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="d3b90-127">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="d3b90-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="d3b90-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="d3b90-129">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="d3b90-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d3b90-130">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="d3b90-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d3b90-131">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="d3b90-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d3b90-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d3b90-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d3b90-133">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d3b90-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
