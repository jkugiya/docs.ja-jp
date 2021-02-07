---
description: '詳細については、次の情報を参照してください:: EnumerateThreads メソッド'
title: ICorDebugController::EnumerateThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: b53425de36be5a435ef0dac538c5165f41db63f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710778"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="9cb39-103">ICorDebugController::EnumerateThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="9cb39-103">ICorDebugController::EnumerateThreads Method</span></span>

<span data-ttu-id="9cb39-104">プロセス内のアクティブなマネージスレッドの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="9cb39-104">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb39-105">構文</span><span class="sxs-lookup"><span data-stu-id="9cb39-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cb39-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9cb39-106">Parameters</span></span>  

 `ppThreads`  
 <span data-ttu-id="9cb39-107">入出力プロセス内でアクティブになっているすべてのマネージスレッドの列挙子を表す "いい Threadenum" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9cb39-107">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cb39-108">解説</span><span class="sxs-lookup"><span data-stu-id="9cb39-108">Remarks</span></span>  

 <span data-ttu-id="9cb39-109">スレッドがアクティブであると見なされるのは、"CreateThread" コールバックがディスパッチされてから、" [](icordebugmanagedcallback-createthread-method.md) [Managedcallback:: exitthread](icordebugmanagedcallback-exitthread-method.md) " コールバックがディスパッチされる前です。</span><span class="sxs-lookup"><span data-stu-id="9cb39-109">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="9cb39-110">マネージスレッドは、必ずしもスタック上にマネージフレームを持つとは限りません。</span><span class="sxs-lookup"><span data-stu-id="9cb39-110">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="9cb39-111">スレッドは、によっては、"、 [" という](icordebugmanagedcallback-createprocess-method.md) ように列挙できます。</span><span class="sxs-lookup"><span data-stu-id="9cb39-111">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="9cb39-112">列挙体は、自然に空になります。</span><span class="sxs-lookup"><span data-stu-id="9cb39-112">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cb39-113">要件</span><span class="sxs-lookup"><span data-stu-id="9cb39-113">Requirements</span></span>  

 <span data-ttu-id="9cb39-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cb39-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb39-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cb39-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cb39-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cb39-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cb39-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb39-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb39-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cb39-118">See also</span></span>
