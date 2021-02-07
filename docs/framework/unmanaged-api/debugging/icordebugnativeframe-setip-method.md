---
description: '詳細については、次のページを参照してください:: テキストボックス'
title: ICorDebugNativeFrame::SetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: cb55b35eb4bd107a7273fd80ba83baac96610fb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729173"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="e668e-103">ICorDebugNativeFrame::SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="e668e-103">ICorDebugNativeFrame::SetIP Method</span></span>

<span data-ttu-id="e668e-104">命令ポインターをネイティブコード内の指定されたオフセット位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="e668e-104">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e668e-105">構文</span><span class="sxs-lookup"><span data-stu-id="e668e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e668e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e668e-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="e668e-107">からネイティブコード内のオフセット位置。</span><span class="sxs-lookup"><span data-stu-id="e668e-107">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e668e-108">解説</span><span class="sxs-lookup"><span data-stu-id="e668e-108">Remarks</span></span>  

 <span data-ttu-id="e668e-109">を呼び出す `SetIP` と、現在のスレッドのすべてのフレームとチェーンがすぐに無効になります。</span><span class="sxs-lookup"><span data-stu-id="e668e-109">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="e668e-110">を呼び出した後にデバッガーがフレーム情報を必要とする場合は `SetIP` 、新しいスタックトレースを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e668e-110">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="e668e-111">[ICorDebug](icordebug-interface.md) は、スタックフレームを有効な状態のままにします。</span><span class="sxs-lookup"><span data-stu-id="e668e-111">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="e668e-112">ただし、フレームが有効な状態の場合でも、ランタイムの場合と同様に、初期化されていないローカル変数などの問題がまだ発生している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e668e-112">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="e668e-113">呼び出し元は、実行中のプログラムの一貫性を保証する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="e668e-113">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="e668e-114">64ビットプラットフォームでは、命令ポインターをまたはブロックの外に移動することはできません `catch` `finally` 。</span><span class="sxs-lookup"><span data-stu-id="e668e-114">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="e668e-115">`SetIP`このような移動を64ビットプラットフォームで実行するためにを呼び出すと、エラーを示す HRESULT が返されます。</span><span class="sxs-lookup"><span data-stu-id="e668e-115">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e668e-116">要件</span><span class="sxs-lookup"><span data-stu-id="e668e-116">Requirements</span></span>  

 <span data-ttu-id="e668e-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e668e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e668e-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e668e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e668e-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e668e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e668e-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e668e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e668e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e668e-121">See also</span></span>
