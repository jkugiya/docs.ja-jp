---
description: '詳細については、次を参照してください: GetContext メソッド'
title: ICorDebugStackWalk::GetContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 30beefaa1e0e2e4c5043cae7213658ac24e8a1b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649612"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="59e7b-103">ICorDebugStackWalk::GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="59e7b-103">ICorDebugStackWalk::GetContext Method</span></span>

<span data-ttu-id="59e7b-104">[は、テキストオブジェクト内](icordebugstackwalk-interface.md)の現在のフレームのコンテキストを返します。</span><span class="sxs-lookup"><span data-stu-id="59e7b-104">Returns the context for the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59e7b-105">構文</span><span class="sxs-lookup"><span data-stu-id="59e7b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59e7b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="59e7b-106">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="59e7b-107">からコンテキストバッファーの要求されたコンテンツを示すフラグ (Winnt.h で定義されています)。</span><span class="sxs-lookup"><span data-stu-id="59e7b-107">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="59e7b-108">からコンテキストバッファーに割り当てられたサイズ。</span><span class="sxs-lookup"><span data-stu-id="59e7b-108">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="59e7b-109">入出力コンテキストの実際のサイズ。</span><span class="sxs-lookup"><span data-stu-id="59e7b-109">[out] The actual size of the context.</span></span> <span data-ttu-id="59e7b-110">この値は、コンテキストバッファーのサイズ以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="59e7b-110">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="59e7b-111">入出力コンテキストバッファー。</span><span class="sxs-lookup"><span data-stu-id="59e7b-111">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59e7b-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="59e7b-112">Return Value</span></span>  

 <span data-ttu-id="59e7b-113">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="59e7b-113">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="59e7b-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="59e7b-114">HRESULT</span></span>|<span data-ttu-id="59e7b-115">説明</span><span class="sxs-lookup"><span data-stu-id="59e7b-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59e7b-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="59e7b-116">S_OK</span></span>|<span data-ttu-id="59e7b-117">現在のフレームのコンテキストが正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="59e7b-117">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="59e7b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="59e7b-118">E_FAIL</span></span>|<span data-ttu-id="59e7b-119">コンテキストを返すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="59e7b-119">The context could not be returned.</span></span>|  
|<span data-ttu-id="59e7b-120">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT バッファー)</span><span class="sxs-lookup"><span data-stu-id="59e7b-120">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="59e7b-121">コンテキストバッファーが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="59e7b-121">The context buffer is too small.</span></span>|  
|<span data-ttu-id="59e7b-122">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="59e7b-122">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="59e7b-123">フレームポインターは既にスタックの末尾にあります。そのため、追加のフレームにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="59e7b-123">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="59e7b-124">例外</span><span class="sxs-lookup"><span data-stu-id="59e7b-124">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59e7b-125">解説</span><span class="sxs-lookup"><span data-stu-id="59e7b-125">Remarks</span></span>  

 <span data-ttu-id="59e7b-126">アンワインドでは、非揮発性レジスタなどのレジスタのサブセットのみが復元されるため、呼び出し時にコンテキストがレジスタの状態と完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="59e7b-126">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59e7b-127">要件</span><span class="sxs-lookup"><span data-stu-id="59e7b-127">Requirements</span></span>  

 <span data-ttu-id="59e7b-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59e7b-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59e7b-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59e7b-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59e7b-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59e7b-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59e7b-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59e7b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e7b-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="59e7b-132">See also</span></span>

- [<span data-ttu-id="59e7b-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="59e7b-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="59e7b-134">デバッグ</span><span class="sxs-lookup"><span data-stu-id="59e7b-134">Debugging</span></span>](index.md)
