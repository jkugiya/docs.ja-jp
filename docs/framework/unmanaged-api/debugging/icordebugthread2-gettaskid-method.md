---
description: '詳細について: ICorDebugThread2:: GetTaskID メソッド'
title: ICorDebugThread2::GetTaskID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: 5429daee9150d63834c747dd5ebb763dd6f0da6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658673"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="5ac85-103">ICorDebugThread2::GetTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="5ac85-103">ICorDebugThread2::GetTaskID Method</span></span>

<span data-ttu-id="5ac85-104">このスレッドで実行されているタスクの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ac85-104">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ac85-105">構文</span><span class="sxs-lookup"><span data-stu-id="5ac85-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ac85-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ac85-106">Parameters</span></span>  

 `pTaskId`  
 <span data-ttu-id="5ac85-107">入出力この ICorDebugThread2 オブジェクトによって表されるスレッド上で実行されているタスクの識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5ac85-107">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ac85-108">解説</span><span class="sxs-lookup"><span data-stu-id="5ac85-108">Remarks</span></span>  

 <span data-ttu-id="5ac85-109">スレッドが接続に関連付けられている場合にのみ、スレッドでタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5ac85-109">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="5ac85-110">`GetTaskID``pTaskId`スレッドが接続に関連付けられていない場合は、で0を返します。</span><span class="sxs-lookup"><span data-stu-id="5ac85-110">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ac85-111">要件</span><span class="sxs-lookup"><span data-stu-id="5ac85-111">Requirements</span></span>  

 <span data-ttu-id="5ac85-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ac85-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ac85-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ac85-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ac85-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ac85-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ac85-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ac85-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
