---
description: '詳細について: ICorProfilerCallback:: ManagedToUnmanagedTransition メソッド'
title: ICorProfilerCallback::ManagedToUnmanagedTransition メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: bf7f45ae576f9812dee24cd3799a3a87678f7c61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705580"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="4c791-103">ICorProfilerCallback::ManagedToUnmanagedTransition メソッド</span><span class="sxs-lookup"><span data-stu-id="4c791-103">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>

<span data-ttu-id="4c791-104">マネージコードからアンマネージコードへの遷移が発生したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4c791-104">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c791-105">構文</span><span class="sxs-lookup"><span data-stu-id="4c791-105">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c791-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4c791-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="4c791-107">から呼び出される関数の ID。</span><span class="sxs-lookup"><span data-stu-id="4c791-107">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="4c791-108">からマネージコードからアンマネージコードへの呼び出しによって移行が発生したかどうか、またはアンマネージコードによって呼び出されたマネージ関数からの戻り値によって発生したものかどうかを示す [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="4c791-108">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c791-109">解説</span><span class="sxs-lookup"><span data-stu-id="4c791-109">Remarks</span></span>  

 <span data-ttu-id="4c791-110">の値 `reason` が COR_PRF_TRANSITION_CALL の場合、関数 ID はアンマネージ関数の ID であり、just-in-time コンパイラを使用してコンパイルされることはありません。</span><span class="sxs-lookup"><span data-stu-id="4c791-110">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="4c791-111">アンマネージ関数には、名前やメタデータなどの基本的な情報が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="4c791-111">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="4c791-112">アンマネージ関数が暗黙のプラットフォーム呼び出し (PInvoke) を使用して呼び出された場合、ランタイムは呼び出し先を特定できず、の値は null になり `functionId` ます。</span><span class="sxs-lookup"><span data-stu-id="4c791-112">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="4c791-113">暗黙の PInvoke の詳細については、「 [C++ Interop の使用 (暗黙的な pinvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c791-113">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c791-114">要件</span><span class="sxs-lookup"><span data-stu-id="4c791-114">Requirements</span></span>  

 <span data-ttu-id="4c791-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c791-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c791-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c791-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c791-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c791-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c791-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c791-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c791-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c791-119">See also</span></span>

- [<span data-ttu-id="4c791-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4c791-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4c791-121">UnmanagedToManagedTransition メソッド</span><span class="sxs-lookup"><span data-stu-id="4c791-121">UnmanagedToManagedTransition Method</span></span>](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="4c791-122">C++ での明示的な PInvoke の使用 (DllImport 属性)</span><span class="sxs-lookup"><span data-stu-id="4c791-122">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
