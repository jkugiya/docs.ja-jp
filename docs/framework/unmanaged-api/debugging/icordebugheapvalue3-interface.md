---
description: 詳細については、「ICorDebugHeapValue3 インターフェイス」を参照してください。
title: ICorDebugHeapValue3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
ms.openlocfilehash: 2483f74e2cfc105fd23c37af6ada467f17b9556b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791466"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="27768-103">ICorDebugHeapValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27768-103">ICorDebugHeapValue3 Interface</span></span>

<span data-ttu-id="27768-104">オブジェクトのモニター ロック プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="27768-104">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="27768-105">このインターフェイスは、ICorDebugHeapValue2 の値とインターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="27768-105">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27768-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="27768-106">Methods</span></span>  
  
|<span data-ttu-id="27768-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="27768-107">Method</span></span>|<span data-ttu-id="27768-108">説明</span><span class="sxs-lookup"><span data-stu-id="27768-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27768-109">GetThreadOwningMonitorLock メソッド</span><span class="sxs-lookup"><span data-stu-id="27768-109">GetThreadOwningMonitorLock Method</span></span>](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="27768-110">このオブジェクトのモニターロックを所有するマネージスレッドを返します。</span><span class="sxs-lookup"><span data-stu-id="27768-110">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="27768-111">GetMonitorEventWaitList メソッド</span><span class="sxs-lookup"><span data-stu-id="27768-111">GetMonitorEventWaitList Method</span></span>](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="27768-112">モニターロックに関連付けられているイベントでキューに登録されているスレッドの順序付きリストを提供します。</span><span class="sxs-lookup"><span data-stu-id="27768-112">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27768-113">解説</span><span class="sxs-lookup"><span data-stu-id="27768-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27768-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="27768-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27768-115">要件</span><span class="sxs-lookup"><span data-stu-id="27768-115">Requirements</span></span>  

 <span data-ttu-id="27768-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27768-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27768-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27768-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27768-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27768-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27768-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27768-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27768-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="27768-120">See also</span></span>

- [<span data-ttu-id="27768-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="27768-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="27768-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="27768-122">Debugging</span></span>](index.md)
