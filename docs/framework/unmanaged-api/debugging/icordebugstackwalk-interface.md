---
description: 詳細については、「のヘルプ」を参照してください。
title: ICorDebugStackWalk インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: 27dcdfc90829a3a28d81ad28dce0cd4d1d674948
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738092"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="22635-103">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22635-103">ICorDebugStackWalk Interface</span></span>

<span data-ttu-id="22635-104">スレッドのスタック上のマネージド メソッド (フレーム) を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="22635-104">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="22635-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="22635-105">Methods</span></span>  
  
|<span data-ttu-id="22635-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="22635-106">Method</span></span>|<span data-ttu-id="22635-107">説明</span><span class="sxs-lookup"><span data-stu-id="22635-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="22635-108">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="22635-108">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="22635-109">オブジェクト内の現在のフレームのコンテキストを返し `ICorDebugStackWalk` ます。</span><span class="sxs-lookup"><span data-stu-id="22635-109">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="22635-110">SetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="22635-110">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="22635-111">`ICorDebugStackWalk`オブジェクトの現在のコンテキストをスレッドの有効なコンテキストに設定します。</span><span class="sxs-lookup"><span data-stu-id="22635-111">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="22635-112">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="22635-112">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="22635-113">オブジェクトを `ICorDebugStackWalk` 次のフレームに移動します。</span><span class="sxs-lookup"><span data-stu-id="22635-113">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="22635-114">GetFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="22635-114">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="22635-115">オブジェクト内の現在のフレームを取得し `ICorDebugStackWalk` ます。</span><span class="sxs-lookup"><span data-stu-id="22635-115">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22635-116">解説</span><span class="sxs-lookup"><span data-stu-id="22635-116">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22635-117">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="22635-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22635-118">要件</span><span class="sxs-lookup"><span data-stu-id="22635-118">Requirements</span></span>  

 <span data-ttu-id="22635-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22635-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22635-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22635-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22635-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22635-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22635-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22635-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22635-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="22635-123">See also</span></span>

- [<span data-ttu-id="22635-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="22635-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="22635-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="22635-125">Debugging</span></span>](index.md)
