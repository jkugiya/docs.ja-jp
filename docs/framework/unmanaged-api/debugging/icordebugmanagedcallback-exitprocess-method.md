---
description: '詳細については、次を参照してください: ExitProcess メソッド'
title: ICorDebugManagedCallback::ExitProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 3418931b8397edefcb801986275c35b28e00072d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790959"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="1ed30-103">ICorDebugManagedCallback::ExitProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="1ed30-103">ICorDebugManagedCallback::ExitProcess Method</span></span>

<span data-ttu-id="1ed30-104">プロセスが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="1ed30-104">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed30-105">構文</span><span class="sxs-lookup"><span data-stu-id="1ed30-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ed30-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ed30-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="1ed30-107">からプロセスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ed30-107">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ed30-108">解説</span><span class="sxs-lookup"><span data-stu-id="1ed30-108">Remarks</span></span>  

 <span data-ttu-id="1ed30-109">イベントから続行することはできません `ExitProcess` 。</span><span class="sxs-lookup"><span data-stu-id="1ed30-109">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="1ed30-110">このイベントは、プロセスの停止中に、他のイベントに非同期に発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1ed30-110">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="1ed30-111">これは、プロセスが停止中に終了した場合に発生する可能性があります。通常は、何らかの外部強制が原因です。</span><span class="sxs-lookup"><span data-stu-id="1ed30-111">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="1ed30-112">共通言語ランタイム (CLR) がマネージコールバックのディスパッチを既に行っている場合、このイベントは、そのコールバックが返されるまで遅延されます。</span><span class="sxs-lookup"><span data-stu-id="1ed30-112">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="1ed30-113">`ExitProcess`イベントは、シャットダウン時に呼び出されることが保証されている唯一の終了/アンロードイベントです。</span><span class="sxs-lookup"><span data-stu-id="1ed30-113">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ed30-114">要件</span><span class="sxs-lookup"><span data-stu-id="1ed30-114">Requirements</span></span>  

 <span data-ttu-id="1ed30-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed30-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ed30-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ed30-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ed30-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ed30-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ed30-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ed30-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed30-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ed30-119">See also</span></span>

- [<span data-ttu-id="1ed30-120">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ed30-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
