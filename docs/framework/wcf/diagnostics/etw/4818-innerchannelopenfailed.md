---
description: '詳細情報: 4818-InnerChannelOpenFailed'
title: 4818 - InnerChannelOpenFailed
ms.date: 03/30/2017
ms.assetid: c8ac6447-4fbb-4e08-ab26-91acae48dd11
ms.openlocfilehash: cc34d88b27d5a9d7344e00e00b2ee0c4e9d96cc1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783626"
---
# <a name="4818---innerchannelopenfailed"></a><span data-ttu-id="0893a-103">4818 - InnerChannelOpenFailed</span><span class="sxs-lookup"><span data-stu-id="0893a-103">4818 - InnerChannelOpenFailed</span></span>

## <a name="properties"></a><span data-ttu-id="0893a-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0893a-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0893a-105">id</span><span class="sxs-lookup"><span data-stu-id="0893a-105">ID</span></span>|<span data-ttu-id="0893a-106">4818</span><span class="sxs-lookup"><span data-stu-id="0893a-106">4818</span></span>|  
|<span data-ttu-id="0893a-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="0893a-107">Keywords</span></span>|<span data-ttu-id="0893a-108">探索</span><span class="sxs-lookup"><span data-stu-id="0893a-108">Discovery</span></span>|  
|<span data-ttu-id="0893a-109">Level</span><span class="sxs-lookup"><span data-stu-id="0893a-109">Level</span></span>|<span data-ttu-id="0893a-110">警告</span><span class="sxs-lookup"><span data-stu-id="0893a-110">Warning</span></span>|  
|<span data-ttu-id="0893a-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="0893a-111">Channel</span></span>|<span data-ttu-id="0893a-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0893a-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0893a-113">説明</span><span class="sxs-lookup"><span data-stu-id="0893a-113">Description</span></span>  

 <span data-ttu-id="0893a-114">このイベントは、DiscoveryClientChannel が、探索されたエンドポイントを使用してチャネルを開くことができなかったときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="0893a-114">This event is emitted when the DiscoveryClientChannel failed to open the channel with a discovered endpoint.</span></span> <span data-ttu-id="0893a-115">DiscoveryClientChannel は、次に使用可能な探索されたエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0893a-115">The DiscoveryClientChannel will now attempt to use the next available discovered endpoint.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0893a-116">Message</span><span class="sxs-lookup"><span data-stu-id="0893a-116">Message</span></span>  

 <span data-ttu-id="0893a-117">DiscoveryClientChannel は、EndpointAddress='%1' および Via='%2' の探索されたエンドポイントを使用して、チャネルを開くことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="0893a-117">The DiscoveryClientChannel failed to open the channel with a discovered endpoint with EndpointAddress='%1' and Via='%2'.</span></span> <span data-ttu-id="0893a-118">DiscoveryClientChannel は、次に使用可能な探索されたエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0893a-118">The DiscoveryClientChannel will now attempt to use the next available discovered endpoint.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0893a-119">詳細</span><span class="sxs-lookup"><span data-stu-id="0893a-119">Details</span></span>
