---
description: '詳細情報: 4817-Innerchannelを失敗とする'
title: 4817 - InnerChannelCreationFailed
ms.date: 03/30/2017
ms.assetid: c1a20619-beda-49b9-bb64-76b6a009c32b
ms.openlocfilehash: ae6dae8a6ffd090a192301bd9236413765c4f16e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783652"
---
# <a name="4817---innerchannelcreationfailed"></a><span data-ttu-id="d570c-103">4817 - InnerChannelCreationFailed</span><span class="sxs-lookup"><span data-stu-id="d570c-103">4817 - InnerChannelCreationFailed</span></span>

## <a name="properties"></a><span data-ttu-id="d570c-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d570c-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d570c-105">id</span><span class="sxs-lookup"><span data-stu-id="d570c-105">ID</span></span>|<span data-ttu-id="d570c-106">4817</span><span class="sxs-lookup"><span data-stu-id="d570c-106">4817</span></span>|  
|<span data-ttu-id="d570c-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="d570c-107">Keywords</span></span>|<span data-ttu-id="d570c-108">探索</span><span class="sxs-lookup"><span data-stu-id="d570c-108">Discovery</span></span>|  
|<span data-ttu-id="d570c-109">Level</span><span class="sxs-lookup"><span data-stu-id="d570c-109">Level</span></span>|<span data-ttu-id="d570c-110">警告</span><span class="sxs-lookup"><span data-stu-id="d570c-110">Warning</span></span>|  
|<span data-ttu-id="d570c-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="d570c-111">Channel</span></span>|<span data-ttu-id="d570c-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d570c-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d570c-113">説明</span><span class="sxs-lookup"><span data-stu-id="d570c-113">Description</span></span>  

 <span data-ttu-id="d570c-114">このイベントは、DiscoveryClientChannel が、探索されたエンドポイントを使用してチャネルを作成できなかったときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="d570c-114">This event is emitted when the DiscoveryClientChannel failed to create the channel with a discovered endpoint.</span></span> <span data-ttu-id="d570c-115">DiscoveryClientChannel は、次に使用可能な探索されたエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="d570c-115">The DiscoveryClientChannel will now attempt to use the next available discovered endpoint.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d570c-116">Message</span><span class="sxs-lookup"><span data-stu-id="d570c-116">Message</span></span>  

 <span data-ttu-id="d570c-117">DiscoveryClientChannel は、EndpointAddress='%1' および Via='%2' の探索されたエンドポイントを使用して、チャネルを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="d570c-117">The DiscoveryClientChannel failed to create the channel with a discovered endpoint with EndpointAddress='%1' and Via='%2'.</span></span> <span data-ttu-id="d570c-118">DiscoveryClientChannel は、次に使用可能な探索されたエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="d570c-118">The DiscoveryClientChannel will now attempt to use the next available discovered endpoint.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d570c-119">詳細</span><span class="sxs-lookup"><span data-stu-id="d570c-119">Details</span></span>
