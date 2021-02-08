---
description: '詳細については、次を参照してください: ICorProfilerCallback7:: Moduleinmemoryシンボル Supmethod'
title: 'ICorProfilerCallback7:: Moduleinmemory メソッド'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: 74adf7edc5269824a924933eb3284a5964e1bac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781728"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="fde97-103">ICorProfilerCallback7:: Moduleinmemory メソッド</span><span class="sxs-lookup"><span data-stu-id="fde97-103">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>

<span data-ttu-id="fde97-104">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="fde97-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="fde97-105">メモリ内モジュールに関連付けられているシンボルストリームが更新されるたびに、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="fde97-105">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fde97-106">構文</span><span class="sxs-lookup"><span data-stu-id="fde97-106">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fde97-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fde97-107">Parameters</span></span>  

 <span data-ttu-id="fde97-108">[入力] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="fde97-108">[in] `moduleId`</span></span>  
 <span data-ttu-id="fde97-109">シンボルストリームが更新されるメモリ内モジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="fde97-109">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fde97-110">解説</span><span class="sxs-lookup"><span data-stu-id="fde97-110">Remarks</span></span>  

 <span data-ttu-id="fde97-111">このコールバックは、 [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)メソッドを呼び出すときに、 [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md)イベントマスクフラグを設定することによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="fde97-111">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fde97-112">このイベントは、api を使用して暗黙的に作成または変更されたシンボルに対しては、現在発生していません <xref:System.Reflection.Emit> 。</span><span class="sxs-lookup"><span data-stu-id="fde97-112">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="fde97-113">アセンブリのシンボルを指定する引数を含むマネージメソッドのオーバーロードのいずれかを呼び出すことによって、シンボルが事前に提供されていても <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> `rawSymbolStore` 、 [moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md) コールバックが発生するまで、ランタイムはシンボリックデータをモジュールに実際に関連付けない場合があります。</span><span class="sxs-lookup"><span data-stu-id="fde97-113">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="fde97-114">このイベントは、後でこのようなモジュールのシンボルを収集する機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="fde97-114">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fde97-115">要件</span><span class="sxs-lookup"><span data-stu-id="fde97-115">Requirements</span></span>  

 <span data-ttu-id="fde97-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fde97-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fde97-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fde97-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fde97-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fde97-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fde97-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fde97-119">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde97-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="fde97-120">See also</span></span>

- [<span data-ttu-id="fde97-121">ModuleLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="fde97-121">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="fde97-122">SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="fde97-122">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="fde97-123">ICorProfilerCallback7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fde97-123">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)
