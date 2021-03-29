---
description: '詳細情報: ICorProfilerInfo12::EventPipeGetProviderInfo メソッド'
title: ICorProfilerInfo12::EventPipeGetProviderInfo メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeGetProviderInfo
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 7bc7ffe1c31e88dc1c65f1670f9bd179e732abfe
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805702"
---
# <a name="icorprofilerinfo12eventpipegetproviderinfo-method"></a><span data-ttu-id="0faf3-103">ICorProfilerInfo12::EventPipeGetProviderInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="0faf3-103">ICorProfilerInfo12::EventPipeGetProviderInfo Method</span></span>

<span data-ttu-id="0faf3-104">他の EventPipe リスナーが受信するイベントを書き込むためにプロファイラーで使用できる EventPipe プロバイダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0faf3-104">Creates an EventPipe provider that the profiler can use to write events for other EventPipe listeners to receive.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="0faf3-105">構文</span><span class="sxs-lookup"><span data-stu-id="0faf3-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeGetProviderInfo(
                [in] EVENTPIPE_PROVIDER provider,
                [in]  ULONG      cchName,
                [out] ULONG      *pcchName,
                [out, annotation("_Out_writes_to_(cchName, *pcchName)")]
                      WCHAR      providerName[]);
```  
  
## <a name="parameters"></a><span data-ttu-id="0faf3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0faf3-106">Parameters</span></span>

<span data-ttu-id="0faf3-107">`provider` [入力] 名前を指定するプロバイダーの ID。</span><span class="sxs-lookup"><span data-stu-id="0faf3-107">`provider` [in] The ID of the provider to provide the name for.</span></span>

<span data-ttu-id="0faf3-108">`cchName` [入力] `providerName` のサイズ (文字数)。</span><span class="sxs-lookup"><span data-stu-id="0faf3-108">`cchName` [in] The size, in characters, of `providerName`.</span></span>

<span data-ttu-id="0faf3-109">`pcchName` [出力] `providerName` の合計の文字の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0faf3-109">`pcchName` [out] A pointer to the total character length of `providerName`.</span></span>

<span data-ttu-id="0faf3-110">`providerName` [出力] 呼び出し元によって提供されたワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="0faf3-110">`providerName` [out] A caller provided wide character buffer.</span></span> <span data-ttu-id="0faf3-111">関数が戻るとき、このバッファーにプロバイダーの名前が格納されます。</span><span class="sxs-lookup"><span data-stu-id="0faf3-111">When the function returns the buffer will contain the name of the provider.</span></span>

## <a name="requirements"></a><span data-ttu-id="0faf3-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="0faf3-112">Requirements</span></span>  

<span data-ttu-id="0faf3-113">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0faf3-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="0faf3-114">**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0faf3-114">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0faf3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0faf3-115">See also</span></span>

- [<span data-ttu-id="0faf3-116">EventPipe の概要</span><span class="sxs-lookup"><span data-stu-id="0faf3-116">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="0faf3-117">既知のイベント プロバイダー</span><span class="sxs-lookup"><span data-stu-id="0faf3-117">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="0faf3-118">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0faf3-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0faf3-119">ICorProfilerCallback10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0faf3-119">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="0faf3-120">ICorProfilerInfo12 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0faf3-120">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
