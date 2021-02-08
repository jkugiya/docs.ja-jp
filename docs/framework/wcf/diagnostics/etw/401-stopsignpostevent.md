---
description: '詳細情報: 401-StopSignPostEvent'
title: 401- StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: 99b6151d902f3f8059b0aa01e6cda290debafda6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793949"
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="7efc7-103">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="7efc7-103">401- StopSignPostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="7efc7-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7efc7-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7efc7-105">id</span><span class="sxs-lookup"><span data-stu-id="7efc7-105">ID</span></span>|<span data-ttu-id="7efc7-106">401</span><span class="sxs-lookup"><span data-stu-id="7efc7-106">401</span></span>|  
|<span data-ttu-id="7efc7-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="7efc7-107">Keywords</span></span>|<span data-ttu-id="7efc7-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="7efc7-108">Troubleshooting</span></span>|  
|<span data-ttu-id="7efc7-109">Level</span><span class="sxs-lookup"><span data-stu-id="7efc7-109">Level</span></span>|<span data-ttu-id="7efc7-110">Information</span><span class="sxs-lookup"><span data-stu-id="7efc7-110">Information</span></span>|  
|<span data-ttu-id="7efc7-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="7efc7-111">Channel</span></span>|<span data-ttu-id="7efc7-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7efc7-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7efc7-113">説明</span><span class="sxs-lookup"><span data-stu-id="7efc7-113">Description</span></span>  

 <span data-ttu-id="7efc7-114">このイベントは、エンド ツー エンド アクティビティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="7efc7-114">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="7efc7-115">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="7efc7-115">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7efc7-116">Message</span><span class="sxs-lookup"><span data-stu-id="7efc7-116">Message</span></span>  

 <span data-ttu-id="7efc7-117">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="7efc7-117">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7efc7-118">詳細</span><span class="sxs-lookup"><span data-stu-id="7efc7-118">Details</span></span>  
  
|<span data-ttu-id="7efc7-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7efc7-119">Data Item Name</span></span>|<span data-ttu-id="7efc7-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7efc7-120">Data Item Type</span></span>|<span data-ttu-id="7efc7-121">説明</span><span class="sxs-lookup"><span data-stu-id="7efc7-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7efc7-122">Extended Data</span><span class="sxs-lookup"><span data-stu-id="7efc7-122">Extended Data</span></span>|`xs:string`|<span data-ttu-id="7efc7-123">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="7efc7-123">The name of the activity.</span></span>|  
|<span data-ttu-id="7efc7-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7efc7-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7efc7-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7efc7-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
