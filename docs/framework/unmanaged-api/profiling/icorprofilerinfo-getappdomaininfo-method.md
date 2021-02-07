---
description: '詳細について: ICorProfilerInfo:: GetAppDomainInfo メソッド'
title: ICorProfilerInfo::GetAppDomainInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 981577320bdf04a2bf119115f066811d3c11b68f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687286"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="ea54f-103">ICorProfilerInfo::GetAppDomainInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="ea54f-103">ICorProfilerInfo::GetAppDomainInfo Method</span></span>

<span data-ttu-id="ea54f-104">アプリケーション ドメイン ID を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="ea54f-104">Accepts an application domain ID.</span></span> <span data-ttu-id="ea54f-105">アプリケーション ドメインの名前と、そのアプリケーション ドメインを含むプロセスの ID を返します。</span><span class="sxs-lookup"><span data-stu-id="ea54f-105">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea54f-106">構文</span><span class="sxs-lookup"><span data-stu-id="ea54f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea54f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea54f-107">Parameters</span></span>  

 `appDomainId`  
 <span data-ttu-id="ea54f-108">[in] アプリケーション ドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="ea54f-108">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ea54f-109">[in] `szName` 戻りバッファーの長さ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="ea54f-109">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ea54f-110">[out] アプリケーション ドメイン名の文字列長の合計へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ea54f-110">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="ea54f-111">[out] 呼び出し元が提供したワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="ea54f-111">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="ea54f-112">このメソッドから制御が戻ると、`szName` にはアプリケーション ドメイン名の全部または一部が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ea54f-112">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="ea54f-113">[out] アプリケーション ドメインを含むプロセスの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ea54f-113">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea54f-114">解説</span><span class="sxs-lookup"><span data-stu-id="ea54f-114">Remarks</span></span>  

 <span data-ttu-id="ea54f-115">このメソッドから制御が戻った後で、`szName` バッファーのサイズが十分で、アプリケーション ドメインの完全名を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea54f-115">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="ea54f-116">これを行うには、`pcchName` が指している値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="ea54f-116">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="ea54f-117">`pcchName` が指している値が `cchName` の値より大きい場合は、`szName` バッファーの割り当てを増やし、`cchName` を新しい大きいサイズに更新して、`GetAppDomainInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ea54f-117">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="ea54f-118">別の方法として、最初に `GetAppDomainInfo` を長さゼロの `szName` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="ea54f-118">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ea54f-119">その後、バッファーのサイズを `pcchName` で返された値に設定し、`GetAppDomainInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ea54f-119">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea54f-120">要件</span><span class="sxs-lookup"><span data-stu-id="ea54f-120">Requirements</span></span>  

 <span data-ttu-id="ea54f-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea54f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea54f-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea54f-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea54f-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea54f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea54f-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea54f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea54f-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea54f-125">See also</span></span>

- [<span data-ttu-id="ea54f-126">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea54f-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="ea54f-127">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea54f-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ea54f-128">プロファイル</span><span class="sxs-lookup"><span data-stu-id="ea54f-128">Profiling</span></span>](index.md)
