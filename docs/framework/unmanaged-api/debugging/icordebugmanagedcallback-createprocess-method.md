---
description: 詳細については、次を参照
title: ICorDebugManagedCallback::CreateProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
ms.openlocfilehash: 564c9862dd90431f0626204fdfe49e59b85a124d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791050"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="6d6c2-103">ICorDebugManagedCallback::CreateProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="6d6c2-103">ICorDebugManagedCallback::CreateProcess Method</span></span>

<span data-ttu-id="6d6c2-104">プロセスが初めてアタッチまたは開始されたときにデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="6d6c2-104">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d6c2-105">構文</span><span class="sxs-lookup"><span data-stu-id="6d6c2-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d6c2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d6c2-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="6d6c2-107">からアタッチまたは開始されたプロセスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6d6c2-107">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d6c2-108">解説</span><span class="sxs-lookup"><span data-stu-id="6d6c2-108">Remarks</span></span>  

 <span data-ttu-id="6d6c2-109">このメソッドは、共通言語ランタイムが初期化されるまで呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="6d6c2-109">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="6d6c2-110">ほとんどの [ICorDebug](icordebug-interface.md) メソッドは、コールバックの前に CORDBG_E_NOTREADY を返し `CreateProcess` ます。</span><span class="sxs-lookup"><span data-stu-id="6d6c2-110">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d6c2-111">要件</span><span class="sxs-lookup"><span data-stu-id="6d6c2-111">Requirements</span></span>  

 <span data-ttu-id="6d6c2-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d6c2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d6c2-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d6c2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d6c2-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d6c2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d6c2-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d6c2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d6c2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d6c2-116">See also</span></span>

- [<span data-ttu-id="6d6c2-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d6c2-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
