---
description: '詳細については、次を参照してください: EMemoryAvailable 列挙型'
title: EMemoryAvailable 列挙型
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
ms.openlocfilehash: fdb33b45c354d39b1a52fd815a44041b659181ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785448"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="018ac-103">EMemoryAvailable 列挙型</span><span class="sxs-lookup"><span data-stu-id="018ac-103">EMemoryAvailable Enumeration</span></span>

<span data-ttu-id="018ac-104">コンピューターの空き物理メモリの量を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="018ac-104">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="018ac-105">これらの値は、Windows API の関数から返されるメモリの量が多い場合のイベントに論理的にマップされ `CreateMemoryResourceNotification` ます。</span><span class="sxs-lookup"><span data-stu-id="018ac-105">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="018ac-106">構文</span><span class="sxs-lookup"><span data-stu-id="018ac-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="018ac-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="018ac-107">Members</span></span>  
  
|<span data-ttu-id="018ac-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="018ac-108">Member</span></span>|<span data-ttu-id="018ac-109">説明</span><span class="sxs-lookup"><span data-stu-id="018ac-109">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="018ac-110">十分な物理メモリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="018ac-110">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="018ac-111">使用できる物理メモリが非常に少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="018ac-111">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="018ac-112">使用可能な物理メモリはニュートラルです。</span><span class="sxs-lookup"><span data-stu-id="018ac-112">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="018ac-113">解説</span><span class="sxs-lookup"><span data-stu-id="018ac-113">Remarks</span></span>  

 <span data-ttu-id="018ac-114">この値は、 [ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) メソッドの呼び出しを使用して、ホストによって共通言語ランタイム (CLR) に渡されます。</span><span class="sxs-lookup"><span data-stu-id="018ac-114">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="018ac-115">要件</span><span class="sxs-lookup"><span data-stu-id="018ac-115">Requirements</span></span>  

 <span data-ttu-id="018ac-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="018ac-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="018ac-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="018ac-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="018ac-118">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="018ac-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="018ac-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="018ac-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="018ac-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="018ac-120">See also</span></span>

- [<span data-ttu-id="018ac-121">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="018ac-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
