---
description: '詳細について: ICorProfilerInfo:: GetAssemblyInfo メソッド'
title: ICorProfilerInfo::GetAssemblyInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: 64e94031e0e4fc5f768e94b83e4e97c3a9a7cb61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647845"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="4f1a2-103">ICorProfilerInfo::GetAssemblyInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="4f1a2-103">ICorProfilerInfo::GetAssemblyInfo Method</span></span>

<span data-ttu-id="4f1a2-104">アセンブリ ID を受け入れ、アセンブリの名前とアセンブリのマニフェスト モジュールの ID を返します。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-104">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f1a2-105">構文</span><span class="sxs-lookup"><span data-stu-id="4f1a2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f1a2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f1a2-106">Parameters</span></span>  

 `assemblyId`  
 <span data-ttu-id="4f1a2-107">[in] アセンブリの識別子。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-107">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4f1a2-108">[in] `szName` の長さ (文字数)。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-108">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4f1a2-109">[out] アセンブリ名の文字列長の合計へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-109">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="4f1a2-110">[out] 呼び出し元が提供したワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="4f1a2-111">関数が戻るときに、この関数の中にアセンブリ名が格納されます。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-111">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="4f1a2-112">[out] アセンブリを含むアプリケーション ドメインの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-112">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="4f1a2-113">[out] アセンブリのマニフェスト モジュールの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-113">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f1a2-114">解説</span><span class="sxs-lookup"><span data-stu-id="4f1a2-114">Remarks</span></span>  

 <span data-ttu-id="4f1a2-115">このメソッドから制御が戻った後で、`szName` バッファーのサイズが十分で、アセンブリの完全名を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-115">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="4f1a2-116">これを行うには、`pcchName` が指している値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-116">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="4f1a2-117">`pcchName` が指している値が `cchName` の値より大きい場合は、`szName` バッファーの割り当てを増やし、`cchName` を新しい大きいサイズに更新して、`GetAssemblyInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-117">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="4f1a2-118">別の方法として、最初に `GetAssemblyInfo` を長さゼロの `szName` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-118">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="4f1a2-119">その後、バッファーのサイズを `pcchName` で返された値に基づいて調整し、`GetAssemblyInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-119">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f1a2-120">要件</span><span class="sxs-lookup"><span data-stu-id="4f1a2-120">Requirements</span></span>  

 <span data-ttu-id="4f1a2-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f1a2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f1a2-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f1a2-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f1a2-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f1a2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f1a2-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f1a2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1a2-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f1a2-125">See also</span></span>

- [<span data-ttu-id="4f1a2-126">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f1a2-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4f1a2-127">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f1a2-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4f1a2-128">プロファイル</span><span class="sxs-lookup"><span data-stu-id="4f1a2-128">Profiling</span></span>](index.md)
