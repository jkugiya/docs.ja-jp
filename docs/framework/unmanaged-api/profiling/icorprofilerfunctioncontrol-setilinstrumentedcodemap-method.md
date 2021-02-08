---
description: '詳細について: ICorProfilerFunctionControl:: SetILInstrumentedCodeMap メソッド'
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: bb345f737459342e0146cbb0e0bd7dd4b1e9a037
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781546"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="1dd48-103">ICorProfilerFunctionControl::SetILInstrumentedCodeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="1dd48-103">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="1dd48-104">指定した共通中間言語 (CIL) マップ エントリを使用して、指定される関数のコード マップを設定します。</span><span class="sxs-lookup"><span data-stu-id="1dd48-104">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd48-105">構文</span><span class="sxs-lookup"><span data-stu-id="1dd48-105">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd48-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1dd48-106">Parameters</span></span>  

 `cILMapEntries`  
 <span data-ttu-id="1dd48-107">[in] マップ内のエントリの数。</span><span class="sxs-lookup"><span data-stu-id="1dd48-107">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="1dd48-108">[in] COR_IL_MAP エントリの呼び出し元が割り当てたアレイ。</span><span class="sxs-lookup"><span data-stu-id="1dd48-108">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="1dd48-109">これらのエントリの解釈は、 [ICorProfilerInfo:: SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) メソッドの場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="1dd48-109">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dd48-110">解説</span><span class="sxs-lookup"><span data-stu-id="1dd48-110">Remarks</span></span>  

 <span data-ttu-id="1dd48-111">このメソッドを呼び出すことによってマッピングを設定すると、デバッガーは [ICorDebugILCode2:: GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md)を呼び出すことによってマッピングを取得できます。</span><span class="sxs-lookup"><span data-stu-id="1dd48-111">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="1dd48-112">またデバッガーは、スタック トレースおよび可変的な有効期間に対する IL オフセットを計算するときに、マッピングを内部で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1dd48-112">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd48-113">要件</span><span class="sxs-lookup"><span data-stu-id="1dd48-113">Requirements</span></span>  

 <span data-ttu-id="1dd48-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dd48-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd48-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1dd48-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1dd48-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dd48-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dd48-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd48-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd48-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1dd48-118">See also</span></span>

- [<span data-ttu-id="1dd48-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1dd48-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
