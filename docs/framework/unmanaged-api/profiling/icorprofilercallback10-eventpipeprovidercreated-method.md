---
description: '詳細情報: ICorProfilerCallback10::EventPipeProviderCreated メソッド'
title: ICorProfilerCallback10::EventPipeProviderCreated メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10.EventPipeProviderCreated
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4602438148a369f2a2321a2ec2e959cc375e37cf
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805585"
---
# <a name="icorprofilercallback10eventpipeprovidercreated-method"></a><span data-ttu-id="2b5d5-103">ICorProfilerCallback10::EventPipeProviderCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="2b5d5-103">ICorProfilerCallback10::EventPipeProviderCreated Method</span></span>

<span data-ttu-id="2b5d5-104">EventPipe プロバイダーが作成されるたびにプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2b5d5-104">Notifies the profiler whenever an EventPipe provider is created.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="2b5d5-105">構文</span><span class="sxs-lookup"><span data-stu-id="2b5d5-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeProviderCreated([in] EVENTPIPE_PROVIDER provider); 
```  
  
## <a name="parameters"></a><span data-ttu-id="2b5d5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b5d5-106">Parameters</span></span>

<span data-ttu-id="2b5d5-107">`provider` [入力] 作成されたプロバイダー。</span><span class="sxs-lookup"><span data-stu-id="2b5d5-107">`provider` [in] The provider that was created.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b5d5-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="2b5d5-108">Requirements</span></span>  

<span data-ttu-id="2b5d5-109">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b5d5-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="2b5d5-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2b5d5-110">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="2b5d5-111">**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b5d5-111">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b5d5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b5d5-112">See also</span></span>

- [<span data-ttu-id="2b5d5-113">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b5d5-113">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2b5d5-114">ICorProfilerCallback10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b5d5-114">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="2b5d5-115">ICorProfilerInfo12 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b5d5-115">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="2b5d5-116">ICorProfilerInfo12.EventPipeAddProviderToSession メソッド</span><span class="sxs-lookup"><span data-stu-id="2b5d5-116">ICorProfilerInfo12.EventPipeAddProviderToSession Method</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
