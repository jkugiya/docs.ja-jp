---
description: 詳細については、「ICorDebugManagedCallback2 インターフェイス」を参照してください。
title: ICorDebugManagedCallback2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
ms.openlocfilehash: a6a5b05479ea0f9e2d86f7c0ce42f5edd35bcb7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691758"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="5abe5-103">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5abe5-103">ICorDebugManagedCallback2 Interface</span></span>

<span data-ttu-id="5abe5-104">デバッガーの例外処理およびマネージド デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5abe5-104">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="5abe5-105">`ICorDebugManagedCallback2` は [、のように、の](icordebugmanagedcallback-interface.md) 論理上の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="5abe5-105">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5abe5-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5abe5-106">Methods</span></span>  
  
|<span data-ttu-id="5abe5-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="5abe5-107">Method</span></span>|<span data-ttu-id="5abe5-108">説明</span><span class="sxs-lookup"><span data-stu-id="5abe5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5abe5-109">ChangeConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="5abe5-109">ChangeConnection Method</span></span>](icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="5abe5-110">指定した接続に関連付けられたタスクのセットが変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5abe5-110">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="5abe5-111">CreateConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="5abe5-111">CreateConnection Method</span></span>](icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="5abe5-112">新しい接続が作成されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5abe5-112">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="5abe5-113">DestroyConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="5abe5-113">DestroyConnection Method</span></span>](icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="5abe5-114">指定された接続が終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5abe5-114">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="5abe5-115">Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="5abe5-115">Exception Method</span></span>](icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="5abe5-116">例外ハンドラーの検索が開始されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5abe5-116">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="5abe5-117">ExceptionUnwind メソッド</span><span class="sxs-lookup"><span data-stu-id="5abe5-117">ExceptionUnwind Method</span></span>](icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="5abe5-118">例外アンワインド処理中の状態通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="5abe5-118">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="5abe5-119">FunctionRemapComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="5abe5-119">FunctionRemapComplete Method</span></span>](icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="5abe5-120">コードの実行が編集された関数の新しいバージョンに切り替わったことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5abe5-120">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="5abe5-121">FunctionRemapOpportunity メソッド</span><span class="sxs-lookup"><span data-stu-id="5abe5-121">FunctionRemapOpportunity Method</span></span>](icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="5abe5-122">コードの実行が、編集された関数の古いバージョンのシーケンスポイントに達したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5abe5-122">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="5abe5-123">MDANotification メソッド</span><span class="sxs-lookup"><span data-stu-id="5abe5-123">MDANotification Method</span></span>](icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="5abe5-124">コード実行でマネージデバッグアシスタント (MDA) メッセージが検出されたことを通知します。</span><span class="sxs-lookup"><span data-stu-id="5abe5-124">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5abe5-125">解説</span><span class="sxs-lookup"><span data-stu-id="5abe5-125">Remarks</span></span>  

 <span data-ttu-id="5abe5-126">インターフェイスは、インターフェイスを拡張して、 `ICorDebugManagedCallback2` `ICorDebugManagedCallback` .NET Framework バージョン2.0 で導入された新しいデバッグイベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="5abe5-126">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="5abe5-127">デバッガー `ICorDebugManagedCallback2` が .NET Framework 2.0 アプリケーションをデバッグしている場合は、を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5abe5-127">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="5abe5-128">またはのインスタンスは、 `ICorDebugManagedCallback` `ICorDebugManagedCallback2` コールバックオブジェクトとして [ICorDebug:: setmanagedhandler](icordebug-setmanagedhandler-method.md)に渡されます。</span><span class="sxs-lookup"><span data-stu-id="5abe5-128">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5abe5-129">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5abe5-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5abe5-130">要件</span><span class="sxs-lookup"><span data-stu-id="5abe5-130">Requirements</span></span>  

 <span data-ttu-id="5abe5-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5abe5-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5abe5-132">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5abe5-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5abe5-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5abe5-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5abe5-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5abe5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5abe5-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="5abe5-135">See also</span></span>

- [<span data-ttu-id="5abe5-136">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="5abe5-136">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5abe5-137">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5abe5-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5abe5-138">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5abe5-138">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
