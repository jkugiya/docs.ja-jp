---
description: '詳細情報: テキスト処理:: GetThreadContext メソッド'
title: ICorDebugProcess::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: 4cb926183522548e924013580f207d1d0677a0d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746868"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="0a74c-103">ICorDebugProcess::GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="0a74c-103">ICorDebugProcess::GetThreadContext Method</span></span>

<span data-ttu-id="0a74c-104">このプロセス内の指定されたスレッドのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a74c-104">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a74c-105">構文</span><span class="sxs-lookup"><span data-stu-id="0a74c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a74c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a74c-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="0a74c-107">からコンテキストを取得するスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="0a74c-107">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="0a74c-108">[in] `context` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="0a74c-108">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="0a74c-109">[入力、出力]スレッドのコンテキストを記述するバイト配列。</span><span class="sxs-lookup"><span data-stu-id="0a74c-109">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="0a74c-110">コンテキストは、スレッドが実行されているプロセッサのアーキテクチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="0a74c-110">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a74c-111">解説</span><span class="sxs-lookup"><span data-stu-id="0a74c-111">Remarks</span></span>  

 <span data-ttu-id="0a74c-112">デバッガーは、Win32 メソッドではなく、このメソッドを呼び出す必要があります。これは、 `GetThreadContext` スレッドが実際には "ハイジャック" 状態にあり、そのコンテキストが一時的に変更されている可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="0a74c-112">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="0a74c-113">このメソッドは、スレッドがネイティブコード内にある場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="0a74c-113">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="0a74c-114">マネージコード内のスレッドには、コード [を使用し](icordebugregisterset-interface.md) ます。</span><span class="sxs-lookup"><span data-stu-id="0a74c-114">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="0a74c-115">返されるデータは、現在のプラットフォームのコンテキスト構造です。</span><span class="sxs-lookup"><span data-stu-id="0a74c-115">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="0a74c-116">Win32 メソッドの場合と同様に、 `GetThreadContext` 呼び出し元は、 `context` このメソッドを呼び出す前にパラメーターを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a74c-116">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a74c-117">要件</span><span class="sxs-lookup"><span data-stu-id="0a74c-117">Requirements</span></span>  

 <span data-ttu-id="0a74c-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a74c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a74c-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a74c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a74c-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a74c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a74c-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a74c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
