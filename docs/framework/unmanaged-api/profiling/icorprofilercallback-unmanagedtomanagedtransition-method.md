---
description: '詳細について: ICorProfilerCallback:: UnmanagedToManagedTransition メソッド'
title: ICorProfilerCallback::UnmanagedToManagedTransition メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 2b2bd86798df8b8c46506c924ee201c191e6cb82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657145"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="fa23d-103">ICorProfilerCallback::UnmanagedToManagedTransition メソッド</span><span class="sxs-lookup"><span data-stu-id="fa23d-103">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>

<span data-ttu-id="fa23d-104">アンマネージコードからマネージコードへの遷移が発生したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="fa23d-104">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa23d-105">構文</span><span class="sxs-lookup"><span data-stu-id="fa23d-105">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa23d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fa23d-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="fa23d-107">から呼び出される関数の ID。</span><span class="sxs-lookup"><span data-stu-id="fa23d-107">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="fa23d-108">からアンマネージコードからのマネージコードの呼び出しによって移行が発生したかどうか、またはマネージ関数によって呼び出されたアンマネージ関数からの戻りが原因で発生したかどうかを示す [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="fa23d-108">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa23d-109">解説</span><span class="sxs-lookup"><span data-stu-id="fa23d-109">Remarks</span></span>  

 <span data-ttu-id="fa23d-110">の値 `reason` が COR_PRF_TRANSITION_RETURN であり、 `functionId` が null でない場合、関数 ID はアンマネージ関数の ID であり、JUST-IN-TIME (JIT) コンパイラを使用してコンパイルされることはありません。</span><span class="sxs-lookup"><span data-stu-id="fa23d-110">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="fa23d-111">アンマネージ関数には、名前やメタデータなど、いくつかの基本的な情報が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="fa23d-111">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="fa23d-112">の値が COR_PRF_TRANSITION_CALL 場合は、呼び出された `reason` 関数 (つまり、マネージ関数) がまだ JIT でコンパイルされていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa23d-112">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa23d-113">要件</span><span class="sxs-lookup"><span data-stu-id="fa23d-113">Requirements</span></span>  

 <span data-ttu-id="fa23d-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa23d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa23d-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa23d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa23d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa23d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa23d-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa23d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa23d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa23d-118">See also</span></span>

- [<span data-ttu-id="fa23d-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa23d-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="fa23d-120">ManagedToUnmanagedTransition メソッド</span><span class="sxs-lookup"><span data-stu-id="fa23d-120">ManagedToUnmanagedTransition Method</span></span>](icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="fa23d-121">C++ での明示的な PInvoke の使用 (DllImport 属性)</span><span class="sxs-lookup"><span data-stu-id="fa23d-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="fa23d-122">C++ Interop (暗黙の PInvoke) の使用</span><span class="sxs-lookup"><span data-stu-id="fa23d-122">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
