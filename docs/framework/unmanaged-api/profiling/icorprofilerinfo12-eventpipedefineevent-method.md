---
description: '詳細情報: ICorProfilerInfo12::EventPipeDefineEvent メソッド'
title: ICorProfilerInfo12::EventPipeDefineEvent メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeDefineEvent
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 845f7f26dce7aa0f4b7d895b9f04cc89e7ac7192
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805754"
---
# <a name="icorprofilerinfo12eventpipedefineevent-method"></a><span data-ttu-id="cd6f9-103">ICorProfilerInfo12::EventPipeDefineEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="cd6f9-103">ICorProfilerInfo12::EventPipeDefineEvent Method</span></span>

<span data-ttu-id="cd6f9-104">既存のプロバイダーで EventPipe イベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-104">Defines an EventPipe event on an existing provider.</span></span> <span data-ttu-id="cd6f9-105">このプロバイダーを使用すると、他のリスナーが受信できる EventPipe イベントを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-105">This provider can be used to write EventPipe events that other listeners can receive.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="cd6f9-106">構文</span><span class="sxs-lookup"><span data-stu-id="cd6f9-106">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeDefineEvent(
                [in] EVENTPIPE_PROVIDER     provider,
                [in, string] const WCHAR   *eventName,
                [in] UINT32                 eventID,
                [in] UINT64                 keywords,
                [in] UINT32                 eventVersion,
                [in] UINT32                 level,
                [in] UINT8                  opcode,
                [in] BOOL                   needStack,
                [in] UINT32                 cParamDescs,
                [in, size_is(cParamDescs)]
                     COR_PRF_EVENTPIPE_PARAM_DESC pParamDescs[],
                [out] EVENTPIPE_EVENT      *pEvent);
```  
  
## <a name="parameters"></a><span data-ttu-id="cd6f9-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd6f9-107">Parameters</span></span>

<span data-ttu-id="cd6f9-108">`provider` [入力] イベントを定義するプロバイダーの ID。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-108">`provider` [in] The ID of the provider to define an event on.</span></span>

<span data-ttu-id="cd6f9-109">`eventName` [入力] イベント名が含まれている null で終わるワイド文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-109">`eventName` [in] A pointer to a null terminated wide character string that contains the event name.</span></span>

<span data-ttu-id="cd6f9-110">`eventID` [入力] 定義されるイベントの ID。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-110">`eventID` [in] The ID of the event being defined.</span></span>

<span data-ttu-id="cd6f9-111">`keywords` [入力] 定義されるイベントのキーワード。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-111">`keywords` [in] The keywords of the event being defined.</span></span>

<span data-ttu-id="cd6f9-112">`eventVersion` [入力] 定義されるイベントのバージョン。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-112">`eventVersion` [in] The version of the event being defined.</span></span>

<span data-ttu-id="cd6f9-113">`level` [入力] 定義されるイベントのレベル。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-113">`level` [in] The level of the event being defined.</span></span>

<span data-ttu-id="cd6f9-114">`opcode` [入力] 定義されるイベントのオペコード。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-114">`opcode` [in] The opcode of the event being defined.</span></span>

<span data-ttu-id="cd6f9-115">`needStack` [入力] このイベントが起動されるたびにマネージド スタックを収集するかどうかを示す `BOOL`。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-115">`needStack` [in] A `BOOL` indicating whether managed stacks should be collected each time this event fires.</span></span>

<span data-ttu-id="cd6f9-116">`cParamDescs` [入力] `pParamDescs` 内のパラメーターの数。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-116">`cParamDescs` [in] The count of the number of parameters in `pParamDescs`.</span></span>

<span data-ttu-id="cd6f9-117">`pParamDescs` [入力] 定義されるイベントへのパラメーターの型を定義している `COR_PRF_EVENTPIPE_PARAM_DESC` の配列。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-117">`pParamDescs` [in] An array of `COR_PRF_EVENTPIPE_PARAM_DESC` defining the parameter types to the event being defined.</span></span>

<span data-ttu-id="cd6f9-118">`pEvent` [出力] 関数が戻るときに定義されるイベントの ID が入力される、呼び出し元によって提供されたポインター。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-118">`pEvent` [out] A caller provided pointer that will be filled with the ID of the event being defined when the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd6f9-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="cd6f9-119">Requirements</span></span>  

<span data-ttu-id="cd6f9-120">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd6f9-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="cd6f9-121">**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd6f9-121">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cd6f9-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd6f9-122">See also</span></span>

- [<span data-ttu-id="cd6f9-123">EventPipe の概要</span><span class="sxs-lookup"><span data-stu-id="cd6f9-123">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="cd6f9-124">既知のイベント プロバイダー</span><span class="sxs-lookup"><span data-stu-id="cd6f9-124">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="cd6f9-125">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd6f9-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cd6f9-126">ICorProfilerCallback10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd6f9-126">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="cd6f9-127">ICorProfilerInfo12 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd6f9-127">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="cd6f9-128">COR_PRF_EVENTPIPE_PARAM_DESC 構造体</span><span class="sxs-lookup"><span data-stu-id="cd6f9-128">COR_PRF_EVENTPIPE_PARAM_DESC Structure</span></span>](cor-prf-eventpipe-param-desc-structure.md)
