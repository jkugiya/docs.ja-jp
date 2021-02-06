---
description: '詳細については、次を参照してください: ICorProfilerInfo:: GetClassFromObject メソッド'
title: ICorProfilerInfo::GetClassFromObject メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
ms.openlocfilehash: 1c0224137c839d167263eefb17e3ae0b3ac29ef3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647805"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="5b3ca-103">ICorProfilerInfo::GetClassFromObject メソッド</span><span class="sxs-lookup"><span data-stu-id="5b3ca-103">ICorProfilerInfo::GetClassFromObject Method</span></span>

<span data-ttu-id="5b3ca-104">を指定して、オブジェクトのを取得し `ClassID` `ObjectID` ます。</span><span class="sxs-lookup"><span data-stu-id="5b3ca-104">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b3ca-105">構文</span><span class="sxs-lookup"><span data-stu-id="5b3ca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b3ca-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5b3ca-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="5b3ca-107">からを取得する対象のオブジェクトの ID `ClassID` 。</span><span class="sxs-lookup"><span data-stu-id="5b3ca-107">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="5b3ca-108">入出力返されたへのポインター `ClassID` 。</span><span class="sxs-lookup"><span data-stu-id="5b3ca-108">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b3ca-109">解説</span><span class="sxs-lookup"><span data-stu-id="5b3ca-109">Remarks</span></span>  

 <span data-ttu-id="5b3ca-110">Null は、が `pClassId` `objectId` アンロード中の型を持つことを示します。</span><span class="sxs-lookup"><span data-stu-id="5b3ca-110">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b3ca-111">要件</span><span class="sxs-lookup"><span data-stu-id="5b3ca-111">Requirements</span></span>  

 <span data-ttu-id="5b3ca-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b3ca-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b3ca-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b3ca-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b3ca-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b3ca-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b3ca-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b3ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b3ca-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b3ca-116">See also</span></span>

- [<span data-ttu-id="5b3ca-117">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5b3ca-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
