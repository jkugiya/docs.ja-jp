---
description: '詳細については、次を参照してください: SetContext メソッド'
title: ICorDebugStackWalk::SetContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 20e18460d237a63e4c2695b9e7cbfa766ed3908f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794716"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="be027-103">ICorDebugStackWalk::SetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="be027-103">ICorDebugStackWalk::SetContext Method</span></span>

<span data-ttu-id="be027-104">[オブジェクトの現在のコンテキスト](icordebugstackwalk-interface.md)をスレッドの有効なコンテキストに設定します。</span><span class="sxs-lookup"><span data-stu-id="be027-104">Sets the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be027-105">構文</span><span class="sxs-lookup"><span data-stu-id="be027-105">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be027-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be027-106">Parameters</span></span>  

 `flag`  
 <span data-ttu-id="be027-107">からコンテキストがスタックのアクティブなフレームからのものであるか、またはスタックのアンワインドによって取得されたコンテキストであるかを示す [Cordebugsetcontextflag](cordebugsetcontextflag-enumeration.md) フラグ。</span><span class="sxs-lookup"><span data-stu-id="be027-107">[in] A [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="be027-108">からバッファーに割り当てられたサイズ `CONTEXT` 。</span><span class="sxs-lookup"><span data-stu-id="be027-108">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="be027-109">から `CONTEXT` バッファー。</span><span class="sxs-lookup"><span data-stu-id="be027-109">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be027-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="be027-110">Return Value</span></span>  

 <span data-ttu-id="be027-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="be027-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="be027-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be027-112">HRESULT</span></span>|<span data-ttu-id="be027-113">説明</span><span class="sxs-lookup"><span data-stu-id="be027-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be027-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="be027-114">S_OK</span></span>|<span data-ttu-id="be027-115">`ICorDebugStackWalk`オブジェクトのコンテキストが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="be027-115">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="be027-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="be027-116">E_FAIL</span></span>|<span data-ttu-id="be027-117">`ICorDebugStackWalk`オブジェクトのコンテキストが設定されていません。</span><span class="sxs-lookup"><span data-stu-id="be027-117">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="be027-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="be027-118">E_INVALIDARG</span></span>|<span data-ttu-id="be027-119">コンテキストが null です。</span><span class="sxs-lookup"><span data-stu-id="be027-119">The context is null.</span></span>|  
|<span data-ttu-id="be027-120">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="be027-120">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="be027-121">コンテキストバッファーが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="be027-121">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="be027-122">例外</span><span class="sxs-lookup"><span data-stu-id="be027-122">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be027-123">解説</span><span class="sxs-lookup"><span data-stu-id="be027-123">Remarks</span></span>  

 <span data-ttu-id="be027-124">このメソッドは、スレッドの現在のコンテキストを変更しません。</span><span class="sxs-lookup"><span data-stu-id="be027-124">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="be027-125">現在のコンテキストを無効なコンテキストに設定すると、スタックウォーカーから予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="be027-125">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="be027-126">このコンテキストの完全なビットごとのコピーを取得するには、次のようにして、" [GetContext](icordebugstackwalk-getcontext-method.md) " メソッドを直ちに呼び出します。</span><span class="sxs-lookup"><span data-stu-id="be027-126">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be027-127">要件</span><span class="sxs-lookup"><span data-stu-id="be027-127">Requirements</span></span>  

 <span data-ttu-id="be027-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be027-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be027-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be027-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be027-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be027-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be027-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be027-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be027-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="be027-132">See also</span></span>

- [<span data-ttu-id="be027-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="be027-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="be027-134">デバッグ</span><span class="sxs-lookup"><span data-stu-id="be027-134">Debugging</span></span>](index.md)
