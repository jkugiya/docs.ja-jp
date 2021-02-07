---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugController インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: 588c41b5b8d87589facd6085655ed0ad415ec3aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710752"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="d1c33-103">ICorDebugController インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1c33-103">ICorDebugController Interface</span></span>

<span data-ttu-id="d1c33-104">コードの実行コンテキストを制御できる <xref:System.Diagnostics.Process> または <xref:System.AppDomain> のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="d1c33-104">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1c33-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d1c33-105">Methods</span></span>  
  
|<span data-ttu-id="d1c33-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d1c33-106">Method</span></span>|<span data-ttu-id="d1c33-107">説明</span><span class="sxs-lookup"><span data-stu-id="d1c33-107">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="d1c33-108">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="d1c33-108">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="d1c33-109">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="d1c33-109">This method is obsolete.</span></span>|  
|[<span data-ttu-id="d1c33-110">Continue メソッド</span><span class="sxs-lookup"><span data-stu-id="d1c33-110">Continue Method</span></span>](icordebugcontroller-continue-method.md)|<span data-ttu-id="d1c33-111">次のように、 [コントロール](icordebugcontroller-stop-method.md)スレッドの実行を再開します。</span><span class="sxs-lookup"><span data-stu-id="d1c33-111">Resumes execution of managed threads after a call to [ICorDebugController::Stop](icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="d1c33-112">Detach メソッド</span><span class="sxs-lookup"><span data-stu-id="d1c33-112">Detach Method</span></span>](icordebugcontroller-detach-method.md)|<span data-ttu-id="d1c33-113">プロセスまたはアプリケーションドメインからデバッガーをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="d1c33-113">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="d1c33-114">EnumerateThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d1c33-114">EnumerateThreads Method</span></span>](icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="d1c33-115">プロセス内のアクティブなマネージスレッドの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d1c33-115">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="d1c33-116">HasQueuedCallbacks メソッド</span><span class="sxs-lookup"><span data-stu-id="d1c33-116">HasQueuedCallbacks Method</span></span>](icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="d1c33-117">マネージコールバックが、指定されたスレッドに対して現在キューに登録されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d1c33-117">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="d1c33-118">IsRunning メソッド</span><span class="sxs-lookup"><span data-stu-id="d1c33-118">IsRunning Method</span></span>](icordebugcontroller-isrunning-method.md)|<span data-ttu-id="d1c33-119">プロセス内のスレッドが現在実行中であるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d1c33-119">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="d1c33-120">SetAllThreadsDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="d1c33-120">SetAllThreadsDebugState Method</span></span>](icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="d1c33-121">プロセス内のすべてのマネージスレッドのデバッグ状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="d1c33-121">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="d1c33-122">Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="d1c33-122">Stop Method</span></span>](icordebugcontroller-stop-method.md)|<span data-ttu-id="d1c33-123">プロセスでマネージコードを実行しているすべてのスレッドで協調停止を実行します。</span><span class="sxs-lookup"><span data-stu-id="d1c33-123">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="d1c33-124">Terminate メソッド</span><span class="sxs-lookup"><span data-stu-id="d1c33-124">Terminate Method</span></span>](icordebugcontroller-terminate-method.md)|<span data-ttu-id="d1c33-125">指定された終了コードを使用してプロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="d1c33-125">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1c33-126">解説</span><span class="sxs-lookup"><span data-stu-id="d1c33-126">Remarks</span></span>  

 <span data-ttu-id="d1c33-127">がプロセスを制御している場合、 `ICorDebugController` スコープにはプロセスのすべてのスレッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1c33-127">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="d1c33-128">`ICorDebugController`がアプリケーションドメインを制御している場合、スコープにはその特定のアプリケーションドメインのスレッドだけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1c33-128">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1c33-129">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d1c33-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c33-130">要件</span><span class="sxs-lookup"><span data-stu-id="d1c33-130">Requirements</span></span>  

 <span data-ttu-id="d1c33-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1c33-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1c33-132">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1c33-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1c33-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1c33-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1c33-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1c33-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c33-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1c33-135">See also</span></span>

- [<span data-ttu-id="d1c33-136">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1c33-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
