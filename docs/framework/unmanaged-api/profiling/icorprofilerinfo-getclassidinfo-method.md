---
description: '詳細については、次を参照してください: ICorProfilerInfo:: Getclassid Dinfo メソッド'
title: ICorProfilerInfo::GetClassIDInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
ms.openlocfilehash: 05937580bd8bd672da16875964548829d071f4bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647714"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="6b4e2-103">ICorProfilerInfo::GetClassIDInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="6b4e2-103">ICorProfilerInfo::GetClassIDInfo Method</span></span>

<span data-ttu-id="6b4e2-104">指定したクラスの親モジュールとメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="6b4e2-104">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b4e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="6b4e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b4e2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b4e2-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="6b4e2-107">から情報を取得する対象のクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="6b4e2-107">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="6b4e2-108">入出力クラスの親モジュールの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b4e2-108">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="6b4e2-109">入出力クラスのメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b4e2-109">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b4e2-110">解説</span><span class="sxs-lookup"><span data-stu-id="6b4e2-110">Remarks</span></span>  

 <span data-ttu-id="6b4e2-111">プロファイラーコードは、 [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) を呼び出して、指定されたモジュールのメタデータインターフェイスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="6b4e2-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="6b4e2-112">`pTypeDefToken` によって参照される場所に返されるメタデータ トークンを使用すると、クラスのメタデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6b4e2-112">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="6b4e2-113">ジェネリック型の詳細情報を取得するには、 [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b4e2-113">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b4e2-114">要件</span><span class="sxs-lookup"><span data-stu-id="6b4e2-114">Requirements</span></span>  

 <span data-ttu-id="6b4e2-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b4e2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b4e2-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b4e2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b4e2-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b4e2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b4e2-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b4e2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b4e2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b4e2-119">See also</span></span>

- [<span data-ttu-id="6b4e2-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b4e2-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
