---
description: '詳細については、次のメソッドを参照してください。: いいね。'
title: ICorDebugStackWalk::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: 27a48ca40f6b43cae32511b71b73e68d88eb60c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717759"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="698d9-103">ICorDebugStackWalk::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="698d9-103">ICorDebugStackWalk::Next Method</span></span>

<span data-ttu-id="698d9-104">このオブジェクトを次のフレームに [移動します](icordebugstackwalk-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="698d9-104">Moves the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="698d9-105">構文</span><span class="sxs-lookup"><span data-stu-id="698d9-105">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="698d9-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="698d9-106">Return Value</span></span>  

 <span data-ttu-id="698d9-107">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="698d9-107">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="698d9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="698d9-108">HRESULT</span></span>|<span data-ttu-id="698d9-109">説明</span><span class="sxs-lookup"><span data-stu-id="698d9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="698d9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="698d9-110">S_OK</span></span>|<span data-ttu-id="698d9-111">ランタイムが次のフレームに正常にアンワインドされました (「解説」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="698d9-111">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="698d9-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="698d9-112">E_FAIL</span></span>|<span data-ttu-id="698d9-113">`ICorDebugStackWalk`オブジェクトを拡張できませんでした。</span><span class="sxs-lookup"><span data-stu-id="698d9-113">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="698d9-114">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="698d9-114">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="698d9-115">このアンワインドの結果、スタックの末尾に到達しました。</span><span class="sxs-lookup"><span data-stu-id="698d9-115">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="698d9-116">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="698d9-116">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="698d9-117">フレームポインターは既にスタックの末尾にあります。そのため、追加のフレームにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="698d9-117">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="698d9-118">例外</span><span class="sxs-lookup"><span data-stu-id="698d9-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="698d9-119">解説</span><span class="sxs-lookup"><span data-stu-id="698d9-119">Remarks</span></span>  

 <span data-ttu-id="698d9-120">メソッドは、 `Next` `ICorDebugStackWalk` ランタイムが現在のフレームをアンワインドできる場合にのみ、オブジェクトを呼び出し元のフレームに進めます。</span><span class="sxs-lookup"><span data-stu-id="698d9-120">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="698d9-121">それ以外の場合、オブジェクトは、ランタイムがアンワインドできる次のフレームに進みます。</span><span class="sxs-lookup"><span data-stu-id="698d9-121">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="698d9-122">要件</span><span class="sxs-lookup"><span data-stu-id="698d9-122">Requirements</span></span>  

 <span data-ttu-id="698d9-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="698d9-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="698d9-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="698d9-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="698d9-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="698d9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="698d9-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="698d9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="698d9-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="698d9-127">See also</span></span>

- [<span data-ttu-id="698d9-128">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="698d9-128">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="698d9-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="698d9-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="698d9-130">デバッグ</span><span class="sxs-lookup"><span data-stu-id="698d9-130">Debugging</span></span>](index.md)
