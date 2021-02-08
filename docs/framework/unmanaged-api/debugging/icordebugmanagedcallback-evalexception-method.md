---
description: 詳細については、次を参照
title: ICorDebugManagedCallback::EvalException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
ms.openlocfilehash: 0938276a854020efa897499af8c0fd69c0541124
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790985"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="f3a18-103">ICorDebugManagedCallback::EvalException メソッド</span><span class="sxs-lookup"><span data-stu-id="f3a18-103">ICorDebugManagedCallback::EvalException Method</span></span>

<span data-ttu-id="f3a18-104">ハンドルされない例外で評価が終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f3a18-104">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a18-105">構文</span><span class="sxs-lookup"><span data-stu-id="f3a18-105">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3a18-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3a18-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="f3a18-107">から評価が終了したアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f3a18-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f3a18-108">から評価が終了したスレッドを表す、のスレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f3a18-108">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="f3a18-109">から評価を実行したコードを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f3a18-109">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3a18-110">要件</span><span class="sxs-lookup"><span data-stu-id="f3a18-110">Requirements</span></span>  

 <span data-ttu-id="f3a18-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3a18-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3a18-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3a18-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3a18-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3a18-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3a18-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3a18-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a18-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3a18-115">See also</span></span>

- [<span data-ttu-id="f3a18-116">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3a18-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
