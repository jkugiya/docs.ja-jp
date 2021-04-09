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
ms.openlocfilehash: 6ce96bf301f1c559923df64edd9dd214c28db918
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231311"
---
# <a name="icorprofilercallback10eventpipeprovidercreated-method"></a><span data-ttu-id="234d1-103">ICorProfilerCallback10::EventPipeProviderCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="234d1-103">ICorProfilerCallback10::EventPipeProviderCreated Method</span></span>

<span data-ttu-id="234d1-104">EventPipe プロバイダーが作成されるたびにプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="234d1-104">Notifies the profiler whenever an EventPipe provider is created.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="234d1-105">構文</span><span class="sxs-lookup"><span data-stu-id="234d1-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeProviderCreated([in] EVENTPIPE_PROVIDER provider);
```  
  
## <a name="parameters"></a><span data-ttu-id="234d1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="234d1-106">Parameters</span></span>

<span data-ttu-id="234d1-107">`provider` [入力] 作成されたプロバイダー。</span><span class="sxs-lookup"><span data-stu-id="234d1-107">`provider` [in] The provider that was created.</span></span>

## <a name="requirements"></a><span data-ttu-id="234d1-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="234d1-108">Requirements</span></span>  

<span data-ttu-id="234d1-109">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="234d1-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="234d1-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="234d1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="234d1-111">**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="234d1-111">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="234d1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="234d1-112">See also</span></span>

- [<span data-ttu-id="234d1-113">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="234d1-113">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="234d1-114">ICorProfilerCallback10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="234d1-114">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="234d1-115">ICorProfilerInfo12 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="234d1-115">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="234d1-116">ICorProfilerInfo12.EventPipeAddProviderToSession メソッド</span><span class="sxs-lookup"><span data-stu-id="234d1-116">ICorProfilerInfo12.EventPipeAddProviderToSession Method</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
