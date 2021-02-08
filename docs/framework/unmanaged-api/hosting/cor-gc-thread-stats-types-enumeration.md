---
description: '詳細情報: COR_GC_THREAD_STATS_TYPES 列挙型'
title: COR_GC_THREAD_STATS_TYPES 列挙体
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
ms.openlocfilehash: 04bc4e11c527b83cf5f1384b1092cc0d084008a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799773"
---
# <a name="cor_gc_thread_stats_types-enumeration"></a><span data-ttu-id="f6702-103">COR_GC_THREAD_STATS_TYPES 列挙体</span><span class="sxs-lookup"><span data-stu-id="f6702-103">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>

<span data-ttu-id="f6702-104">スレッドのガベージコレクションの統計を示します。</span><span class="sxs-lookup"><span data-stu-id="f6702-104">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6702-105">構文</span><span class="sxs-lookup"><span data-stu-id="f6702-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="f6702-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f6702-106">Members</span></span>  
  
|<span data-ttu-id="f6702-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="f6702-107">Member</span></span>|<span data-ttu-id="f6702-108">説明</span><span class="sxs-lookup"><span data-stu-id="f6702-108">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="f6702-109">スレッドには、最新のガベージコレクションで昇格されたバイト数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f6702-109">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6702-110">要件</span><span class="sxs-lookup"><span data-stu-id="f6702-110">Requirements</span></span>  

 <span data-ttu-id="f6702-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6702-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6702-112">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="f6702-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f6702-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6702-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6702-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6702-114">See also</span></span>

- [<span data-ttu-id="f6702-115">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="f6702-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
