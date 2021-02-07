---
description: 詳細については、「ICLRMemoryNotificationCallback インターフェイス」を参照してください。
title: ICLRMemoryNotificationCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: 46e53cdf0b7f797b8945237d47fc3b521b08ddb7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689226"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="fd8fb-103">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fd8fb-103">ICLRMemoryNotificationCallback Interface</span></span>

<span data-ttu-id="fd8fb-104">Win32 関数と同様の方法を使用して、ホストがメモリ不足状態を報告できるようにし `CreateMemoryResourceNotification` ます。</span><span class="sxs-lookup"><span data-stu-id="fd8fb-104">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd8fb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="fd8fb-105">Methods</span></span>  
  
|<span data-ttu-id="fd8fb-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="fd8fb-106">Method</span></span>|<span data-ttu-id="fd8fb-107">説明</span><span class="sxs-lookup"><span data-stu-id="fd8fb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd8fb-108">OnMemoryNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="fd8fb-108">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="fd8fb-109">コンピューターのメモリ負荷の共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="fd8fb-109">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd8fb-110">解説</span><span class="sxs-lookup"><span data-stu-id="fd8fb-110">Remarks</span></span>  

 <span data-ttu-id="fd8fb-111">ホストは、このインターフェイスを使用して、 `ICLRMemoryNotificationCallback` CLR のメモリリソースを解放するように要求します。</span><span class="sxs-lookup"><span data-stu-id="fd8fb-111">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd8fb-112">要件</span><span class="sxs-lookup"><span data-stu-id="fd8fb-112">Requirements</span></span>  

 <span data-ttu-id="fd8fb-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd8fb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd8fb-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fd8fb-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd8fb-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="fd8fb-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd8fb-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd8fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd8fb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd8fb-117">See also</span></span>

- [<span data-ttu-id="fd8fb-118">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fd8fb-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="fd8fb-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fd8fb-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
