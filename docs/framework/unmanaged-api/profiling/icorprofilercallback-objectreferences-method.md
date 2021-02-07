---
description: '詳細について: ICorProfilerCallback:: ObjectReferences メソッド'
title: ICorProfilerCallback::ObjectReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 55ea6fae87ecb6534af322fc9d5055c8a247f37a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745113"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="1a590-103">ICorProfilerCallback::ObjectReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="1a590-103">ICorProfilerCallback::ObjectReferences Method</span></span>

<span data-ttu-id="1a590-104">指定したオブジェクトによって参照されているメモリ内のオブジェクトに関する情報をプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="1a590-104">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a590-105">構文</span><span class="sxs-lookup"><span data-stu-id="1a590-105">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a590-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1a590-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="1a590-107">からオブジェクトを参照しているオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="1a590-107">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="1a590-108">から指定したオブジェクトがインスタンスであるクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="1a590-108">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="1a590-109">から指定したオブジェクトによって参照されるオブジェクトの数 (つまり、配列内の要素の数 `objectRefIds` )。</span><span class="sxs-lookup"><span data-stu-id="1a590-109">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="1a590-110">からによって参照されているオブジェクトの Id の配列 `objectId` 。</span><span class="sxs-lookup"><span data-stu-id="1a590-110">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a590-111">解説</span><span class="sxs-lookup"><span data-stu-id="1a590-111">Remarks</span></span>  

 <span data-ttu-id="1a590-112">`ObjectReferences`メソッドは、ガベージコレクションが完了した後にヒープ内の残りのオブジェクトに対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1a590-112">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="1a590-113">プロファイラーがこのコールバックからエラーを返すと、プロファイリングサービスは、次のガベージコレクションまでこのコールバックの呼び出しを中止します。</span><span class="sxs-lookup"><span data-stu-id="1a590-113">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="1a590-114">コールバックは、 `ObjectReferences` [ICorProfilerCallback:: rootreferences](icorprofilercallback-rootreferences-method.md) コールバックと共に使用して、ランタイムの完全なオブジェクト参照グラフを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1a590-114">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="1a590-115">共通言語ランタイム (CLR) では、各オブジェクト参照がメソッドによって1回だけ報告され `ObjectReferences` ます。</span><span class="sxs-lookup"><span data-stu-id="1a590-115">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="1a590-116">によって返されるオブジェクト Id `ObjectReferences` は、オブジェクトの移動中にガベージコレクションが発生する可能性があるため、コールバック自体では無効です。</span><span class="sxs-lookup"><span data-stu-id="1a590-116">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="1a590-117">そのため、呼び出し中にプロファイラーがオブジェクトの検査を試行することはできません `ObjectReferences` 。</span><span class="sxs-lookup"><span data-stu-id="1a590-117">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="1a590-118">[ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)が呼び出されると、ガベージコレクションが完了し、検査を安全に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1a590-118">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="1a590-119">Null は、が `ClassId` `objectId` アンロード中の型を持つことを示します。</span><span class="sxs-lookup"><span data-stu-id="1a590-119">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a590-120">要件</span><span class="sxs-lookup"><span data-stu-id="1a590-120">Requirements</span></span>  

 <span data-ttu-id="1a590-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a590-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a590-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1a590-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1a590-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a590-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a590-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a590-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a590-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a590-125">See also</span></span>

- [<span data-ttu-id="1a590-126">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a590-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
