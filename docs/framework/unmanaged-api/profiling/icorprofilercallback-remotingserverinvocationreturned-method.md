---
description: '詳細について: ICorProfilerCallback:: RemotingServerInvocationReturned メソッド'
title: ICorProfilerCallback::RemotingServerInvocationReturned メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationReturned
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned method [.NET Framework profiling]
- RemotingServerInvocationReturned method [.NET Framework profiling]
ms.assetid: a4de6805-e159-4280-99e5-3390c86166d0
topic_type:
- apiref
ms.openlocfilehash: 97f9fda42059ac66fc3a29689adc252556798e4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788918"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="75bac-103">ICorProfilerCallback::RemotingServerInvocationReturned メソッド</span><span class="sxs-lookup"><span data-stu-id="75bac-103">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>

<span data-ttu-id="75bac-104">プロセスがリモートメソッド呼び出し要求に応答してメソッドの呼び出しを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="75bac-104">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75bac-105">構文</span><span class="sxs-lookup"><span data-stu-id="75bac-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="75bac-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="75bac-106">Requirements</span></span>  

 <span data-ttu-id="75bac-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75bac-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75bac-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="75bac-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75bac-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75bac-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75bac-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75bac-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75bac-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="75bac-111">See also</span></span>

- [<span data-ttu-id="75bac-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75bac-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
