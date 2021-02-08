---
description: '詳細情報: 219-ServiceException'
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: b2ac12d6c5c68517b085b39dd7d0f81c39db9ebd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794326"
---
# <a name="219---serviceexception"></a><span data-ttu-id="2b16a-103">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="2b16a-103">219 - ServiceException</span></span>

## <a name="properties"></a><span data-ttu-id="2b16a-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2b16a-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b16a-105">id</span><span class="sxs-lookup"><span data-stu-id="2b16a-105">ID</span></span>|<span data-ttu-id="2b16a-106">219</span><span class="sxs-lookup"><span data-stu-id="2b16a-106">219</span></span>|  
|<span data-ttu-id="2b16a-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="2b16a-107">Keywords</span></span>|<span data-ttu-id="2b16a-108">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2b16a-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2b16a-109">Level</span><span class="sxs-lookup"><span data-stu-id="2b16a-109">Level</span></span>|<span data-ttu-id="2b16a-110">エラー</span><span class="sxs-lookup"><span data-stu-id="2b16a-110">Error</span></span>|  
|<span data-ttu-id="2b16a-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="2b16a-111">Channel</span></span>|<span data-ttu-id="2b16a-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2b16a-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2b16a-113">説明</span><span class="sxs-lookup"><span data-stu-id="2b16a-113">Description</span></span>  

 <span data-ttu-id="2b16a-114">このイベントは、WCF サービスがハンドルされない例外を検出した場合に生成されます。</span><span class="sxs-lookup"><span data-stu-id="2b16a-114">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="2b16a-115">これには、アクティベーション中のハンドルされない例外、メッセージ処理中のハンドルされない例外、およびユーザー コード内でのハンドルされない例外が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2b16a-115">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2b16a-116">Message</span><span class="sxs-lookup"><span data-stu-id="2b16a-116">Message</span></span>  

 <span data-ttu-id="2b16a-117">メッセージの処理中に種類 '%2' のハンドルされない例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="2b16a-117">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="2b16a-118">完全な例外 ToString: %1。</span><span class="sxs-lookup"><span data-stu-id="2b16a-118">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2b16a-119">詳細</span><span class="sxs-lookup"><span data-stu-id="2b16a-119">Details</span></span>  
  
|<span data-ttu-id="2b16a-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2b16a-120">Data Item Name</span></span>|<span data-ttu-id="2b16a-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2b16a-121">Data Item Type</span></span>|<span data-ttu-id="2b16a-122">説明</span><span class="sxs-lookup"><span data-stu-id="2b16a-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2b16a-123">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="2b16a-123">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="2b16a-124">CLR 例外に対して `ToString`() を呼び出した結果。</span><span class="sxs-lookup"><span data-stu-id="2b16a-124">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="2b16a-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="2b16a-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="2b16a-126">例外の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="2b16a-126">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="2b16a-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="2b16a-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="2b16a-128">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="2b16a-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2b16a-129">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="2b16a-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2b16a-130">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="2b16a-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2b16a-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2b16a-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2b16a-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2b16a-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
