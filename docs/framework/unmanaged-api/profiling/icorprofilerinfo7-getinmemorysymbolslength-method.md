---
description: '詳細について: ICorProfilerInfo7:: Getinmemoryシンボルの長さメソッド'
title: 'ICorProfilerInfo7:: Getinmemoryシンボルの長さメソッド'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 5d96b17e8abbd023f2d050eff3f121a871a94754
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737117"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="78cb9-103">ICorProfilerInfo7:: Getinmemoryシンボルの長さメソッド</span><span class="sxs-lookup"><span data-stu-id="78cb9-103">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>

<span data-ttu-id="78cb9-104">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="78cb9-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="78cb9-105">メモリ内シンボルストリームの長さを返します。</span><span class="sxs-lookup"><span data-stu-id="78cb9-105">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78cb9-106">構文</span><span class="sxs-lookup"><span data-stu-id="78cb9-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78cb9-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78cb9-107">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="78cb9-108">からメモリ内ストリームを格納しているモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="78cb9-108">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="78cb9-109">Pcountシンボルバイト数</span><span class="sxs-lookup"><span data-stu-id="78cb9-109">pCountSymbolBytes</span></span>  
 <span data-ttu-id="78cb9-110">入出力 `DWORD` メソッドから制御が戻るときに、ストリーム長がバイト単位で格納されている値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="78cb9-110">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78cb9-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="78cb9-111">Return Value</span></span>  

 <span data-ttu-id="78cb9-112">`S_OK`メモリストリームの長さがゼロ (0) であっても、このメソッドはを返します。</span><span class="sxs-lookup"><span data-stu-id="78cb9-112">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="78cb9-113">メソッドが `CORPROF_E_MODULE_IS_DYNAMIC` を使用して作成された場合、メソッドはを返し <xref:System.Reflection.Emit?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="78cb9-113">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78cb9-114">解説</span><span class="sxs-lookup"><span data-stu-id="78cb9-114">Remarks</span></span>  

 <span data-ttu-id="78cb9-115">モジュールにメモリ内シンボルがある場合は、ストリームの長さがに配置され `pCountSymbolBytes` ます。</span><span class="sxs-lookup"><span data-stu-id="78cb9-115">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="78cb9-116">モジュールにメモリ内シンボルがない場合は `*pCountSymbolBytes = 0` 。</span><span class="sxs-lookup"><span data-stu-id="78cb9-116">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78cb9-117">現在の実装では、リフレクションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="78cb9-117">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="78cb9-118">モジュールがリフレクションを使用して作成された場合、メソッドは `CORPROF_E_MODULE_IS_DYNAMIC` を返します。</span><span class="sxs-lookup"><span data-stu-id="78cb9-118">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78cb9-119">要件</span><span class="sxs-lookup"><span data-stu-id="78cb9-119">Requirements</span></span>  

 <span data-ttu-id="78cb9-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78cb9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78cb9-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78cb9-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78cb9-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78cb9-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78cb9-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78cb9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78cb9-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="78cb9-124">See also</span></span>

- [<span data-ttu-id="78cb9-125">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78cb9-125">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
