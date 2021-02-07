---
description: '詳細情報: 4802-DiscoveryClientProtocolExceptionSuppressed'
title: 4802 - DiscoveryClientProtocolExceptionSuppressed
ms.date: 03/30/2017
ms.assetid: 568212f7-1060-4f5c-a7a0-1352c7cc743b
ms.openlocfilehash: 5183e9de704e4da4d93376eeb1dbe22f48bad918
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99744540"
---
# <a name="4802---discoveryclientprotocolexceptionsuppressed"></a><span data-ttu-id="e5f75-103">4802 - DiscoveryClientProtocolExceptionSuppressed</span><span class="sxs-lookup"><span data-stu-id="e5f75-103">4802 - DiscoveryClientProtocolExceptionSuppressed</span></span>

## <a name="properties"></a><span data-ttu-id="e5f75-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e5f75-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5f75-105">id</span><span class="sxs-lookup"><span data-stu-id="e5f75-105">ID</span></span>|<span data-ttu-id="e5f75-106">4802</span><span class="sxs-lookup"><span data-stu-id="e5f75-106">4802</span></span>|  
|<span data-ttu-id="e5f75-107">Keywords</span><span class="sxs-lookup"><span data-stu-id="e5f75-107">Keywords</span></span>|<span data-ttu-id="e5f75-108">探索</span><span class="sxs-lookup"><span data-stu-id="e5f75-108">Discovery</span></span>|  
|<span data-ttu-id="e5f75-109">Level</span><span class="sxs-lookup"><span data-stu-id="e5f75-109">Level</span></span>|<span data-ttu-id="e5f75-110">Information</span><span class="sxs-lookup"><span data-stu-id="e5f75-110">Information</span></span>|  
|<span data-ttu-id="e5f75-111">チャネル</span><span class="sxs-lookup"><span data-stu-id="e5f75-111">Channel</span></span>|<span data-ttu-id="e5f75-112">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e5f75-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e5f75-113">説明</span><span class="sxs-lookup"><span data-stu-id="e5f75-113">Description</span></span>  

 <span data-ttu-id="e5f75-114">このイベントは DiscoveryClient の終了中に ProtocolException が抑制されたときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="e5f75-114">This event is emitted when the a ProtocolException was suppressed while closing the DiscoveryClient.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e5f75-115">Message</span><span class="sxs-lookup"><span data-stu-id="e5f75-115">Message</span></span>  

 <span data-ttu-id="e5f75-116">DiscoveryClient を閉じているときに ProtocolException が抑制されました。</span><span class="sxs-lookup"><span data-stu-id="e5f75-116">A ProtocolException was suppressed while closing the DiscoveryClient.</span></span> <span data-ttu-id="e5f75-117">その理由として、DiscoveryService がまだ DiscoveryClient に応答を送信しようとしていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="e5f75-117">This could be because a DiscoveryService is still trying to send response to the DiscoveryClient.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e5f75-118">詳細</span><span class="sxs-lookup"><span data-stu-id="e5f75-118">Details</span></span>
