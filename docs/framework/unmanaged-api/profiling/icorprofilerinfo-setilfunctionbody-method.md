---
description: '詳細について: ICorProfilerInfo:: SetILFunctionBody メソッド'
title: ICorProfilerInfo::SetILFunctionBody メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: 38e7907080065dc96d72a3d38a67227414637a70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647168"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="e019d-103">ICorProfilerInfo::SetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="e019d-103">ICorProfilerInfo::SetILFunctionBody Method</span></span>

<span data-ttu-id="e019d-104">指定したモジュール内の指定した関数の本体を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e019d-104">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e019d-105">構文</span><span class="sxs-lookup"><span data-stu-id="e019d-105">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e019d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e019d-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="e019d-107">から関数が存在するモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="e019d-107">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="e019d-108">から本文の置換対象となる関数のトークン。</span><span class="sxs-lookup"><span data-stu-id="e019d-108">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="e019d-109">から関数の新しいヘッダー。</span><span class="sxs-lookup"><span data-stu-id="e019d-109">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e019d-110">解説</span><span class="sxs-lookup"><span data-stu-id="e019d-110">Remarks</span></span>  

 <span data-ttu-id="e019d-111">メソッドは、 `SetILFunctionBody` メタデータ内の関数の相対仮想アドレスを置き換えて、新しい関数本体をポイントし、必要に応じて内部データ構造を調整します。</span><span class="sxs-lookup"><span data-stu-id="e019d-111">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="e019d-112">メソッドは、 `SetILFunctionBody` just-in-time (JIT) コンパイラによってコンパイルされたことがない関数に対してのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e019d-112">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="e019d-113">[ICorProfilerInfo:: GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)メソッドを使用して、新しいメソッドの領域を割り当て、バッファーに互換性があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e019d-113">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e019d-114">要件</span><span class="sxs-lookup"><span data-stu-id="e019d-114">Requirements</span></span>  

 <span data-ttu-id="e019d-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e019d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e019d-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e019d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e019d-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e019d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e019d-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e019d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e019d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e019d-119">See also</span></span>

- [<span data-ttu-id="e019d-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e019d-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
