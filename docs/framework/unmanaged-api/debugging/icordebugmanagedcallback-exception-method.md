---
description: '詳細については、次の情報を参照してください: の説明:: の例外メソッド'
title: ICorDebugManagedCallback::Exception メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
ms.openlocfilehash: f738c328e1f6edfeb61a1d5e2ba8f9dd827d05dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790972"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="e9f42-103">ICorDebugManagedCallback::Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="e9f42-103">ICorDebugManagedCallback::Exception Method</span></span>

<span data-ttu-id="e9f42-104">マネージコードから例外がスローされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e9f42-104">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f42-105">構文</span><span class="sxs-lookup"><span data-stu-id="e9f42-105">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9f42-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9f42-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="e9f42-107">から例外がスローされたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e9f42-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="e9f42-108">から例外がスローされたスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e9f42-108">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="e9f42-109">からこの値がの場合、 `false` アプリケーションによって例外がまだ処理されていません。それ以外の場合、例外はハンドルされず、プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="e9f42-109">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9f42-110">解説</span><span class="sxs-lookup"><span data-stu-id="e9f42-110">Remarks</span></span>  

 <span data-ttu-id="e9f42-111">スレッドオブジェクトから特定の例外を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e9f42-111">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9f42-112">要件</span><span class="sxs-lookup"><span data-stu-id="e9f42-112">Requirements</span></span>  

 <span data-ttu-id="e9f42-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9f42-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9f42-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9f42-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9f42-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9f42-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9f42-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9f42-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f42-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9f42-117">See also</span></span>

- [<span data-ttu-id="e9f42-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9f42-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
