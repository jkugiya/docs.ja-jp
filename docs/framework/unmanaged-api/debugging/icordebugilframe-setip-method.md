---
description: 詳細については、次のページを参照してください
title: ICorDebugILFrame::SetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 75d2530a3d9151c64980316757074141776a78d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791323"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="01fa1-103">ICorDebugILFrame::SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="01fa1-103">ICorDebugILFrame::SetIP Method</span></span>

<span data-ttu-id="01fa1-104">命令ポインターを Microsoft 中間言語 (MSIL) コード内の指定されたオフセット位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="01fa1-104">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01fa1-105">構文</span><span class="sxs-lookup"><span data-stu-id="01fa1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01fa1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01fa1-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="01fa1-107">MSIL コード内のオフセット位置。</span><span class="sxs-lookup"><span data-stu-id="01fa1-107">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01fa1-108">解説</span><span class="sxs-lookup"><span data-stu-id="01fa1-108">Remarks</span></span>  

 <span data-ttu-id="01fa1-109">を呼び出す `SetIP` と、現在のスレッドのすべてのフレームとチェーンがすぐに無効になります。</span><span class="sxs-lookup"><span data-stu-id="01fa1-109">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="01fa1-110">を呼び出した後にデバッガーがフレーム情報を必要とする場合は `SetIP` 、新しいスタックトレースを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01fa1-110">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="01fa1-111">[ICorDebug](icordebug-interface.md) は、スタックフレームを有効な状態のままにします。</span><span class="sxs-lookup"><span data-stu-id="01fa1-111">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="01fa1-112">ただし、フレームが有効な状態であっても、初期化されていないローカル変数などの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="01fa1-112">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="01fa1-113">呼び出し元は、実行中のプログラムの一貫性を確保する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="01fa1-113">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="01fa1-114">64ビットプラットフォームでは、命令ポインターをまたはブロックの外に移動することはできません `catch` `finally` 。</span><span class="sxs-lookup"><span data-stu-id="01fa1-114">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="01fa1-115">`SetIP`このような移動を64ビットプラットフォームで実行するためにを呼び出すと、エラーを示す HRESULT が返されます。</span><span class="sxs-lookup"><span data-stu-id="01fa1-115">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01fa1-116">要件</span><span class="sxs-lookup"><span data-stu-id="01fa1-116">Requirements</span></span>  

 <span data-ttu-id="01fa1-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01fa1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01fa1-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01fa1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01fa1-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01fa1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01fa1-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01fa1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
