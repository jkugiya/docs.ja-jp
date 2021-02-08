---
description: '詳細について: ICorDebugManagedCallback2:: FunctionRemapOpportunity メソッド'
title: ICorDebugManagedCallback2::FunctionRemapOpportunity メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
ms.openlocfilehash: 901a9432ddf17efabd96153581b816f653ff501d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790868"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="ed613-103">ICorDebugManagedCallback2::FunctionRemapOpportunity メソッド</span><span class="sxs-lookup"><span data-stu-id="ed613-103">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>

<span data-ttu-id="ed613-104">コードの実行が、編集された関数の古いバージョンのシーケンスポイントに達したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ed613-104">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed613-105">構文</span><span class="sxs-lookup"><span data-stu-id="ed613-105">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed613-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ed613-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="ed613-107">から編集された関数を含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ed613-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ed613-108">からリマップブレークポイントが検出されたスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ed613-108">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="ed613-109">からスレッドで現在実行されている関数のバージョンを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ed613-109">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="ed613-110">から関数の最新バージョンを表す、の関数オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ed613-110">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="ed613-111">から以前のバージョンの関数の命令ポインターの MSIL (Microsoft 中間言語) オフセット。</span><span class="sxs-lookup"><span data-stu-id="ed613-111">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed613-112">解説</span><span class="sxs-lookup"><span data-stu-id="ed613-112">Remarks</span></span>  

 <span data-ttu-id="ed613-113">このコールバックでは、 [ICorDebugILFrame2:: RemapFunction](icordebugilframe2-remapfunction-method.md) メソッドを呼び出すことによって、指定された関数の新しいバージョンの適切な場所に命令ポインターを再マップする機会がデバッガーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="ed613-113">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="ed613-114">場合、デバッガーは、 `RemapFunction` 次のシーケンスポイント[](icordebugcontroller-continue-method.md)では、前のコードを実行してから別のコールバックを起動して、このメソッドを呼び出すことができません。 `FunctionRemapOpportunity`</span><span class="sxs-lookup"><span data-stu-id="ed613-114">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="ed613-115">このコールバックは、指定された関数の古いバージョンを実行しているすべてのフレームに対して、デバッガーが S_OK を返すまで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ed613-115">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed613-116">要件</span><span class="sxs-lookup"><span data-stu-id="ed613-116">Requirements</span></span>  

 <span data-ttu-id="ed613-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed613-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed613-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed613-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed613-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed613-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed613-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed613-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed613-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed613-121">See also</span></span>

- [<span data-ttu-id="ed613-122">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed613-122">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="ed613-123">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed613-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
