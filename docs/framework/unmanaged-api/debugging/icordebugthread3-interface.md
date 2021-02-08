---
description: 詳細については、「ICorDebugThread3 インターフェイス」を参照してください。
title: ICorDebugThread3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 88c668f1e08d0843f26d231937c85d80e03bee6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800969"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="73b93-103">ICorDebugThread3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73b93-103">ICorDebugThread3 Interface</span></span>

<span data-ttu-id="73b93-104">とそれに対応するインターフェイス [へのエントリ](icordebugstackwalk-interface.md) ポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="73b93-104">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73b93-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="73b93-105">Methods</span></span>  
  
|<span data-ttu-id="73b93-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="73b93-106">Method</span></span>|<span data-ttu-id="73b93-107">説明</span><span class="sxs-lookup"><span data-stu-id="73b93-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73b93-108">CreateStackWalk メソッド</span><span class="sxs-lookup"><span data-stu-id="73b93-108">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="73b93-109">スタックをアンワインドするスレッドに対し [て、このオブジェクトを](icordebugstackwalk-interface.md) 作成します。</span><span class="sxs-lookup"><span data-stu-id="73b93-109">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="73b93-110">GetActiveInternalFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="73b93-110">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="73b93-111">スタック上の内部フレーム ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="73b93-111">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73b93-112">解説</span><span class="sxs-lookup"><span data-stu-id="73b93-112">Remarks</span></span>  

 <span data-ttu-id="73b93-113">`ICorDebugThread3` は、のように、の論理上の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="73b93-113">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73b93-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="73b93-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73b93-115">要件</span><span class="sxs-lookup"><span data-stu-id="73b93-115">Requirements</span></span>  

 <span data-ttu-id="73b93-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73b93-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73b93-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73b93-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73b93-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73b93-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73b93-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73b93-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73b93-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="73b93-120">See also</span></span>

- [<span data-ttu-id="73b93-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="73b93-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="73b93-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="73b93-122">Debugging</span></span>](index.md)
