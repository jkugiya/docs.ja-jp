---
description: '詳細について: ICorProfilerCallback:: JITCompilationFinished メソッド'
title: ICorProfilerCallback::JITCompilationFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: f0308bfb5f81d7305ab36acbb9144142232ef8c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705786"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="b6b62-103">ICorProfilerCallback::JITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="b6b62-103">ICorProfilerCallback::JITCompilationFinished Method</span></span>

<span data-ttu-id="b6b62-104">Just-in-time (JIT) コンパイラが関数のコンパイルを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b6b62-104">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b62-105">構文</span><span class="sxs-lookup"><span data-stu-id="b6b62-105">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6b62-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6b62-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="b6b62-107">\[in] コンパイルされた関数の ID。</span><span class="sxs-lookup"><span data-stu-id="b6b62-107">\[in] The ID of the function that was compiled.</span></span>

- `hrStatus`

  <span data-ttu-id="b6b62-108">\[in] コンパイルが成功したかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="b6b62-108">\[in] A value indicating whether compilation was successful.</span></span>

- `fIsSafeToBlock`

  <span data-ttu-id="b6b62-109">\[in] プロファイラーに対して、ブロックがランタイムの操作に影響を与えるかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="b6b62-109">\[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="b6b62-110">この値は、ブロックによって、 `true` ランタイムが呼び出し元のスレッドがこのコールバックから戻るのを待機する場合は、それ以外の場合はです `false` 。</span><span class="sxs-lookup"><span data-stu-id="b6b62-110">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>

  <span data-ttu-id="b6b62-111">の値は `true` ランタイムに害を及ぼすことはありませんが、プロファイルの結果をスキューできます。</span><span class="sxs-lookup"><span data-stu-id="b6b62-111">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>

## <a name="requirements"></a><span data-ttu-id="b6b62-112">要件</span><span class="sxs-lookup"><span data-stu-id="b6b62-112">Requirements</span></span>  

 <span data-ttu-id="b6b62-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6b62-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6b62-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b6b62-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6b62-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6b62-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6b62-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6b62-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b62-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6b62-117">See also</span></span>

- [<span data-ttu-id="b6b62-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b6b62-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b6b62-119">JITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="b6b62-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
