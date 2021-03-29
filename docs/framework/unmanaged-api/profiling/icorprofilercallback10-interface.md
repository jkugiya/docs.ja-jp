---
description: '詳細情報: ICorProfilerCallback10 インターフェイス'
title: ICorProfilerCallback10 インターフェイス
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d9091dc81307e2dcb83e74154a8217dffaa1e7a2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805650"
---
# <a name="icorprofilercallback10-interface"></a><span data-ttu-id="29b8d-103">ICorProfilerCallback10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29b8d-103">ICorProfilerCallback10 Interface</span></span>

 <span data-ttu-id="29b8d-104">プロファイラーに、EventPipe イベントがそのプロファイラーの現在アクティブなセッションに配信されたことを通知するためのコールバック メソッドを提供する、[ICorProfilerCallback9](icorprofilercallback9-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="29b8d-104">A subclass of [ICorProfilerCallback9](icorprofilercallback9-interface.md) that provides callback methods to notify the profiler that EventPipe events have been delivered to the profiler's currently active session.</span></span>
  
## <a name="methods"></a><span data-ttu-id="29b8d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="29b8d-105">Methods</span></span>  
  
|<span data-ttu-id="29b8d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="29b8d-106">Method</span></span>|<span data-ttu-id="29b8d-107">説明</span><span class="sxs-lookup"><span data-stu-id="29b8d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29b8d-108">EventPipeEventDelivered メソッド</span><span class="sxs-lookup"><span data-stu-id="29b8d-108">EventPipeEventDelivered Method</span></span>](icorprofilercallback10-eventpipeeventdelivered-method.md)|<span data-ttu-id="29b8d-109">プロファイラーに、EventPipe イベントがそのプロファイラーが開いているセッションに配信されたことを通知します。</span><span class="sxs-lookup"><span data-stu-id="29b8d-109">Notifies the profiler that an EventPipe event has been delivered to the session that the profiler has open.</span></span>|
|[<span data-ttu-id="29b8d-110">EventPipeProviderCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="29b8d-110">EventPipeProviderCreated Method</span></span>](icorprofilercallback10-eventpipeprovidercreated-method.md)|<span data-ttu-id="29b8d-111">プロファイラーに、EventPipe プロバイダーが作成され、そのプロバイダーを自身のセッションに追加できるようになったことを通知します。</span><span class="sxs-lookup"><span data-stu-id="29b8d-111">Notifies the profiler that an EventPipe provider has been created, allowing the profiler to add that provider the their session.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29b8d-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="29b8d-112">Requirements</span></span>  

<span data-ttu-id="29b8d-113">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="29b8d-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="29b8d-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29b8d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="29b8d-115">**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29b8d-115">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="29b8d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="29b8d-116">See also</span></span>

- [<span data-ttu-id="29b8d-117">EventPipe の概要</span><span class="sxs-lookup"><span data-stu-id="29b8d-117">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="29b8d-118">既知のイベント プロバイダー</span><span class="sxs-lookup"><span data-stu-id="29b8d-118">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="29b8d-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="29b8d-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="29b8d-120">ICorProfilerInfo12 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29b8d-120">ICorProfilerInfo12 Interface</span></span>](ICorProfilerInfo12-interface.md)
- [<span data-ttu-id="29b8d-121">ICorProfilerInfo12.EventPipeStartSession メソッド</span><span class="sxs-lookup"><span data-stu-id="29b8d-121">ICorProfilerInfo12.EventPipeStartSession method</span></span>](ICorProfilerInfo12-eventpipestartsession-method.md)
- [<span data-ttu-id="29b8d-122">ICorProfilerInfo12.EventPipeStopSession メソッド</span><span class="sxs-lookup"><span data-stu-id="29b8d-122">ICorProfilerInfo12.EventPipeStopSession method</span></span>](ICorProfilerInfo12-eventpipestopsession-method.md)
