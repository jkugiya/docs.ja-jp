---
description: '詳細については、次を参照してください: ICorProfilerInfo7:: ReadInMemorySymbols'
title: 'ICorProfilerInfo7:: ReadInMemorySymbols'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
ms.openlocfilehash: 7f1a88d823e7cdfcc89aa140681f61cfbe3f63ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736987"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="35a0e-103">ICorProfilerInfo7:: ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="35a0e-103">ICorProfilerInfo7::ReadInMemorySymbols</span></span>

<span data-ttu-id="35a0e-104">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="35a0e-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="35a0e-105">メモリ内シンボルストリームからバイトを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="35a0e-105">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a0e-106">構文</span><span class="sxs-lookup"><span data-stu-id="35a0e-106">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35a0e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="35a0e-107">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="35a0e-108">からメモリ内ストリームを格納しているモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="35a0e-108">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="35a0e-109">からメモリ内ストリーム内でバイトの読み取りを開始する位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="35a0e-109">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="35a0e-110">入出力データがコピーされるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="35a0e-110">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="35a0e-111">バッファーには、 `countSymbolBytes` 使用可能な領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="35a0e-111">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="35a0e-112">からコピーするバイト数。</span><span class="sxs-lookup"><span data-stu-id="35a0e-112">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="35a0e-113">入出力メソッドから制御が戻るときに、実際に読み取られたバイト数を格納します。</span><span class="sxs-lookup"><span data-stu-id="35a0e-113">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35a0e-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="35a0e-114">Return Value</span></span>  

 <span data-ttu-id="35a0e-115">`S_OK`0以外のバイト数が読み取られた場合は。</span><span class="sxs-lookup"><span data-stu-id="35a0e-115">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="35a0e-116">`CORPROF_E_MODULE_IS_DYNAMIC`モジュールがを使用して作成された場合は <xref:System.Reflection.Emit> 。</span><span class="sxs-lookup"><span data-stu-id="35a0e-116">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35a0e-117">解説</span><span class="sxs-lookup"><span data-stu-id="35a0e-117">Remarks</span></span>  

 <span data-ttu-id="35a0e-118">メソッドは、 `ReadInMemorySymbols` `countSymbolBytes` インメモリストリーム内のオフセットを開始位置として、データの読み取りを試み      `symbolsReadOffset` ます。</span><span class="sxs-lookup"><span data-stu-id="35a0e-118">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="35a0e-119">データはにコピーされ `pSymbolBytes` ます。これには、使用可能な領域があることが予想され `countSymbolBytes` ます。</span><span class="sxs-lookup"><span data-stu-id="35a0e-119">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="35a0e-120">`pCountSymbolsBytesRead` 実際に読み取られたバイト数を格納し `countSymbolBytes` ます。ストリームの末尾に到達した場合よりも小さくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="35a0e-120">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35a0e-121">現在の実装では、リフレクションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="35a0e-121">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="35a0e-122">モジュールがリフレクションを使用して作成された場合、メソッドは `CORPROF_E_MODULE_IS_DYNAMIC` を返します。</span><span class="sxs-lookup"><span data-stu-id="35a0e-122">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a0e-123">要件</span><span class="sxs-lookup"><span data-stu-id="35a0e-123">Requirements</span></span>  

 <span data-ttu-id="35a0e-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35a0e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a0e-125">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="35a0e-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35a0e-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35a0e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35a0e-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35a0e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a0e-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="35a0e-128">See also</span></span>

- [<span data-ttu-id="35a0e-129">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35a0e-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
