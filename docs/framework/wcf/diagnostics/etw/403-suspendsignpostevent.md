---
description: '詳細情報: 403-SuspendSignpostEvent'
title: 403 - SuspendSignpostEvent
ms.date: 03/30/2017
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
ms.openlocfilehash: 4e601920c94ed99c25a1c969508798f65f5348bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99656424"
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="9cdec-103">403 - SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="9cdec-103">403 - SuspendSignpostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="9cdec-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9cdec-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9cdec-105">id</span><span class="sxs-lookup"><span data-stu-id="9cdec-105">ID</span></span>|<span data-ttu-id="9cdec-106">403</span><span class="sxs-lookup"><span data-stu-id="9cdec-106">403</span></span>|  
|<span data-ttu-id="9cdec-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="9cdec-107">Keywords</span></span>|<span data-ttu-id="9cdec-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9cdec-108">Troubleshooting</span></span>|  
|<span data-ttu-id="9cdec-109">Level</span><span class="sxs-lookup"><span data-stu-id="9cdec-109">Level</span></span>|<span data-ttu-id="9cdec-110">Information</span><span class="sxs-lookup"><span data-stu-id="9cdec-110">Information</span></span>|  
|<span data-ttu-id="9cdec-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="9cdec-111">Channel</span></span>|<span data-ttu-id="9cdec-112">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9cdec-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9cdec-113">説明</span><span class="sxs-lookup"><span data-stu-id="9cdec-113">Description</span></span>  

 <span data-ttu-id="9cdec-114">このイベントは、エンド ツー エンド アクティビティの中断を示します。</span><span class="sxs-lookup"><span data-stu-id="9cdec-114">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="9cdec-115">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="9cdec-115">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9cdec-116">Message</span><span class="sxs-lookup"><span data-stu-id="9cdec-116">Message</span></span>  

 <span data-ttu-id="9cdec-117">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="9cdec-117">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9cdec-118">詳細</span><span class="sxs-lookup"><span data-stu-id="9cdec-118">Details</span></span>  
  
|<span data-ttu-id="9cdec-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9cdec-119">Data Item Name</span></span>|<span data-ttu-id="9cdec-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9cdec-120">Data Item Type</span></span>|<span data-ttu-id="9cdec-121">説明</span><span class="sxs-lookup"><span data-stu-id="9cdec-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9cdec-122">Extended Data</span><span class="sxs-lookup"><span data-stu-id="9cdec-122">Extended Data</span></span>|`xs:string`|<span data-ttu-id="9cdec-123">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="9cdec-123">The name of the activity.</span></span>|  
|<span data-ttu-id="9cdec-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9cdec-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9cdec-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="9cdec-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
