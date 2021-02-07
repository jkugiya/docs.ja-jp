---
description: '詳細情報: ICorProfilerCallback:: Initialize メソッド'
title: ICorProfilerCallback::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: b3ff579dee384b331450aa54aace39890febfe30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705942"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="ed2f6-103">ICorProfilerCallback::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="ed2f6-103">ICorProfilerCallback::Initialize Method</span></span>

<span data-ttu-id="ed2f6-104">新しい共通言語ランタイム (CLR) アプリケーションが開始されるたびに、コードプロファイラーを初期化するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ed2f6-104">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed2f6-105">構文</span><span class="sxs-lookup"><span data-stu-id="ed2f6-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed2f6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ed2f6-106">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="ed2f6-107">\[in) プロファイラーが[ICorProfilerInfo](icorprofilerinfo-interface.md)インターフェイスポインターを照会する必要がある[IUnknown](/cpp/atl/iunknown)インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ed2f6-107">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="ed2f6-108">解説</span><span class="sxs-lookup"><span data-stu-id="ed2f6-108">Remarks</span></span>  

 <span data-ttu-id="ed2f6-109">`Initialize`呼び出しは、変更できないコールバックを有効 (または無効) にする唯一の機会です。</span><span class="sxs-lookup"><span data-stu-id="ed2f6-109">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="ed2f6-110">呼び出しによってコールバックが有効になると `Initialize` 、後で [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)を使用して無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ed2f6-110">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="ed2f6-111">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列挙の COR_PRF_MONITOR_IMMUTABLE 値は、どのイベントが不変であるかを示します。</span><span class="sxs-lookup"><span data-stu-id="ed2f6-111">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed2f6-112">要件</span><span class="sxs-lookup"><span data-stu-id="ed2f6-112">Requirements</span></span>  

 <span data-ttu-id="ed2f6-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed2f6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed2f6-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ed2f6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed2f6-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed2f6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed2f6-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed2f6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed2f6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed2f6-117">See also</span></span>

- [<span data-ttu-id="ed2f6-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed2f6-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ed2f6-119">Shutdown メソッド</span><span class="sxs-lookup"><span data-stu-id="ed2f6-119">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
