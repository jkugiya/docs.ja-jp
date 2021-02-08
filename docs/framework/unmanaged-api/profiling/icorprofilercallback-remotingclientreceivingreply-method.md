---
description: '詳細について: ICorProfilerCallback:: RemotingClientReceivingReply メソッド'
title: ICorProfilerCallback::RemotingClientReceivingReply メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: 4c1d42baa9f4381b66c9be75afa239899ae81b81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788944"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="9a137-103">ICorProfilerCallback::RemotingClientReceivingReply メソッド</span><span class="sxs-lookup"><span data-stu-id="9a137-103">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>

<span data-ttu-id="9a137-104">リモート処理呼び出しのサーバー側の部分が完了し、クライアントが応答を受信および処理するようになったことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9a137-104">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a137-105">構文</span><span class="sxs-lookup"><span data-stu-id="9a137-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="9a137-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a137-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="9a137-107">から次の条件下で [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) で指定された値に対応する値。</span><span class="sxs-lookup"><span data-stu-id="9a137-107">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="9a137-108">リモート処理 GUID クッキーはアクティブです。</span><span class="sxs-lookup"><span data-stu-id="9a137-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="9a137-109">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="9a137-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="9a137-110">GUID クッキーはサーバー側のプロセスでアクティブです。</span><span class="sxs-lookup"><span data-stu-id="9a137-110">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="9a137-111">これにより、リモート処理呼び出しを簡単に組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="9a137-111">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="9a137-112">から `true` 呼び出しが非同期の場合は、それ以外の場合はとなる `false` 値。</span><span class="sxs-lookup"><span data-stu-id="9a137-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a137-113">要件</span><span class="sxs-lookup"><span data-stu-id="9a137-113">Requirements</span></span>  

 <span data-ttu-id="9a137-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a137-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a137-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a137-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a137-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a137-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a137-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a137-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a137-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a137-118">See also</span></span>

- [<span data-ttu-id="9a137-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a137-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
