---
description: '詳細情報: ICorProfilerInfo:: IsArrayClass メソッド'
title: ICorProfilerInfo::IsArrayClass メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 1eee0b834c63c3cfe15bd08776214ca8b2ba3f69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687234"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="e95e2-103">ICorProfilerInfo::IsArrayClass メソッド</span><span class="sxs-lookup"><span data-stu-id="e95e2-103">ICorProfilerInfo::IsArrayClass Method</span></span>

<span data-ttu-id="e95e2-104">指定したクラスが配列クラスであるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e95e2-104">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e95e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="e95e2-105">Syntax</span></span>  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e95e2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e95e2-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="e95e2-107">から調べるクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="e95e2-107">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="e95e2-108">入出力配列要素の型を示す CorElementType 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e95e2-108">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="e95e2-109">入出力使用可能な場合は、配列要素のクラス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e95e2-109">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="e95e2-110">入出力配列のランク (次元の数) を示す整数を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="e95e2-110">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e95e2-111">解説</span><span class="sxs-lookup"><span data-stu-id="e95e2-111">Remarks</span></span>  

 <span data-ttu-id="e95e2-112">指定したクラスが配列クラスの場合、 `IsArrayClass` メソッドは、null 以外の出力パラメーターの S_OK HRESULT と値を返します。</span><span class="sxs-lookup"><span data-stu-id="e95e2-112">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="e95e2-113">それ以外の場合は S_FALSE を返します。</span><span class="sxs-lookup"><span data-stu-id="e95e2-113">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e95e2-114">要件</span><span class="sxs-lookup"><span data-stu-id="e95e2-114">Requirements</span></span>  

 <span data-ttu-id="e95e2-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e95e2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e95e2-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e95e2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e95e2-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e95e2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e95e2-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e95e2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e95e2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e95e2-119">See also</span></span>

- [<span data-ttu-id="e95e2-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e95e2-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
