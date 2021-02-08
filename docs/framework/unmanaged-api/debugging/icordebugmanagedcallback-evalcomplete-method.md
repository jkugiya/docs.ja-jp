---
description: 詳細については、次を参照
title: ICorDebugManagedCallback::EvalComplete メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
ms.openlocfilehash: 729b00bc630ef5d6e508b75bd6483580f1dd75b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791028"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="98299-103">ICorDebugManagedCallback::EvalComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="98299-103">ICorDebugManagedCallback::EvalComplete Method</span></span>

<span data-ttu-id="98299-104">評価が完了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="98299-104">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98299-105">構文</span><span class="sxs-lookup"><span data-stu-id="98299-105">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98299-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98299-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="98299-107">から評価が実行されたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="98299-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="98299-108">から評価が実行されたスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="98299-108">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="98299-109">から評価を実行したコードを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="98299-109">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98299-110">要件</span><span class="sxs-lookup"><span data-stu-id="98299-110">Requirements</span></span>  

 <span data-ttu-id="98299-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98299-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98299-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98299-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98299-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98299-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98299-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98299-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98299-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="98299-115">See also</span></span>

- [<span data-ttu-id="98299-116">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98299-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
