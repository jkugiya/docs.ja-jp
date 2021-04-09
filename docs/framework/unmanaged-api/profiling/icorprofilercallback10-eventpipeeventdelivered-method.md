---
description: '詳細情報: ICorProfilerCallback10::EventPipeEventDelivered メソッド'
title: ICorProfilerCallback10::EventPipeEventDelivered メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10.EventPipeEventDelivered
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 73f3eb64671b22b1ec16b5a5b1b24115f7f65f6d
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231337"
---
# <a name="icorprofilercallback10eventpipeeventdelivered-method"></a><span data-ttu-id="8719b-103">ICorProfilerCallback10::EventPipeEventDelivered メソッド</span><span class="sxs-lookup"><span data-stu-id="8719b-103">ICorProfilerCallback10::EventPipeEventDelivered Method</span></span>

<span data-ttu-id="8719b-104">EventPipe イベントがそのプロファイラーの現在アクティブなセッションに配信されるたびにプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8719b-104">Notifies the profiler whenever an EventPipe event has been delivered to the profiler's currently active session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8719b-105">構文</span><span class="sxs-lookup"><span data-stu-id="8719b-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeEventDelivered(
        [in] EVENTPIPE_PROVIDER provider,
        [in] DWORD eventId,
        [in] DWORD eventVersion,
        [in] ULONG cbMetadataBlob,
        [in, size_is(cbMetadataBlob)] LPCBYTE metadataBlob,
        [in] ULONG cbEventData,
        [in, size_is(cbEventData)] LPCBYTE eventData,
        [in] LPCGUID pActivityId,
        [in] LPCGUID pRelatedActivityId,
        [in] ThreadID eventThread,
        [in] ULONG numStackFrames,
        [in, length_is(numStackFrames)] UINT_PTR stackFrames[]);
```  
  
## <a name="parameters"></a><span data-ttu-id="8719b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8719b-106">Parameters</span></span>

<span data-ttu-id="8719b-107">`provider` [入力] このイベントの発信元のプロバイダー。</span><span class="sxs-lookup"><span data-stu-id="8719b-107">`provider` [in] The provider that this event originated from.</span></span>

<span data-ttu-id="8719b-108">`eventId` [入力] 配信されるイベントの ID。</span><span class="sxs-lookup"><span data-stu-id="8719b-108">`eventId` [in] The ID of the event being delivered.</span></span>

<span data-ttu-id="8719b-109">`eventVersion` [入力] 配信されるイベントのバージョン。</span><span class="sxs-lookup"><span data-stu-id="8719b-109">`eventVersion` [in] The version of the event being delivered.</span></span>

<span data-ttu-id="8719b-110">`cbMetadataBlob` [入力] `metadataBlob` の長さ (バイト数)。</span><span class="sxs-lookup"><span data-stu-id="8719b-110">`cbMetadataBlob` [in] The length, in bytes, of `metadataBlob`.</span></span>

<span data-ttu-id="8719b-111">`metadataBlob` [入力] イベントのメタデータ BLOB へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8719b-111">`metadataBlob` [in] A pointer to the metadata blob for the event.</span></span>

<span data-ttu-id="8719b-112">`cbEventData` [入力] `eventData` の長さ (バイト数)。</span><span class="sxs-lookup"><span data-stu-id="8719b-112">`cbEventData` [in] The length, in bytes, of `eventData`.</span></span>

<span data-ttu-id="8719b-113">`eventData` [入力] イベントのペイロード。</span><span class="sxs-lookup"><span data-stu-id="8719b-113">`eventData` [in] The payload for the event.</span></span>

<span data-ttu-id="8719b-114">`pActivityId` [入力] イベントのアクティビティ ID を表す GUID へのポインター、または NULL。</span><span class="sxs-lookup"><span data-stu-id="8719b-114">`pActivityId` [in] A pointer to the GUID that represents the event's activity ID, or NULL.</span></span>

<span data-ttu-id="8719b-115">`pRelatedActivityId` [入力] イベントの関連アクティビティ ID を表す GUID へのポインター、または NULL。</span><span class="sxs-lookup"><span data-stu-id="8719b-115">`pRelatedActivityId` [in] A pointer to the GUID that represents the event's related activity ID, or NULL.</span></span>

<span data-ttu-id="8719b-116">`eventThread` [入力] イベントが発生したスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="8719b-116">`eventThread` [in] The ID of the thread the event occurred on.</span></span>

<span data-ttu-id="8719b-117">`numStackFrames` [入力] `stackFrames` 配列内の要素の数。</span><span class="sxs-lookup"><span data-stu-id="8719b-117">`numStackFrames` [in] The number of elements in the `stackFrames` array.</span></span>

<span data-ttu-id="8719b-118">`stackFrames` [入力] イベントのマネージド呼び出し履歴を表すコード アドレスの配列。</span><span class="sxs-lookup"><span data-stu-id="8719b-118">`stackFrames` [in] An array of code addresses representing the managed callstack of the event.</span></span>

## <a name="requirements"></a><span data-ttu-id="8719b-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="8719b-119">Requirements</span></span>  

<span data-ttu-id="8719b-120">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8719b-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="8719b-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8719b-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="8719b-122">**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8719b-122">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8719b-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8719b-123">See also</span></span>

- [<span data-ttu-id="8719b-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8719b-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8719b-125">ICorProfilerCallback10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8719b-125">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="8719b-126">ICorProfilerInfo12 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8719b-126">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="8719b-127">ICorProfilerInfo12.EventPipeStartSession メソッド</span><span class="sxs-lookup"><span data-stu-id="8719b-127">ICorProfilerInfo12.EventPipeStartSession Method</span></span>](icorprofilerinfo12-eventpipestartsession-method.md)
