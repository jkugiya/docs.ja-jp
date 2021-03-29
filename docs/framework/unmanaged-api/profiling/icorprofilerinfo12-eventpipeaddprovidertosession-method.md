---
description: '詳細情報: ICorProfilerInfo12::EventPipeAddProviderToSession メソッド'
title: ICorProfilerInfo12::EventPipeAddProviderToSession メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeAddProviderToSession
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 70654660c496211c20459ef9ba37dfbd96b829b3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805689"
---
# <a name="icorprofilerinfo12eventpipeaddprovidertosession-method"></a><span data-ttu-id="6d98b-103">ICorProfilerInfo12::EventPipeAddProviderToSession メソッド</span><span class="sxs-lookup"><span data-stu-id="6d98b-103">ICorProfilerInfo12::EventPipeAddProviderToSession Method</span></span>

<span data-ttu-id="6d98b-104">既存の EventPipe セッションにプロバイダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="6d98b-104">Adds a provider to an existing EventPipe session.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="6d98b-105">構文</span><span class="sxs-lookup"><span data-stu-id="6d98b-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeAddProviderToSession(
        [in] EVENTPIPE_SESSION                 session,
        [in] COR_PRF_EVENTPIPE_PROVIDER_CONFIG providerConfig);
```  
  
## <a name="parameters"></a><span data-ttu-id="6d98b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d98b-106">Parameters</span></span>

<span data-ttu-id="6d98b-107">`session` [入力] プロバイダーの追加先のセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="6d98b-107">`session` [in] The ID of the session to add the provider to.</span></span>

<span data-ttu-id="6d98b-108">`providerConfig` [入力] セッションに追加するプロバイダーを記述した `COR_PRF_EVENTPIPE_PROVIDER_CONFIG`。</span><span class="sxs-lookup"><span data-stu-id="6d98b-108">`providerConfig` [in] A `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` describing the provider to add to the session.</span></span>

## <a name="requirements"></a><span data-ttu-id="6d98b-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="6d98b-109">Requirements</span></span>  

<span data-ttu-id="6d98b-110">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d98b-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="6d98b-111">**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d98b-111">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6d98b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d98b-112">See also</span></span>

- [<span data-ttu-id="6d98b-113">EventPipe の概要</span><span class="sxs-lookup"><span data-stu-id="6d98b-113">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="6d98b-114">既知のイベント プロバイダー</span><span class="sxs-lookup"><span data-stu-id="6d98b-114">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="6d98b-115">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d98b-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6d98b-116">ICorProfilerCallback10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d98b-116">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="6d98b-117">ICorProfilerInfo12 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d98b-117">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="6d98b-118">COR_PRF_EVENTPIPE_PROVIDER_CONFIG 構造体</span><span class="sxs-lookup"><span data-stu-id="6d98b-118">COR_PRF_EVENTPIPE_PROVIDER_CONFIG Structure</span></span>](cor-prf-eventpipe-provider-config-structure.md)
