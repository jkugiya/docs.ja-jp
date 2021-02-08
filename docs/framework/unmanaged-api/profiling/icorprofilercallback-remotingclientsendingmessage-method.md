---
description: '詳細について: ICorProfilerCallback:: RemotingClientSendingMessage メソッド'
title: ICorProfilerCallback::RemotingClientSendingMessage メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
ms.openlocfilehash: 3d075b3f3c3ffe63c9d4401bdc182037593b5b19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788931"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="58b5d-103">ICorProfilerCallback::RemotingClientSendingMessage メソッド</span><span class="sxs-lookup"><span data-stu-id="58b5d-103">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>

<span data-ttu-id="58b5d-104">クライアントがサーバーに要求を送信していることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="58b5d-104">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58b5d-105">構文</span><span class="sxs-lookup"><span data-stu-id="58b5d-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58b5d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="58b5d-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="58b5d-107">から次の条件下で [ICorProfilerCallback:: RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) で指定された値に対応する値。</span><span class="sxs-lookup"><span data-stu-id="58b5d-107">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="58b5d-108">リモート処理 GUID クッキーはアクティブです。</span><span class="sxs-lookup"><span data-stu-id="58b5d-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="58b5d-109">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="58b5d-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="58b5d-110">GUID クッキーはサーバー側のプロセスでアクティブです。</span><span class="sxs-lookup"><span data-stu-id="58b5d-110">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="58b5d-111">これにより、リモート処理呼び出しと論理呼び出し履歴の作成を簡単に組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="58b5d-111">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="58b5d-112">から `true` 呼び出しが非同期の場合は、それ以外の場合はとなる `false` 値。</span><span class="sxs-lookup"><span data-stu-id="58b5d-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58b5d-113">要件</span><span class="sxs-lookup"><span data-stu-id="58b5d-113">Requirements</span></span>  

 <span data-ttu-id="58b5d-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58b5d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58b5d-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58b5d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58b5d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58b5d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58b5d-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58b5d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b5d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="58b5d-118">See also</span></span>

- [<span data-ttu-id="58b5d-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58b5d-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
