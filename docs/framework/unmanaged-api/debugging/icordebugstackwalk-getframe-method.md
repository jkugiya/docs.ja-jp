---
description: 詳細については、次を参照
title: ICorDebugStackWalk::GetFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: b00ddb6a475aff4263a922f5a20b866cd0e1b2ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794742"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="83c24-103">ICorDebugStackWalk::GetFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="83c24-103">ICorDebugStackWalk::GetFrame Method</span></span>

<span data-ttu-id="83c24-104">テキスト [オブジェクトの現在のフレーム](icordebugstackwalk-interface.md) を取得します。</span><span class="sxs-lookup"><span data-stu-id="83c24-104">Gets the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83c24-105">構文</span><span class="sxs-lookup"><span data-stu-id="83c24-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83c24-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83c24-106">Parameters</span></span>  

 `pFrame`  
 <span data-ttu-id="83c24-107">からスタック内の現在のフレームを表す、作成されたフレームオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="83c24-107">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83c24-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="83c24-108">Return Value</span></span>  

 <span data-ttu-id="83c24-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="83c24-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="83c24-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83c24-110">HRESULT</span></span>|<span data-ttu-id="83c24-111">説明</span><span class="sxs-lookup"><span data-stu-id="83c24-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83c24-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="83c24-112">S_OK</span></span>|<span data-ttu-id="83c24-113">ランタイムは、現在のフレームを正常に返しました。</span><span class="sxs-lookup"><span data-stu-id="83c24-113">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="83c24-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83c24-114">E_FAIL</span></span>|<span data-ttu-id="83c24-115">現在のフレームは返されませんでした。</span><span class="sxs-lookup"><span data-stu-id="83c24-115">The current frame was not returned.</span></span>|  
|<span data-ttu-id="83c24-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="83c24-116">S_FALSE</span></span>|<span data-ttu-id="83c24-117">現在のフレームはネイティブスタックフレームです。</span><span class="sxs-lookup"><span data-stu-id="83c24-117">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="83c24-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="83c24-118">E_INVALIDARG</span></span>|<span data-ttu-id="83c24-119">`pFrame` が null です。</span><span class="sxs-lookup"><span data-stu-id="83c24-119">`pFrame` is null.</span></span>|  
|<span data-ttu-id="83c24-120">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="83c24-120">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="83c24-121">フレームポインターは既にスタックの末尾にあります。そのため、追加のフレームにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="83c24-121">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="83c24-122">例外</span><span class="sxs-lookup"><span data-stu-id="83c24-122">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83c24-123">解説</span><span class="sxs-lookup"><span data-stu-id="83c24-123">Remarks</span></span>  

 <span data-ttu-id="83c24-124">`ICorDebugStackWalk` 実際のスタックフレームだけを返します。</span><span class="sxs-lookup"><span data-stu-id="83c24-124">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="83c24-125">内部フレームを返すには、 [ICorDebugThread3:: GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="83c24-125">Use the [ICorDebugThread3::GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="83c24-126">内部フレームは、一時データを格納するためにランタイムによってスタックにプッシュされるデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="83c24-126">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83c24-127">要件</span><span class="sxs-lookup"><span data-stu-id="83c24-127">Requirements</span></span>  

 <span data-ttu-id="83c24-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83c24-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83c24-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83c24-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83c24-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83c24-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83c24-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83c24-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c24-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="83c24-132">See also</span></span>

- [<span data-ttu-id="83c24-133">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83c24-133">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="83c24-134">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="83c24-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="83c24-135">デバッグ</span><span class="sxs-lookup"><span data-stu-id="83c24-135">Debugging</span></span>](index.md)
