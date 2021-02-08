---
description: '詳細情報: ETaskType 列挙型'
title: ETaskType 列挙型
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 7cb241765b2ff3b4a3402221c6b3e2b7ff6305c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785407"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="a3b8a-103">ETaskType 列挙型</span><span class="sxs-lookup"><span data-stu-id="a3b8a-103">ETaskType Enumeration</span></span>

<span data-ttu-id="a3b8a-104">[ICLRTask](iclrtask-interface.md)または[IHostTask](ihosttask-interface.md)インターフェイスによって表されるタスクの種類を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-104">Contains values that indicate the type of task that is represented by either an [ICLRTask](iclrtask-interface.md) or an [IHostTask](ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3b8a-105">構文</span><span class="sxs-lookup"><span data-stu-id="a3b8a-105">Syntax</span></span>  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="a3b8a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a3b8a-106">Members</span></span>  
  
|<span data-ttu-id="a3b8a-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="a3b8a-107">Member</span></span>|<span data-ttu-id="a3b8a-108">説明</span><span class="sxs-lookup"><span data-stu-id="a3b8a-108">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="a3b8a-109">インターフェイスは、アプリケーションドメインのアンロードタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-109">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="a3b8a-110">インターフェイスは、デバッガーヘルパータスクを表します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-110">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="a3b8a-111">インターフェイスは、ファイナライザータスクを表します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-111">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="a3b8a-112">インターフェイスは、ガベージコレクションタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-112">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="a3b8a-113">インターフェイスは、ゲートスレッドタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-113">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="a3b8a-114">インターフェイスは、i/o スレッドタスクまたは完了ポートスレッドタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-114">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="a3b8a-115">インターフェイスは、タイマースレッドタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-115">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="a3b8a-116">インターフェイスは、待機スレッドタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-116">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="a3b8a-117">インターフェイスは、ワーカースレッドタスクを表します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-117">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="a3b8a-118">タスクは不明です。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-118">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="a3b8a-119">インターフェイスは、ユーザータスクを表します。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-119">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3b8a-120">要件</span><span class="sxs-lookup"><span data-stu-id="a3b8a-120">Requirements</span></span>  

 <span data-ttu-id="a3b8a-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3b8a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3b8a-122">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a3b8a-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3b8a-123">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3b8a-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3b8a-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3b8a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b8a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3b8a-125">See also</span></span>

- [<span data-ttu-id="a3b8a-126">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="a3b8a-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
