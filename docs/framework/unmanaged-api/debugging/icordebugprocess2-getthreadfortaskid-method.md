---
description: '詳細について: ICorDebugProcess2:: GetThreadForTaskID メソッド'
title: ICorDebugProcess2::GetThreadForTaskID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
ms.openlocfilehash: aafb1223f6e2e73aae600fd482c76b84c57dae52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650132"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="d8848-103">ICorDebugProcess2::GetThreadForTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="d8848-103">ICorDebugProcess2::GetThreadForTaskID Method</span></span>

<span data-ttu-id="d8848-104">指定した id を持つタスクが実行されているスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="d8848-104">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8848-105">構文</span><span class="sxs-lookup"><span data-stu-id="d8848-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8848-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d8848-106">Parameters</span></span>  

 `taskid`  
 <span data-ttu-id="d8848-107">からタスクの識別子です。</span><span class="sxs-lookup"><span data-stu-id="d8848-107">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="d8848-108">入出力取得するスレッドを表す ICorDebugThread2 オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d8848-108">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8848-109">解説</span><span class="sxs-lookup"><span data-stu-id="d8848-109">Remarks</span></span>  

 <span data-ttu-id="d8848-110">ホストは、 [ICLRTask:: SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) メソッドを使用してタスク識別子を設定できます。</span><span class="sxs-lookup"><span data-stu-id="d8848-110">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8848-111">要件</span><span class="sxs-lookup"><span data-stu-id="d8848-111">Requirements</span></span>  

 <span data-ttu-id="d8848-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8848-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8848-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8848-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8848-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8848-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8848-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8848-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
