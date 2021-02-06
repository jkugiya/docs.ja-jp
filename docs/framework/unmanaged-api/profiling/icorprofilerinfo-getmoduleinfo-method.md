---
description: '詳細について: ICorProfilerInfo:: GetModuleInfo メソッド'
title: ICorProfilerInfo::GetModuleInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: 003f40e6637490be23e8bf87a6bac8ab76bc50e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647194"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="f7bcb-103">ICorProfilerInfo::GetModuleInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="f7bcb-103">ICorProfilerInfo::GetModuleInfo Method</span></span>

<span data-ttu-id="f7bcb-104">モジュール ID を指定して、モジュールのファイル名とモジュールの親アセンブリの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-104">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7bcb-105">構文</span><span class="sxs-lookup"><span data-stu-id="f7bcb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7bcb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f7bcb-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="f7bcb-107">[in] 情報が取得されるモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-107">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="f7bcb-108">[out] モジュールが読み込まれるベース アドレス。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-108">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f7bcb-109">[in] `szName` 戻りバッファーの長さ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-109">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f7bcb-110">[out] 返されるモジュールのファイル名の文字列長の合計へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-110">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="f7bcb-111">[out] 呼び出し元が提供したワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-111">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="f7bcb-112">メソッドから制御が戻るとき、このバッファーにモジュールのファイル名が格納されます。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-112">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="f7bcb-113">[out] モジュールの親アセンブリ ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-113">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7bcb-114">解説</span><span class="sxs-lookup"><span data-stu-id="f7bcb-114">Remarks</span></span>  

 <span data-ttu-id="f7bcb-115">動的モジュールの場合、`szName` パラメーターは空の文字列、ベース アドレスは 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-115">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="f7bcb-116">メソッドは、 `GetModuleInfo` モジュールの id が存在するとすぐに呼び出される場合がありますが、プロファイラーが [ICorProfilerCallback:: ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) コールバックを受信するまで、親アセンブリの id は使用できません。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-116">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="f7bcb-117">`GetModuleInfo` から制御が戻ったら、`szName` バッファーのサイズが十分で、モジュールのファイル名全体を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-117">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="f7bcb-118">これを行うには、`pcchName` が指している値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-118">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="f7bcb-119">`pcchName` が指している値が `cchName` の値より大きい場合は、`szName` バッファーの割り当てを増やし、`cchName` を新しい大きいサイズに更新して、`GetModuleInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-119">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="f7bcb-120">別の方法として、最初に `GetModuleInfo` を長さゼロの `szName` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-120">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="f7bcb-121">その後、バッファーのサイズを `pcchName` で返された値に設定し、`GetModuleInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-121">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7bcb-122">要件</span><span class="sxs-lookup"><span data-stu-id="f7bcb-122">Requirements</span></span>  

 <span data-ttu-id="f7bcb-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7bcb-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7bcb-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7bcb-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7bcb-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7bcb-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7bcb-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7bcb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7bcb-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7bcb-127">See also</span></span>

- [<span data-ttu-id="f7bcb-128">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7bcb-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f7bcb-129">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7bcb-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f7bcb-130">プロファイル</span><span class="sxs-lookup"><span data-stu-id="f7bcb-130">Profiling</span></span>](index.md)
- [<span data-ttu-id="f7bcb-131">GetModuleInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="f7bcb-131">GetModuleInfo2 Method</span></span>](icorprofilerinfo3-getmoduleinfo2-method.md)
