---
description: 詳細については、「ICorDebugStepper インターフェイス」を参照してください。
title: ICorDebugStepper インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
ms.openlocfilehash: a16df9d25b4d87b0638448c1fdf8fec4759261d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803586"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="ca6a6-103">ICorDebugStepper インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca6a6-103">ICorDebugStepper Interface</span></span>

<span data-ttu-id="ca6a6-104">デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-104">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca6a6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ca6a6-105">Methods</span></span>  
  
|<span data-ttu-id="ca6a6-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ca6a6-106">Method</span></span>|<span data-ttu-id="ca6a6-107">説明</span><span class="sxs-lookup"><span data-stu-id="ca6a6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca6a6-108">Deactivate メソッド</span><span class="sxs-lookup"><span data-stu-id="ca6a6-108">Deactivate Method</span></span>](icordebugstepper-deactivate-method.md)|<span data-ttu-id="ca6a6-109">これにより、 `ICorDebugStepper` 受信した最後のステップコマンドがキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-109">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="ca6a6-110">IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="ca6a6-110">IsActive Method</span></span>](icordebugstepper-isactive-method.md)|<span data-ttu-id="ca6a6-111">この `ICorDebugStepper` が現在ステップを実行しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-111">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="ca6a6-112">SetInterceptMask メソッド</span><span class="sxs-lookup"><span data-stu-id="ca6a6-112">SetInterceptMask Method</span></span>](icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="ca6a6-113">ステップインするコードの種類を指定する CorDebugIntercept 値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-113">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="ca6a6-114">SetRangeIL メソッド</span><span class="sxs-lookup"><span data-stu-id="ca6a6-114">SetRangeIL Method</span></span>](icordebugstepper-setrangeil-method.md)|<span data-ttu-id="ca6a6-115">[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md)を呼び出すかどうかを示す値を設定します。これは、ネイティブコードまたはステップスルー中のメソッドの Microsoft 中間言語 (MSIL) コードを基準として、引数の値を渡します。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-115">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="ca6a6-116">SetUnmappedStopMask メソッド</span><span class="sxs-lookup"><span data-stu-id="ca6a6-116">SetUnmappedStopMask Method</span></span>](icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="ca6a6-117">実行が停止するマップされていないコードの種類を指定する CorDebugUnmappedStop 値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-117">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="ca6a6-118">Step メソッド</span><span class="sxs-lookup"><span data-stu-id="ca6a6-118">Step Method</span></span>](icordebugstepper-step-method.md)|<span data-ttu-id="ca6a6-119">これにより、このが格納している `ICorDebugStepper` スレッドを1ステップずつ実行します。また、必要に応じて、スレッド内で呼び出される関数を使用したシングルステップ実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-119">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="ca6a6-120">StepOut メソッド</span><span class="sxs-lookup"><span data-stu-id="ca6a6-120">StepOut Method</span></span>](icordebugstepper-stepout-method.md)|<span data-ttu-id="ca6a6-121">これにより、この `ICorDebugStepper` が格納しているスレッドを1ステップずつ実行し、現在のフレームが呼び出し元のフレームに制御を返すときに完了します。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-121">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="ca6a6-122">StepRange メソッド</span><span class="sxs-lookup"><span data-stu-id="ca6a6-122">StepRange Method</span></span>](icordebugstepper-steprange-method.md)|<span data-ttu-id="ca6a6-123">これにより、このが `ICorDebugStepper` 格納しているスレッドを1ステップずつ実行し、指定した範囲の最後のコードに到達したときにを返します。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-123">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca6a6-124">解説</span><span class="sxs-lookup"><span data-stu-id="ca6a6-124">Remarks</span></span>  

 <span data-ttu-id="ca6a6-125">この `ICorDebugStepper` インターフェイスは、次の目的で機能します。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-125">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="ca6a6-126">発行されたステップコマンドとそのコマンドの完了の間の識別子として機能します。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-126">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="ca6a6-127">これは、実行可能なすべてのステップをカプセル化するための中心的なインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-127">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="ca6a6-128">これにより、ステップ実行操作を途中で取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-128">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="ca6a6-129">スレッドごとに複数のステッパが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-129">There can be more than one stepper per thread.</span></span> <span data-ttu-id="ca6a6-130">たとえば、関数をステップオーバーしている間にブレークポイントがヒットし、ユーザーがその関数内で新しいステップ実行操作を開始する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-130">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="ca6a6-131">この状況をどのように処理するかは、デバッガーによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-131">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="ca6a6-132">デバッガーでは、元のステップ実行操作をキャンセルするか、2つの操作を入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-132">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="ca6a6-133">インターフェイスでは、 `ICorDebugStepper` 両方の選択肢がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-133">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="ca6a6-134">共通言語ランタイム (CLR) がクロススレッドでマーシャリングされた呼び出しを行う場合、ステッパはスレッド間で移行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-134">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca6a6-135">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca6a6-136">要件</span><span class="sxs-lookup"><span data-stu-id="ca6a6-136">Requirements</span></span>  

 <span data-ttu-id="ca6a6-137">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca6a6-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca6a6-138">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca6a6-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca6a6-139">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca6a6-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca6a6-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca6a6-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca6a6-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca6a6-141">See also</span></span>

- [<span data-ttu-id="ca6a6-142">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca6a6-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
