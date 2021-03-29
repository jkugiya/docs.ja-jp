---
description: '詳細情報: ICorProfilerInfo12::EventPipeStopSession メソッド'
title: ICorProfilerInfo12::EventPipeStopSession メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeStopSession
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c1b104f63755bcec52a113be7e2aa9af76ecd34e
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805715"
---
# <a name="icorprofilerinfo12eventpipestopsession-method"></a><span data-ttu-id="00af5-103">ICorProfilerInfo12::EventPipeStopSession メソッド</span><span class="sxs-lookup"><span data-stu-id="00af5-103">ICorProfilerInfo12::EventPipeStopSession Method</span></span>

<span data-ttu-id="00af5-104">EventPipe セッションを停止し、今後のイベントがセッションに書き込まれないようにします。</span><span class="sxs-lookup"><span data-stu-id="00af5-104">Stops an EventPipe session, preventing any future events from being written to the session.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="00af5-105">構文</span><span class="sxs-lookup"><span data-stu-id="00af5-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeStopSession(
        [in] EVENTPIPE_SESSION session);
```  
  
## <a name="parameters"></a><span data-ttu-id="00af5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00af5-106">Parameters</span></span>

<span data-ttu-id="00af5-107">`session` [入力] 停止するセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="00af5-107">`session` [in] The ID of the session to stop.</span></span>

## <a name="requirements"></a><span data-ttu-id="00af5-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="00af5-108">Requirements</span></span>  

<span data-ttu-id="00af5-109">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="00af5-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="00af5-110">**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00af5-110">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="00af5-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="00af5-111">See also</span></span>

- [<span data-ttu-id="00af5-112">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="00af5-112">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="00af5-113">ICorProfilerCallback10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00af5-113">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="00af5-114">ICorProfilerInfo12 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00af5-114">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
