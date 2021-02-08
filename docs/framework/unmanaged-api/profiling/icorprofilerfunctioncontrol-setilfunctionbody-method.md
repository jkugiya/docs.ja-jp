---
description: '詳細について: ICorProfilerFunctionControl:: SetILFunctionBody メソッド'
title: ICorProfilerFunctionControl::SetILFunctionBody メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: 470eefce5b211adcfd111951be9a004b3bd7d8fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781611"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="f24c1-103">ICorProfilerFunctionControl::SetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="f24c1-103">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>

<span data-ttu-id="f24c1-104">メソッドの中間共通言語 (CIL) 本体を置換します。</span><span class="sxs-lookup"><span data-stu-id="f24c1-104">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f24c1-105">構文</span><span class="sxs-lookup"><span data-stu-id="f24c1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f24c1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f24c1-106">Parameters</span></span>  

 `cbNewILMethodHeader`  
 <span data-ttu-id="f24c1-107">[入力] ヘッダー、および本体の後に続く構造を含む、新しい CIL の合計サイズ。</span><span class="sxs-lookup"><span data-stu-id="f24c1-107">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="f24c1-108">[入力] 新しい CIL ヘッダーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f24c1-108">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f24c1-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f24c1-109">Return Value</span></span>  

 <span data-ttu-id="f24c1-110">このメソッドは、次の特定の HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="f24c1-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="f24c1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f24c1-111">HRESULT</span></span>|<span data-ttu-id="f24c1-112">説明</span><span class="sxs-lookup"><span data-stu-id="f24c1-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f24c1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f24c1-113">S_OK</span></span>|<span data-ttu-id="f24c1-114">置換が成功しました。</span><span class="sxs-lookup"><span data-stu-id="f24c1-114">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f24c1-115">解説</span><span class="sxs-lookup"><span data-stu-id="f24c1-115">Remarks</span></span>  

 <span data-ttu-id="f24c1-116">[ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)メソッドとは異なり、 `SetILFunctionBody` メソッドは新しい CIL 本体に必要なメモリを管理します。</span><span class="sxs-lookup"><span data-stu-id="f24c1-116">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="f24c1-117">これは、プロファイラーによって提供される CIL 本体を [Imethodmalloc](imethodmalloc-interface.md) インターフェイスを使用して割り当てたり、特定の範囲内で割り当てたりする必要がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="f24c1-117">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="f24c1-118">この本体は、どのヒープにも割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="f24c1-118">It can be allocated on any heap.</span></span> <span data-ttu-id="f24c1-119">プロファイラーは、が返された後に、その CIL 本体に使用されるメモリを解放でき `SetILFunctionBody` ます。</span><span class="sxs-lookup"><span data-stu-id="f24c1-119">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f24c1-120">要件</span><span class="sxs-lookup"><span data-stu-id="f24c1-120">Requirements</span></span>  

 <span data-ttu-id="f24c1-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f24c1-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f24c1-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f24c1-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f24c1-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f24c1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f24c1-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f24c1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f24c1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="f24c1-125">See also</span></span>

- [<span data-ttu-id="f24c1-126">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f24c1-126">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
