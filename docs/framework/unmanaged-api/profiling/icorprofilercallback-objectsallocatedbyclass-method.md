---
description: '詳細について: ICorProfilerCallback:: ObjectsAllocatedByClass メソッド'
title: ICorProfilerCallback::ObjectsAllocatedByClass メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: df9f3dde27664de7db4afb264b221f640753ddb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745061"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="d2c9d-103">ICorProfilerCallback::ObjectsAllocatedByClass メソッド</span><span class="sxs-lookup"><span data-stu-id="d2c9d-103">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>

<span data-ttu-id="d2c9d-104">最後のガベージコレクション以降に作成された、指定した各クラスのインスタンスの数をプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-104">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c9d-105">構文</span><span class="sxs-lookup"><span data-stu-id="d2c9d-105">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2c9d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2c9d-106">Parameters</span></span>  

 `cClassCount`  
 <span data-ttu-id="d2c9d-107">から `classIds` 配列と配列のサイズ `cObjects` 。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-107">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="d2c9d-108">からクラス Id の配列。各 ID は、1つ以上のインスタンスを持つクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-108">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="d2c9d-109">から整数の配列。各整数は、配列内の対応するクラスのインスタンスの数を指定し `classIds` ます。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-109">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2c9d-110">解説</span><span class="sxs-lookup"><span data-stu-id="d2c9d-110">Remarks</span></span>  

 <span data-ttu-id="d2c9d-111">`classIds`配列と `cObjects` 配列は並列配列です。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-111">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="d2c9d-112">たとえば、 `classIds[i]` とは `cObjects[i]` 同じクラスを参照します。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-112">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="d2c9d-113">前のガベージコレクションの後にクラスのインスタンスが作成されていない場合、クラスは省略されます。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-113">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="d2c9d-114">`ObjectsAllocatedByClass`コールバックは、大きなオブジェクトヒープに割り当てられたオブジェクトを報告しません。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-114">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="d2c9d-115">によって報告 `ObjectsAllocatedByClass` される数値は、推定値のみです。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-115">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="d2c9d-116">正確にカウントするには、 [ICorProfilerCallback:: ObjectAllocated](icorprofilercallback-objectallocated-method.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-116">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="d2c9d-117">`classIds`対応する配列にアンロード中の型がある場合、配列には1つ以上の null エントリが含まれ `cObjects` ます。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-117">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2c9d-118">要件</span><span class="sxs-lookup"><span data-stu-id="d2c9d-118">Requirements</span></span>  

 <span data-ttu-id="d2c9d-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2c9d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2c9d-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d2c9d-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2c9d-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2c9d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2c9d-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2c9d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c9d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2c9d-123">See also</span></span>

- [<span data-ttu-id="d2c9d-124">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2c9d-124">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
