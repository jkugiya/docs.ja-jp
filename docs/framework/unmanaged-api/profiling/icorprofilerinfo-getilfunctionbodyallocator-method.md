---
description: '詳細について: ICorProfilerInfo:: GetILFunctionBodyAllocator メソッド'
title: ICorProfilerInfo::GetILFunctionBodyAllocator メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
ms.openlocfilehash: 25d059d784fe64231d4d2ff3d23b4820443873cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647428"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="6a9fb-103">ICorProfilerInfo::GetILFunctionBodyAllocator メソッド</span><span class="sxs-lookup"><span data-stu-id="6a9fb-103">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>

<span data-ttu-id="6a9fb-104">Microsoft 中間言語 (MSIL) コードでメソッドの本体を交換するために使用されるメモリを割り当てるメソッドを提供するインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6a9fb-104">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9fb-105">構文</span><span class="sxs-lookup"><span data-stu-id="6a9fb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a9fb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a9fb-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="6a9fb-107">からメソッドが存在するモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="6a9fb-107">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="6a9fb-108">入出力メモリを割り当てるメソッドを提供する [Imethodmalloc](imethodmalloc-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6a9fb-108">[out] A pointer to an [IMethodMalloc](imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a9fb-109">解説</span><span class="sxs-lookup"><span data-stu-id="6a9fb-109">Remarks</span></span>  

 <span data-ttu-id="6a9fb-110">MSIL コードのメソッド本体は、読み込まれたモジュールに対して相対的な相対仮想アドレス (RVA) として配置されている必要があります。これは、モジュールが 4 GB 以内に続くことを意味します。</span><span class="sxs-lookup"><span data-stu-id="6a9fb-110">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="6a9fb-111">ツールがメソッドの本体を簡単に交換できるようにするために、メソッドは、 `GetILFunctionBodyAllocator` その範囲内でメモリが割り当てられるようにします。</span><span class="sxs-lookup"><span data-stu-id="6a9fb-111">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a9fb-112">要件</span><span class="sxs-lookup"><span data-stu-id="6a9fb-112">Requirements</span></span>  

 <span data-ttu-id="6a9fb-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a9fb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a9fb-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6a9fb-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6a9fb-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a9fb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a9fb-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a9fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a9fb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a9fb-117">See also</span></span>

- [<span data-ttu-id="6a9fb-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a9fb-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
