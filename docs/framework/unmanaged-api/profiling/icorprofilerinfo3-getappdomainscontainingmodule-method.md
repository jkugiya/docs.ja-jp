---
description: '詳細について: ICorProfilerInfo3:: GetAppDomainsContainingModule メソッド'
title: ICorProfilerInfo3::GetAppDomainsContainingModule メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
ms.openlocfilehash: 0f0fea5b01b80b110d7ab041574dc195162cb508
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646843"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="4dd81-103">ICorProfilerInfo3::GetAppDomainsContainingModule メソッド</span><span class="sxs-lookup"><span data-stu-id="4dd81-103">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>

<span data-ttu-id="4dd81-104">指定したモジュールが読み込まれているアプリケーション ドメインの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="4dd81-104">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dd81-105">構文</span><span class="sxs-lookup"><span data-stu-id="4dd81-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dd81-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4dd81-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="4dd81-107">[in] 読み込まれたモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="4dd81-107">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="4dd81-108">[in] `appDomainIds` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="4dd81-108">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="4dd81-109">[out] 返される要素の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4dd81-109">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="4dd81-110">[out] アプリケーション ドメイン ID 値の配列。</span><span class="sxs-lookup"><span data-stu-id="4dd81-110">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dd81-111">解説</span><span class="sxs-lookup"><span data-stu-id="4dd81-111">Remarks</span></span>  

 <span data-ttu-id="4dd81-112">このメソッドは、呼び出し元が割り当てたバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="4dd81-112">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dd81-113">要件</span><span class="sxs-lookup"><span data-stu-id="4dd81-113">Requirements</span></span>  

 <span data-ttu-id="4dd81-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dd81-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dd81-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4dd81-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4dd81-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dd81-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dd81-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dd81-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd81-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dd81-118">See also</span></span>

- [<span data-ttu-id="4dd81-119">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4dd81-119">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="4dd81-120">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4dd81-120">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="4dd81-121">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4dd81-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4dd81-122">プロファイル</span><span class="sxs-lookup"><span data-stu-id="4dd81-122">Profiling</span></span>](index.md)
