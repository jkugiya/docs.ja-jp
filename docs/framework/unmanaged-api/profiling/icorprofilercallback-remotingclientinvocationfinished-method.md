---
description: '詳細について: ICorProfilerCallback:: RemotingClientInvocationFinished メソッド'
title: ICorProfilerCallback::RemotingClientInvocationFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
ms.openlocfilehash: bc15139e10b7634c50604d9a05ba290566145c21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648008"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="10d6b-103">ICorProfilerCallback::RemotingClientInvocationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="10d6b-103">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>

<span data-ttu-id="10d6b-104">リモート処理呼び出しがクライアントで完了まで実行されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="10d6b-104">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10d6b-105">構文</span><span class="sxs-lookup"><span data-stu-id="10d6b-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="10d6b-106">解説</span><span class="sxs-lookup"><span data-stu-id="10d6b-106">Remarks</span></span>  

 <span data-ttu-id="10d6b-107">リモート処理の呼び出しが同期されている場合は、サーバー上でも完了まで実行されます。</span><span class="sxs-lookup"><span data-stu-id="10d6b-107">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="10d6b-108">リモート処理呼び出しが非同期の場合は、呼び出しが処理されるときに応答が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="10d6b-108">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="10d6b-109">応答が予想される場合は、 [ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) の呼び出しとして、および `RemotingClientInvocationFinished` 非同期呼び出しの必要なセカンダリ処理を示すための追加の呼び出しとして発生します。</span><span class="sxs-lookup"><span data-stu-id="10d6b-109">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="10d6b-110">次のコールバックの各ペアは、同じスレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="10d6b-110">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="10d6b-111">`RemotingClientInvocationStarted` and [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="10d6b-111">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="10d6b-112">[ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) と [ICorProfilerCallback:: RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="10d6b-112">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="10d6b-113">[ICorProfilerCallback:: RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) と [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="10d6b-113">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="10d6b-114">リモート処理のコールバックでは、次の問題に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10d6b-114">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="10d6b-115">リモート処理関数の実行はプロファイラー API によっては反映されないため、クライアントから呼び出され、サーバーで実行される関数の通知は正しく受信されません。</span><span class="sxs-lookup"><span data-stu-id="10d6b-115">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="10d6b-116">実際の呼び出しは、プロキシオブジェクトを介して行われます。プロファイラーには、特定の関数が JIT コンパイルされていても使用されていないように見えます。</span><span class="sxs-lookup"><span data-stu-id="10d6b-116">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="10d6b-117">プロファイラーは、非同期のリモート処理イベントに対して正確な通知を受信しません。</span><span class="sxs-lookup"><span data-stu-id="10d6b-117">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10d6b-118">要件</span><span class="sxs-lookup"><span data-stu-id="10d6b-118">Requirements</span></span>  

 <span data-ttu-id="10d6b-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10d6b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10d6b-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10d6b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10d6b-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10d6b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10d6b-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10d6b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10d6b-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="10d6b-123">See also</span></span>

- [<span data-ttu-id="10d6b-124">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10d6b-124">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
