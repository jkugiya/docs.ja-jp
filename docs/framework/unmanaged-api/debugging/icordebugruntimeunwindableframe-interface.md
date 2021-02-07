---
description: 詳細については、「ICorDebugRuntimeUnwindableFrame インターフェイス」を参照してください。
title: ICorDebugRuntimeUnwindableFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: e83ede8265a400b30f2202115bf47aed6ea43e5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717811"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="a80cd-103">ICorDebugRuntimeUnwindableFrame インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a80cd-103">ICorDebugRuntimeUnwindableFrame Interface</span></span>

<span data-ttu-id="a80cd-104">共通言語ランタイム (CLR: Common Language Runtime) でフレームをアンワインドする必要のあるアンマネージ メソッドに対してサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="a80cd-104">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a80cd-105">解説</span><span class="sxs-lookup"><span data-stu-id="a80cd-105">Remarks</span></span>  

 <span data-ttu-id="a80cd-106">`ICorDebugRuntimeUnwindableFrame` は、テキストフレームインターフェイスの特殊なバージョンです。</span><span class="sxs-lookup"><span data-stu-id="a80cd-106">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="a80cd-107">これは、ランタイムが現在のスタック上のフレームをアンワインドする必要があるアンマネージメソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="a80cd-107">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="a80cd-108">既存のアンワインド規則は、JIT コンパイルコードを使用しないため、機能しません。</span><span class="sxs-lookup"><span data-stu-id="a80cd-108">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="a80cd-109">デバッガーに unwindable フレームが表示された場合、そのフレームをアンワインドするには、 [次](icordebugstackwalk-next-method.md) のメソッドを使用する必要がありますが、検査自体を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a80cd-109">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="a80cd-110">デバッガーは、を受け取ると `ICorDebugRuntimeUnwindableFrame` 、テキストフレームのコンテキストを取得するために [、を](icordebugstackwalk-getcontext-method.md) 呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a80cd-110">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a80cd-111">要件</span><span class="sxs-lookup"><span data-stu-id="a80cd-111">Requirements</span></span>  

 <span data-ttu-id="a80cd-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a80cd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a80cd-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a80cd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a80cd-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a80cd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a80cd-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a80cd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a80cd-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a80cd-116">See also</span></span>

- [<span data-ttu-id="a80cd-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a80cd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a80cd-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a80cd-118">Debugging</span></span>](index.md)
