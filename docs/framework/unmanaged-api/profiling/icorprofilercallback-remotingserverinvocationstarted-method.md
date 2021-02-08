---
description: '詳細について: ICorProfilerCallback:: RemotingServerInvocationStarted メソッド'
title: ICorProfilerCallback::RemotingServerInvocationStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type:
- apiref
ms.openlocfilehash: 8a27e3e545b9ff2812561f5faa7ebfe70d41f015
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788905"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="43ef1-103">ICorProfilerCallback::RemotingServerInvocationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="43ef1-103">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>

<span data-ttu-id="43ef1-104">プロセスがリモートメソッド呼び出し要求に応答してメソッドを呼び出していることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="43ef1-104">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ef1-105">構文</span><span class="sxs-lookup"><span data-stu-id="43ef1-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="43ef1-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="43ef1-106">Requirements</span></span>  

 <span data-ttu-id="43ef1-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43ef1-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ef1-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="43ef1-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43ef1-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43ef1-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43ef1-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ef1-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ef1-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="43ef1-111">See also</span></span>

- [<span data-ttu-id="43ef1-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="43ef1-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
