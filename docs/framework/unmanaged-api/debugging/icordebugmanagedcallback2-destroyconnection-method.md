---
description: '詳細について: ICorDebugManagedCallback2::D estroyConnection メソッド'
title: ICorDebugManagedCallback2::DestroyConnection メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
ms.openlocfilehash: f17def5599dc02ed6b7b49d7f8ed4db02eb40181
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790894"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="4c023-103">ICorDebugManagedCallback2::DestroyConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="4c023-103">ICorDebugManagedCallback2::DestroyConnection Method</span></span>

<span data-ttu-id="4c023-104">指定された接続が終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4c023-104">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c023-105">構文</span><span class="sxs-lookup"><span data-stu-id="4c023-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c023-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4c023-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="4c023-107">から破棄された接続を含むプロセスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4c023-107">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="4c023-108">から破棄された接続の ID。</span><span class="sxs-lookup"><span data-stu-id="4c023-108">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c023-109">解説</span><span class="sxs-lookup"><span data-stu-id="4c023-109">Remarks</span></span>  

 <span data-ttu-id="4c023-110">ホストがホスト `DestroyConnection` [API](../hosting/index.md)で[ICLRDebugManager:: endconnection](../hosting/iclrdebugmanager-endconnection-method.md)を呼び出すと、コールバックが発生します。</span><span class="sxs-lookup"><span data-stu-id="4c023-110">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c023-111">要件</span><span class="sxs-lookup"><span data-stu-id="4c023-111">Requirements</span></span>  

 <span data-ttu-id="4c023-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c023-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c023-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c023-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c023-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c023-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c023-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c023-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c023-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c023-116">See also</span></span>

- [<span data-ttu-id="4c023-117">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4c023-117">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="4c023-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4c023-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
