---
description: '詳細については、次を参照してください: BreakpointSetError メソッド'
title: ICorDebugManagedCallback::BreakpointSetError メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
ms.openlocfilehash: cf78b4dc06a71b6ac0eb4f653a00c1b3c6ae464b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791089"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="98a9c-103">ICorDebugManagedCallback::BreakpointSetError メソッド</span><span class="sxs-lookup"><span data-stu-id="98a9c-103">ICorDebugManagedCallback::BreakpointSetError Method</span></span>

<span data-ttu-id="98a9c-104">関数が just-in-time (JIT) コンパイルされる前に設定されたブレークポイントを共通言語ランタイムが正しくバインドできなかったことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="98a9c-104">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a9c-105">構文</span><span class="sxs-lookup"><span data-stu-id="98a9c-105">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98a9c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98a9c-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="98a9c-107">からバインドされていないブレークポイントを含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="98a9c-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="98a9c-108">からバインドされていないブレークポイントを含むスレッドを表す、表示スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="98a9c-108">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="98a9c-109">からバインドされていないブレークポイントを表す ICorDebugBreakpoint オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="98a9c-109">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="98a9c-110">からエラーを示す整数。</span><span class="sxs-lookup"><span data-stu-id="98a9c-110">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98a9c-111">解説</span><span class="sxs-lookup"><span data-stu-id="98a9c-111">Remarks</span></span>  

 <span data-ttu-id="98a9c-112">指定されたブレークポイントはヒットしません。</span><span class="sxs-lookup"><span data-stu-id="98a9c-112">The given breakpoint will never be hit.</span></span> <span data-ttu-id="98a9c-113">デバッガーは、非アクティブ化して再バインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="98a9c-113">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a9c-114">要件</span><span class="sxs-lookup"><span data-stu-id="98a9c-114">Requirements</span></span>  

 <span data-ttu-id="98a9c-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98a9c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a9c-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98a9c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98a9c-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98a9c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98a9c-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98a9c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a9c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="98a9c-119">See also</span></span>

- [<span data-ttu-id="98a9c-120">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98a9c-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
