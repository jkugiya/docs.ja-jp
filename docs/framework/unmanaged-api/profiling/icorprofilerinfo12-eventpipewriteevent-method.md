---
description: '詳細情報: ICorProfilerInfo12::EventPipeWriteEvent メソッド'
title: ICorProfilerInfo12::EventPipeWriteEvent メソッドド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeWriteEvent
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a0a06ff0fa1c936518586834f4dfc73810ef0e44
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805741"
---
# <a name="icorprofilerinfo12eventpipewriteevent-method"></a><span data-ttu-id="f9d5d-103">ICorProfilerInfo12::EventPipeWriteEvent メソッドド</span><span class="sxs-lookup"><span data-stu-id="f9d5d-103">ICorProfilerInfo12::EventPipeWriteEvent Method</span></span>

<span data-ttu-id="f9d5d-104">このイベントを有効にしているすべてのリスナーに EventPipe イベントを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f9d5d-104">Writes an EventPipe event to any listeners who have enabled this event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="f9d5d-105">構文</span><span class="sxs-lookup"><span data-stu-id="f9d5d-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeWriteEvent(
                [in] EVENTPIPE_EVENT    event,
                [in] UINT32             cData,
                [in, size_is(cData)]
                     COR_PRF_EVENT_DATA data[],
                [in] LPCGUID            pActivityId,
                [in] LPCGUID            pRelatedActivityId);
```  
  
## <a name="parameters"></a><span data-ttu-id="f9d5d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9d5d-106">Parameters</span></span>

<span data-ttu-id="f9d5d-107">`event` [入力] 書き込まれるイベントの ID。</span><span class="sxs-lookup"><span data-stu-id="f9d5d-107">`event` [in] The ID of the event being written.</span></span>

<span data-ttu-id="f9d5d-108">`cData` [入力] `data` 内の要素の数。</span><span class="sxs-lookup"><span data-stu-id="f9d5d-108">`cData` [in] The number of elements in `data`.</span></span>

<span data-ttu-id="f9d5d-109">`data` [入力] イベント引数が含まれている `COR_PRF_EVENT_DATA` の配列。</span><span class="sxs-lookup"><span data-stu-id="f9d5d-109">`data` [in] An array of `COR_PRF_EVENT_DATA` containing the event arguments.</span></span>

<span data-ttu-id="f9d5d-110">`pActivityId` [入力] イベントのアクティビティ ID を指定する GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f9d5d-110">`pActivityId` [in] A pointer to a GUID specifying the event's activity ID.</span></span>

<span data-ttu-id="f9d5d-111">`pRelatedActivityId` [入力] イベントの関連アクティビティ ID を指定する GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f9d5d-111">`pRelatedActivityId` [in] A pointer to a GUID specifying the event's related activity ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9d5d-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="f9d5d-112">Requirements</span></span>  

<span data-ttu-id="f9d5d-113">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9d5d-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="f9d5d-114">**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9d5d-114">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f9d5d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9d5d-115">See also</span></span>

- [<span data-ttu-id="f9d5d-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9d5d-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f9d5d-117">ICorProfilerCallback10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9d5d-117">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="f9d5d-118">ICorProfilerInfo12 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9d5d-118">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="f9d5d-119">COR_PRF_EVENT_DATA 構造体</span><span class="sxs-lookup"><span data-stu-id="f9d5d-119">COR_PRF_EVENT_DATA Structure</span></span>](cor-prf-event-data-structure.md)
