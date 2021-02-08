---
description: '詳細について: ICorProfilerCallback:: RemotingServerReceivingMessage メソッド'
title: ICorProfilerCallback::RemotingServerReceivingMessage メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 5efa706d934158d09796dfab40b132a334c10ffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788892"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="0451b-103">ICorProfilerCallback::RemotingServerReceivingMessage メソッド</span><span class="sxs-lookup"><span data-stu-id="0451b-103">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>

<span data-ttu-id="0451b-104">プロセスがリモートメソッド呼び出しまたはアクティベーション要求を受信したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0451b-104">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0451b-105">構文</span><span class="sxs-lookup"><span data-stu-id="0451b-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0451b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0451b-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="0451b-107">から次の条件下で [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) で指定された値に対応する値。</span><span class="sxs-lookup"><span data-stu-id="0451b-107">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="0451b-108">リモート処理 GUID クッキーはアクティブです。</span><span class="sxs-lookup"><span data-stu-id="0451b-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="0451b-109">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="0451b-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="0451b-110">GUID cookie は、クライアント側のプロセスでアクティブです。</span><span class="sxs-lookup"><span data-stu-id="0451b-110">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="0451b-111">これにより、リモート処理呼び出しと論理呼び出し履歴の作成を簡単に組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="0451b-111">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="0451b-112">から `true` 呼び出しが非同期の場合は、それ以外の場合はとなる `false` 値。</span><span class="sxs-lookup"><span data-stu-id="0451b-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0451b-113">解説</span><span class="sxs-lookup"><span data-stu-id="0451b-113">Remarks</span></span>  

 <span data-ttu-id="0451b-114">メッセージ要求が非同期の場合は、任意のスレッドで要求を処理できます。</span><span class="sxs-lookup"><span data-stu-id="0451b-114">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0451b-115">要件</span><span class="sxs-lookup"><span data-stu-id="0451b-115">Requirements</span></span>  

 <span data-ttu-id="0451b-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0451b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0451b-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0451b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0451b-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0451b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0451b-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0451b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0451b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0451b-120">See also</span></span>

- [<span data-ttu-id="0451b-121">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0451b-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
