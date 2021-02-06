---
description: '詳細情報: 402-StartSignpostEvent'
title: 402 - StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
ms.openlocfilehash: e77cac50be2a2e96fabe1301aaeab7ff74142e5a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99656684"
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="2a9d2-103">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="2a9d2-103">402 - StartSignpostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="2a9d2-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2a9d2-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a9d2-105">id</span><span class="sxs-lookup"><span data-stu-id="2a9d2-105">ID</span></span>|<span data-ttu-id="2a9d2-106">402</span><span class="sxs-lookup"><span data-stu-id="2a9d2-106">402</span></span>|  
|<span data-ttu-id="2a9d2-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="2a9d2-107">Keywords</span></span>|<span data-ttu-id="2a9d2-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2a9d2-108">Troubleshooting</span></span>|  
|<span data-ttu-id="2a9d2-109">Level</span><span class="sxs-lookup"><span data-stu-id="2a9d2-109">Level</span></span>|<span data-ttu-id="2a9d2-110">Information</span><span class="sxs-lookup"><span data-stu-id="2a9d2-110">Information</span></span>|  
|<span data-ttu-id="2a9d2-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="2a9d2-111">Channel</span></span>|<span data-ttu-id="2a9d2-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2a9d2-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2a9d2-113">説明</span><span class="sxs-lookup"><span data-stu-id="2a9d2-113">Description</span></span>  

 <span data-ttu-id="2a9d2-114">このイベントは、エンド ツー エンド アクティビティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="2a9d2-114">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="2a9d2-115">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="2a9d2-115">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2a9d2-116">Message</span><span class="sxs-lookup"><span data-stu-id="2a9d2-116">Message</span></span>  

 <span data-ttu-id="2a9d2-117">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="2a9d2-117">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2a9d2-118">詳細</span><span class="sxs-lookup"><span data-stu-id="2a9d2-118">Details</span></span>  
  
|<span data-ttu-id="2a9d2-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2a9d2-119">Data Item Name</span></span>|<span data-ttu-id="2a9d2-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2a9d2-120">Data Item Type</span></span>|<span data-ttu-id="2a9d2-121">説明</span><span class="sxs-lookup"><span data-stu-id="2a9d2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2a9d2-122">Extended Data</span><span class="sxs-lookup"><span data-stu-id="2a9d2-122">Extended Data</span></span>|`xs:string`|<span data-ttu-id="2a9d2-123">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="2a9d2-123">The name of the activity.</span></span>|  
|<span data-ttu-id="2a9d2-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2a9d2-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2a9d2-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2a9d2-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
