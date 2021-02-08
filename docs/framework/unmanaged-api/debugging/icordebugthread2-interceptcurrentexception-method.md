---
description: '詳細について: ICorDebugThread2:: InterceptCurrentException メソッド'
title: ICorDebugThread2::InterceptCurrentException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: 5bf8d3adf6f5e4a24d8fc5abddb72c0c8963c142
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790712"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="64eba-103">ICorDebugThread2::InterceptCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="64eba-103">ICorDebugThread2::InterceptCurrentException Method</span></span>

<span data-ttu-id="64eba-104">デバッガーがこのスレッドの現在の例外をインターセプトできるようにします。</span><span class="sxs-lookup"><span data-stu-id="64eba-104">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64eba-105">構文</span><span class="sxs-lookup"><span data-stu-id="64eba-105">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64eba-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64eba-106">Parameters</span></span>  

 `pFrame`  
 <span data-ttu-id="64eba-107">からアクティブなスタックフレームを表すテキストフレームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="64eba-107">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64eba-108">解説</span><span class="sxs-lookup"><span data-stu-id="64eba-108">Remarks</span></span>  

 <span data-ttu-id="64eba-109">メソッドは、 `InterceptCurrentException` 例外コールバック ( [ICorDebugManagedCallback2:: exception](icordebugmanagedcallback2-exception-method.md)) と、それに関連付けられています: [: Continue](icordebugcontroller-continue-method.md)への呼び出しの間で呼び出すことができます。[](icordebugmanagedcallback-exception-method.md)</span><span class="sxs-lookup"><span data-stu-id="64eba-109">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64eba-110">要件</span><span class="sxs-lookup"><span data-stu-id="64eba-110">Requirements</span></span>  

 <span data-ttu-id="64eba-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64eba-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64eba-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64eba-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64eba-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64eba-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64eba-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64eba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
