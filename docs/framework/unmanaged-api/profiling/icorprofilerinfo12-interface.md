---
description: '詳細情報: ICorProfilerInfo12 インターフェイス'
title: ICorProfilerInfo12 インターフェイス
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a8b91eba686478c3e825ae15d6ae95bd0ffad944
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805728"
---
# <a name="icorprofilerinfo12-interface"></a><span data-ttu-id="64cb6-103">ICorProfilerInfo12 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64cb6-103">ICorProfilerInfo12 Interface</span></span>

 <span data-ttu-id="64cb6-104">EventPipe セッション、イベント、プロバイダーを作成するためのメソッドを提供する、[ICorProfilerInfo11](icorprofilerinfo11-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="64cb6-104">A subclass of [ICorProfilerInfo11](icorprofilerinfo11-interface.md) that provides methods to create EventPipe sessions, events, and providers.</span></span>
  
## <a name="methods"></a><span data-ttu-id="64cb6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="64cb6-105">Methods</span></span>  
  
|<span data-ttu-id="64cb6-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="64cb6-106">Method</span></span>|<span data-ttu-id="64cb6-107">説明</span><span class="sxs-lookup"><span data-stu-id="64cb6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64cb6-108">EventPipeStartSession メソッド</span><span class="sxs-lookup"><span data-stu-id="64cb6-108">EventPipeStartSession Method</span></span>](icorprofilerinfo12-eventpipestartsession-method.md)|<span data-ttu-id="64cb6-109">プロファイラーの EventPipe セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="64cb6-109">Starts a profiler EventPipe session.</span></span>|
|[<span data-ttu-id="64cb6-110">EventPipeAddProviderToSession メソッド</span><span class="sxs-lookup"><span data-stu-id="64cb6-110">EventPipeAddProviderToSession Method</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)|<span data-ttu-id="64cb6-111">既存の EventPipe セッションにプロバイダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="64cb6-111">Adds a provider to an existing EventPipe session.</span></span>|
|[<span data-ttu-id="64cb6-112">EventPipeStopSession メソッド</span><span class="sxs-lookup"><span data-stu-id="64cb6-112">EventPipeStopSession Method</span></span>](icorprofilerinfo12-eventpipestopsession-method.md)|<span data-ttu-id="64cb6-113">EventPipe セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="64cb6-113">Stops an EventPipe session.</span></span>|
|[<span data-ttu-id="64cb6-114">EventPipeCreateProvider メソッド</span><span class="sxs-lookup"><span data-stu-id="64cb6-114">EventPipeCreateProvider Method</span></span>](icorprofilerinfo12-eventpipecreateprovider-method.md)|<span data-ttu-id="64cb6-115">EventPipe プロバイダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="64cb6-115">Creates an EventPipe provider.</span></span>|  
|[<span data-ttu-id="64cb6-116">EventPipeGetProviderInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="64cb6-116">EventPipeGetProviderInfo Method</span></span>](icorprofilerinfo12-eventpipegetproviderinfo-method.md)|<span data-ttu-id="64cb6-117">EventPipe プロバイダーの名前をその ID から取得します。</span><span class="sxs-lookup"><span data-stu-id="64cb6-117">Gets the name of an EventPipe provider from its ID.</span></span>|
|[<span data-ttu-id="64cb6-118">EventPipeDefineEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="64cb6-118">EventPipeDefineEvent Method</span></span>](icorprofilerinfo12-eventpipedefineevent-method.md)|<span data-ttu-id="64cb6-119">既存の EventPipe プロバイダーでイベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="64cb6-119">Defines an event on an existing EventPipe provider.</span></span>|  
|[<span data-ttu-id="64cb6-120">EventPipeWriteEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="64cb6-120">EventPipeWriteEvent Method</span></span>](icorprofilerinfo12-eventpipewriteevent-method.md)|<span data-ttu-id="64cb6-121">EventPipe イベントを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="64cb6-121">Writes an EventPipe event.</span></span>|
  
## <a name="requirements"></a><span data-ttu-id="64cb6-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="64cb6-122">Requirements</span></span>  

<span data-ttu-id="64cb6-123">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="64cb6-123">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="64cb6-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64cb6-124">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="64cb6-125">**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64cb6-125">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="64cb6-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="64cb6-126">See also</span></span>

- [<span data-ttu-id="64cb6-127">EventPipe の概要</span><span class="sxs-lookup"><span data-stu-id="64cb6-127">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="64cb6-128">既知のイベント プロバイダー</span><span class="sxs-lookup"><span data-stu-id="64cb6-128">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="64cb6-129">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="64cb6-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="64cb6-130">ICorProfilerCallback10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64cb6-130">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
