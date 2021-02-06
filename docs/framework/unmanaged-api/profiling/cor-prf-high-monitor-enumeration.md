---
description: '詳細情報: COR_PRF_HIGH_MONITOR 列挙型'
title: COR_PRF_HIGH_MONITOR 列挙型
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 800bad21af96d8bbdf73f2af799f474f11294705
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648767"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="1b15b-103">COR_PRF_HIGH_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="1b15b-103">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="1b15b-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="1b15b-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="1b15b-105">プロファイラーが読み込み時に[ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)メソッドに対して指定できる、 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列挙に含まれるフラグだけでなく、フラグも提供します。</span><span class="sxs-lookup"><span data-stu-id="1b15b-105">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b15b-106">構文</span><span class="sxs-lookup"><span data-stu-id="1b15b-106">Syntax</span></span>  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED |
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="1b15b-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="1b15b-107">Members</span></span>  
  
|<span data-ttu-id="1b15b-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="1b15b-108">Member</span></span>|<span data-ttu-id="1b15b-109">説明</span><span class="sxs-lookup"><span data-stu-id="1b15b-109">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="1b15b-110">フラグが設定されていません。</span><span class="sxs-lookup"><span data-stu-id="1b15b-110">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="1b15b-111">CLR アセンブリ参照クロージャウォーク中にアセンブリ参照を追加するための [ICorProfilerCallback6:: GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) コールバックを制御します。</span><span class="sxs-lookup"><span data-stu-id="1b15b-111">Controls the [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="1b15b-112">メモリ内モジュールに関連付けられているシンボルストリームに更新するための [ICorProfilerCallback7:: Moduleinmemorysymbol supcallback](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) を制御します。</span><span class="sxs-lookup"><span data-stu-id="1b15b-112">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="1b15b-113">動的メソッドがガベージコレクションおよびアンロードされたことを示す [ICorProfilerCallback9::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) コールバックを制御します。</span><span class="sxs-lookup"><span data-stu-id="1b15b-113">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="1b15b-114">.NET Core 3.0 以降のバージョンのみ: プロファイラーの階層化された [コンパイル](../../../core/whats-new/dotnet-core-3-0.md) を無効にします。</span><span class="sxs-lookup"><span data-stu-id="1b15b-114">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="1b15b-115">.NET Core 3.0 以降のバージョンのみ: と比較して、軽量の GC プロファイルオプションが用意されて [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md) います。</span><span class="sxs-lookup"><span data-stu-id="1b15b-115">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="1b15b-116">[GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)、 [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)、および[GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md)の各コールバックのみを制御します。</span><span class="sxs-lookup"><span data-stu-id="1b15b-116">Controls only the  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="1b15b-117">フラグとは異なり `COR_PRF_MONITOR_GC` 、 `COR_PRF_HIGH_BASIC_GC` は同時実行ガベージコレクションを無効にしません。</span><span class="sxs-lookup"><span data-stu-id="1b15b-117">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="1b15b-118">.NET Core 3.0 以降のバージョンのみ: Gc を圧縮するために、 [Movedreferences](icorprofilercallback-movedreferences-method.md) と [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) コールバックを有効にします。</span><span class="sxs-lookup"><span data-stu-id="1b15b-118">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="1b15b-119">.NET Core 3.0 以降のバージョンのみ: に似て [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md) いますが、ラージオブジェクトヒープ (LOH) に対してのみオブジェクト割り当てに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="1b15b-119">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="1b15b-120">プロファイルが強化されたイメージを必要とするすべての `COR_PRF_HIGH_MONITOR` フラグを表しています。</span><span class="sxs-lookup"><span data-stu-id="1b15b-120">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="1b15b-121">これは、 `COR_PRF_REQUIRE_PROFILE_IMAGE` [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) 列挙のフラグに対応します。</span><span class="sxs-lookup"><span data-stu-id="1b15b-121">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="1b15b-122">プロファイラーが実行中のアプリケーションに割り当てられた後に設定することが可能な、`COR_PRF_HIGH_MONITOR` のすべてのフラグを表します。</span><span class="sxs-lookup"><span data-stu-id="1b15b-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="1b15b-123">初期化中にのみ設定可能な、`COR_PRF_HIGH_MONITOR` のすべてのフラグを表します。</span><span class="sxs-lookup"><span data-stu-id="1b15b-123">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="1b15b-124">他の場所でこれらのフラグを変更しようとすると、エラーを表す `HRESULT` 値が生じます。</span><span class="sxs-lookup"><span data-stu-id="1b15b-124">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b15b-125">解説</span><span class="sxs-lookup"><span data-stu-id="1b15b-125">Remarks</span></span>

<span data-ttu-id="1b15b-126">`COR_PRF_HIGH_MONITOR`フラグは、 `pdwEventsHigh` [ICorProfilerInfo5:: GetEventMask2](icorprofilerinfo5-geteventmask2-method.md)メソッドと[ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)メソッドのパラメーターと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b15b-126">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="1b15b-127">.NET Framework 4.6.1 以降では、の値が `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` 0 から (0x00000002) に変更されました `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` 。</span><span class="sxs-lookup"><span data-stu-id="1b15b-127">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="1b15b-128">.NET Framework 4.7.2 以降では、値がからに変更されました `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS` 。</span><span class="sxs-lookup"><span data-stu-id="1b15b-128">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>

<span data-ttu-id="1b15b-129">`COR_PRF_HIGH_MONITOR_IMMUTABLE` は、初期化中にのみ設定できるすべてのフラグを表すビットマスクであることを意図しています。</span><span class="sxs-lookup"><span data-stu-id="1b15b-129">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="1b15b-130">これらのフラグを他の場所で変更しようとすると、が失敗 `HRESULT` します。</span><span class="sxs-lookup"><span data-stu-id="1b15b-130">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b15b-131">要件</span><span class="sxs-lookup"><span data-stu-id="1b15b-131">Requirements</span></span>

<span data-ttu-id="1b15b-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b15b-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="1b15b-133">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b15b-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="1b15b-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b15b-134">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="1b15b-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b15b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b15b-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b15b-136">See also</span></span>

- [<span data-ttu-id="1b15b-137">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="1b15b-137">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="1b15b-138">COR_PRF_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="1b15b-138">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="1b15b-139">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b15b-139">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
