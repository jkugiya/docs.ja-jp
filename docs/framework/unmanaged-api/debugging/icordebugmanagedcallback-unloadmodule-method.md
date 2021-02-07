---
description: '詳細については、次を参照してください: UnloadModule メソッド'
title: ICorDebugManagedCallback::UnloadModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: d8d37b28d7a7d11000c259f1bcde3138634b2498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754057"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="66855-103">ICorDebugManagedCallback::UnloadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="66855-103">ICorDebugManagedCallback::UnloadModule Method</span></span>

<span data-ttu-id="66855-104">共通言語ランタイムモジュール (DLL) がアンロードされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="66855-104">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66855-105">構文</span><span class="sxs-lookup"><span data-stu-id="66855-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66855-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66855-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="66855-107">からモジュールを含んでいるアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="66855-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="66855-108">からモジュールを表す、のモジュールオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="66855-108">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66855-109">解説</span><span class="sxs-lookup"><span data-stu-id="66855-109">Remarks</span></span>  

 <span data-ttu-id="66855-110">この呼び出しの後にモジュールを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="66855-110">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66855-111">要件</span><span class="sxs-lookup"><span data-stu-id="66855-111">Requirements</span></span>  

 <span data-ttu-id="66855-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66855-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66855-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66855-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66855-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66855-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66855-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66855-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66855-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="66855-116">See also</span></span>

- [<span data-ttu-id="66855-117">LoadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="66855-117">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="66855-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66855-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
