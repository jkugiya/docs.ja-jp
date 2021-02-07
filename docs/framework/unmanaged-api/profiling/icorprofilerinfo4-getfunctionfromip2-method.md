---
description: '詳細について: ICorProfilerInfo4:: GetFunctionFromIP2 メソッド'
title: ICorProfilerInfo4::GetFunctionFromIP2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: f6abda7c9e7d4abcc0f0b256d6a7785cea205d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686805"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="5f6da-103">ICorProfilerInfo4::GetFunctionFromIP2 メソッド</span><span class="sxs-lookup"><span data-stu-id="5f6da-103">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>

<span data-ttu-id="5f6da-104">マネージコード命令ポインターを JIT 再コンパイルされた関数のバージョンにマップします。</span><span class="sxs-lookup"><span data-stu-id="5f6da-104">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f6da-105">構文</span><span class="sxs-lookup"><span data-stu-id="5f6da-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f6da-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5f6da-106">Parameters</span></span>  

 `ip`  
 <span data-ttu-id="5f6da-107">からマネージコード内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="5f6da-107">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="5f6da-108">入出力関数 ID。</span><span class="sxs-lookup"><span data-stu-id="5f6da-108">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="5f6da-109">入出力関数の JIT 再コンパイルバージョンの id。</span><span class="sxs-lookup"><span data-stu-id="5f6da-109">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f6da-110">解説</span><span class="sxs-lookup"><span data-stu-id="5f6da-110">Remarks</span></span>  

 <span data-ttu-id="5f6da-111">`GetFunctionFromIP2` はと似てい `GetFunctionFromIP` ますが、指定された IP アドレスを含む関数の関数 id ではなく、JIT 再コンパイルされた id を取得する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="5f6da-111">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f6da-112">`GetFunctionFromIP2` はガベージコレクションをトリガーできますが、で `GetFunctionFromIP` は発生しません。</span><span class="sxs-lookup"><span data-stu-id="5f6da-112">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="5f6da-113">詳細については、「 [HRESULT CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f6da-113">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f6da-114">要件</span><span class="sxs-lookup"><span data-stu-id="5f6da-114">Requirements</span></span>  

 <span data-ttu-id="5f6da-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f6da-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f6da-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f6da-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5f6da-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f6da-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f6da-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f6da-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f6da-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f6da-119">See also</span></span>

- [<span data-ttu-id="5f6da-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f6da-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
