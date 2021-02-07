---
description: '詳細については、次のページを参照してください: いいね。:: GetThreadContext メソッド'
title: ICorDebugDataTarget::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: cf40579aa0a495af4e5e775334d177ca6f3da86f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710635"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="e9afd-103">ICorDebugDataTarget::GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="e9afd-103">ICorDebugDataTarget::GetThreadContext Method</span></span>

<span data-ttu-id="e9afd-104">指定されたスレッドの現在のスレッドコンテキストを返します。</span><span class="sxs-lookup"><span data-stu-id="e9afd-104">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9afd-105">構文</span><span class="sxs-lookup"><span data-stu-id="e9afd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9afd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9afd-106">Parameters</span></span>  

 `dwThreadID`  
 <span data-ttu-id="e9afd-107">からコンテキストを取得するスレッドの識別子。</span><span class="sxs-lookup"><span data-stu-id="e9afd-107">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="e9afd-108">識別子はオペレーティングシステムによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="e9afd-108">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="e9afd-109">からコンテキストのどの部分を読み取る必要があるかを示す、プラットフォームに依存するフラグのビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="e9afd-109">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="e9afd-110">[入力] `pContext` のサイズ。</span><span class="sxs-lookup"><span data-stu-id="e9afd-110">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="e9afd-111">入出力スレッドコンテキストが格納されるバッファー。</span><span class="sxs-lookup"><span data-stu-id="e9afd-111">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9afd-112">解説</span><span class="sxs-lookup"><span data-stu-id="e9afd-112">Remarks</span></span>  

 <span data-ttu-id="e9afd-113">Windows プラットフォームでは、は、の `pContext` `CONTEXT` 構造体 (winnt.h で定義されています) である必要があります。これは [、の](icordebugdatatarget-getplatform-method.md) 型によって指定されたコンピューターの種類に適しています。</span><span class="sxs-lookup"><span data-stu-id="e9afd-113">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="e9afd-114">`contextFlags` 構造体のフィールドと同じ値を持つ必要があり `ContextFlags` `CONTEXT` ます。</span><span class="sxs-lookup"><span data-stu-id="e9afd-114">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="e9afd-115">`CONTEXT`構造体はプロセッサに固有です。詳細については、winnt.h の .h ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9afd-115">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9afd-116">要件</span><span class="sxs-lookup"><span data-stu-id="e9afd-116">Requirements</span></span>  

 <span data-ttu-id="e9afd-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9afd-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9afd-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9afd-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9afd-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9afd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9afd-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9afd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9afd-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9afd-121">See also</span></span>

- [<span data-ttu-id="e9afd-122">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9afd-122">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="e9afd-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9afd-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e9afd-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="e9afd-124">Debugging</span></span>](index.md)
