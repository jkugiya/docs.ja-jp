---
description: 詳細については、「ICorDebugThread2 インターフェイス」を参照してください。
title: ICorDebugThread2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: 81f687f6daff9ffa7298ec6d818a214b8934bcc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658504"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="a7cce-103">ICorDebugThread2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a7cce-103">ICorDebugThread2 Interface</span></span>

<span data-ttu-id="a7cce-104">は、"、" スレッドインターフェイスの論理的な拡張として機能します。</span><span class="sxs-lookup"><span data-stu-id="a7cce-104">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7cce-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a7cce-105">Methods</span></span>  
  
|<span data-ttu-id="a7cce-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a7cce-106">Method</span></span>|<span data-ttu-id="a7cce-107">説明</span><span class="sxs-lookup"><span data-stu-id="a7cce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7cce-108">GetActiveFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="a7cce-108">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="a7cce-109">スレッドのフレーム内のアクティブな関数に関するデータを格納している COR_ACTIVE_FUNCTION インスタンスの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="a7cce-109">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="a7cce-110">GetConnectionID メソッド</span><span class="sxs-lookup"><span data-stu-id="a7cce-110">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="a7cce-111">このの接続識別子を取得し `ICorDebugThread2` ます。</span><span class="sxs-lookup"><span data-stu-id="a7cce-111">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="a7cce-112">GetTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="a7cce-112">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="a7cce-113">こののタスク識別子を取得し `ICorDebugThread2` ます。</span><span class="sxs-lookup"><span data-stu-id="a7cce-113">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="a7cce-114">GetVolatileOSThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="a7cce-114">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="a7cce-115">こののオペレーティングシステムスレッド識別子を取得し `ICorDebugThread2` ます。</span><span class="sxs-lookup"><span data-stu-id="a7cce-115">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="a7cce-116">InterceptCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="a7cce-116">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="a7cce-117">デバッガーがスレッドの現在の例外をインターセプトできるようにします。</span><span class="sxs-lookup"><span data-stu-id="a7cce-117">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7cce-118">解説</span><span class="sxs-lookup"><span data-stu-id="a7cce-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7cce-119">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a7cce-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7cce-120">要件</span><span class="sxs-lookup"><span data-stu-id="a7cce-120">Requirements</span></span>  

 <span data-ttu-id="a7cce-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7cce-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7cce-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7cce-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7cce-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7cce-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7cce-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7cce-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7cce-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7cce-125">See also</span></span>

- [<span data-ttu-id="a7cce-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a7cce-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
