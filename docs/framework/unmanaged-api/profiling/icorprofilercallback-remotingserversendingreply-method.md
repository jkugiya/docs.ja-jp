---
description: '詳細について: ICorProfilerCallback:: RemotingServerSendingReply メソッド'
title: ICorProfilerCallback::RemotingServerSendingReply メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
ms.openlocfilehash: 236a707fcbc051a3d00c408f71f3b4f9f452c220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788879"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="638f8-103">ICorProfilerCallback::RemotingServerSendingReply メソッド</span><span class="sxs-lookup"><span data-stu-id="638f8-103">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>

<span data-ttu-id="638f8-104">プロセスがリモートメソッド呼び出し要求の処理を完了したこと、およびチャネルを介して応答を送信しようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="638f8-104">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="638f8-105">構文</span><span class="sxs-lookup"><span data-stu-id="638f8-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="638f8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="638f8-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="638f8-107">から次の条件下で [ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) で指定された値に対応する GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="638f8-107">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="638f8-108">リモート処理 GUID クッキーはアクティブです。</span><span class="sxs-lookup"><span data-stu-id="638f8-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="638f8-109">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="638f8-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="638f8-110">GUID cookie は、クライアント側のプロセスでアクティブです。</span><span class="sxs-lookup"><span data-stu-id="638f8-110">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="638f8-111">これにより、リモート処理呼び出しと論理呼び出し履歴の作成を簡単に組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="638f8-111">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="638f8-112">から `true` 呼び出しが非同期の場合は、それ以外の場合はとなる `false` 値。</span><span class="sxs-lookup"><span data-stu-id="638f8-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="638f8-113">要件</span><span class="sxs-lookup"><span data-stu-id="638f8-113">Requirements</span></span>  

 <span data-ttu-id="638f8-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="638f8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="638f8-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="638f8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="638f8-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="638f8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="638f8-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="638f8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638f8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="638f8-118">See also</span></span>

- [<span data-ttu-id="638f8-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="638f8-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
