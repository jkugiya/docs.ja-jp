---
description: '詳細情報: 表示スレッドインターフェイス'
title: ICorDebugThread インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
ms.openlocfilehash: 7e16fa2a82a004a5c85d60a278cdd14df6ab2300
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658829"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="6c3c7-103">ICorDebugThread インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c3c7-103">ICorDebugThread Interface</span></span>

<span data-ttu-id="6c3c7-104">プロセス内のスレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-104">Represents a thread in a process.</span></span> <span data-ttu-id="6c3c7-105">`ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-105">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c3c7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-106">Methods</span></span>  
  
|<span data-ttu-id="6c3c7-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-107">Method</span></span>|<span data-ttu-id="6c3c7-108">説明</span><span class="sxs-lookup"><span data-stu-id="6c3c7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c3c7-109">ClearCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-109">ClearCurrentException Method</span></span>](icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="6c3c7-110">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-110">This method is not implemented.</span></span> <span data-ttu-id="6c3c7-111">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-111">Do not use it.</span></span>|  
|[<span data-ttu-id="6c3c7-112">CreateEval メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-112">CreateEval Method</span></span>](icordebugthread-createeval-method.md)|<span data-ttu-id="6c3c7-113">このを操作する、のオブジェクトを作成し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-113">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="6c3c7-114">CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-114">CreateStepper Method</span></span>](icordebugthread-createstepper-method.md)|<span data-ttu-id="6c3c7-115">こののアクティブなフレームをステップ実行できるようにする ICorDebugStepper オブジェクトを作成し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-115">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="6c3c7-116">EnumerateChains メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-116">EnumerateChains Method</span></span>](icordebugthread-enumeratechains-method.md)|<span data-ttu-id="6c3c7-117">この内のすべてのスタックチェーンを格納している ICorDebugChainEnum 列挙子へのインターフェイスポインターを取得し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-117">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="6c3c7-118">GetActiveChain メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-118">GetActiveChain Method</span></span>](icordebugthread-getactivechain-method.md)|<span data-ttu-id="6c3c7-119">こののアクティブなツールチェーンへのインターフェイスポインターを取得し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-119">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="6c3c7-120">GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-120">GetActiveFrame Method</span></span>](icordebugthread-getactiveframe-method.md)|<span data-ttu-id="6c3c7-121">この上のアクティブなテキストフレームへのインターフェイスポインターを取得し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-121">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="6c3c7-122">GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-122">GetAppDomain Method</span></span>](icordebugthread-getappdomain-method.md)|<span data-ttu-id="6c3c7-123">このが現在実行されているアプリケーションドメインへのインターフェイスポインターを取得し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-123">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="6c3c7-124">GetCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-124">GetCurrentException Method</span></span>](icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="6c3c7-125">現在マネージコードによってスローされている例外を表す、ICorDebugValue オブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-125">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="6c3c7-126">GetDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-126">GetDebugState Method</span></span>](icordebugthread-getdebugstate-method.md)|<span data-ttu-id="6c3c7-127">このの現在のデバッグ状態を示す CorDebugThreadState 値を取得し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-127">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="6c3c7-128">GetHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-128">GetHandle Method</span></span>](icordebugthread-gethandle-method.md)|<span data-ttu-id="6c3c7-129">こののアクティブな部分の現在のハンドルを取得し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-129">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="6c3c7-130">GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-130">GetID Method</span></span>](icordebugthread-getid-method.md)|<span data-ttu-id="6c3c7-131">こののアクティブな部分の現在のオペレーティングシステム識別子を取得し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-131">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="6c3c7-132">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-132">GetObject Method</span></span>](icordebugthread-getobject-method.md)|<span data-ttu-id="6c3c7-133">共通言語ランタイム (CLR) スレッドへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-133">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="6c3c7-134">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-134">GetProcess Method</span></span>](icordebugthread-getprocess-method.md)|<span data-ttu-id="6c3c7-135">このがパートを形成するプロセスへのインターフェイスポインターを取得し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-135">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="6c3c7-136">GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-136">GetRegisterSet Method</span></span>](icordebugthread-getregisterset-method.md)|<span data-ttu-id="6c3c7-137">このに関連付けられているレジスタセットへのインターフェイスポインターを取得し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-137">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="6c3c7-138">GetUserState メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-138">GetUserState Method</span></span>](icordebugthread-getuserstate-method.md)|<span data-ttu-id="6c3c7-139">このの現在の状態を示す CorDebugUserState 値のビットごとの組み合わせを取得し `ICorDebugThread` ます。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-139">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="6c3c7-140">SetDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="6c3c7-140">SetDebugState Method</span></span>](icordebugthread-setdebugstate-method.md)|<span data-ttu-id="6c3c7-141">こののデバッグ状態を記述する値のビットごとの組み合わせを設定 `CorDebugThreadState` `ICorDebugThread` します。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-141">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c3c7-142">解説</span><span class="sxs-lookup"><span data-stu-id="6c3c7-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c3c7-143">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c3c7-144">要件</span><span class="sxs-lookup"><span data-stu-id="6c3c7-144">Requirements</span></span>  

 <span data-ttu-id="6c3c7-145">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c3c7-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c3c7-146">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c3c7-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c3c7-147">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c3c7-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c3c7-148">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c3c7-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c3c7-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c3c7-149">See also</span></span>

- [<span data-ttu-id="6c3c7-150">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c3c7-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
