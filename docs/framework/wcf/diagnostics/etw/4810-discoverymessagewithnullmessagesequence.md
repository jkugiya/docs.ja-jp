---
description: '詳細については、次を参照してください: 4810-DiscoveryMessageWithNullMessageSequence'
title: 4810 - DiscoveryMessageWithNullMessageSequence
ms.date: 03/30/2017
ms.assetid: aa70573e-8a76-486a-9616-ccca8c7008b6
ms.openlocfilehash: e2c767a0c5a39c75a084c1ebcc114e9d15962cbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760252"
---
# <a name="4810---discoverymessagewithnullmessagesequence"></a><span data-ttu-id="cd59a-103">4810 - DiscoveryMessageWithNullMessageSequence</span><span class="sxs-lookup"><span data-stu-id="cd59a-103">4810 - DiscoveryMessageWithNullMessageSequence</span></span>

## <a name="properties"></a><span data-ttu-id="cd59a-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cd59a-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd59a-105">id</span><span class="sxs-lookup"><span data-stu-id="cd59a-105">ID</span></span>|<span data-ttu-id="cd59a-106">4810</span><span class="sxs-lookup"><span data-stu-id="cd59a-106">4810</span></span>|  
|<span data-ttu-id="cd59a-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="cd59a-107">Keywords</span></span>|<span data-ttu-id="cd59a-108">探索</span><span class="sxs-lookup"><span data-stu-id="cd59a-108">Discovery</span></span>|  
|<span data-ttu-id="cd59a-109">Level</span><span class="sxs-lookup"><span data-stu-id="cd59a-109">Level</span></span>|<span data-ttu-id="cd59a-110">警告</span><span class="sxs-lookup"><span data-stu-id="cd59a-110">Warning</span></span>|  
|<span data-ttu-id="cd59a-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="cd59a-111">Channel</span></span>|<span data-ttu-id="cd59a-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="cd59a-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cd59a-113">説明</span><span class="sxs-lookup"><span data-stu-id="cd59a-113">Description</span></span>  

 <span data-ttu-id="cd59a-114">このイベントは、DiscoveryMessageSequence プロパティがなかったことが原因で探索要求メッセージが DiscoveryClient によってドロップされたときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd59a-114">This event is emitted when the discovery message was dropped by the DiscoveryClient because it did not have the DiscoveryMessageSequence property.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cd59a-115">Message</span><span class="sxs-lookup"><span data-stu-id="cd59a-115">Message</span></span>  

 <span data-ttu-id="cd59a-116">messageId='%2' の %1 メッセージは、DiscoveryMessageSequence プロパティがなかったため、DiscoveryClient によってドロップされました。</span><span class="sxs-lookup"><span data-stu-id="cd59a-116">A %1 message with messageId='%2' was dropped by the DiscoveryClient because it did not have the DiscoveryMessageSequence property.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cd59a-117">詳細</span><span class="sxs-lookup"><span data-stu-id="cd59a-117">Details</span></span>
