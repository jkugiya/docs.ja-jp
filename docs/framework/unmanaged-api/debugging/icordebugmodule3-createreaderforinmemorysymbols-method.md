---
description: '詳細について: ICorDebugModule3:: CreateReaderForInMemorySymbols メソッド'
title: ICorDebugModule3::CreateReaderForInMemorySymbols メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: af037cc891e83f53fd94bad290f40286ed665e6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790777"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="5c21a-103">ICorDebugModule3::CreateReaderForInMemorySymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="5c21a-103">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>

<span data-ttu-id="5c21a-104">動的モジュールのデバッグシンボルリーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5c21a-104">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c21a-105">構文</span><span class="sxs-lookup"><span data-stu-id="5c21a-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c21a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c21a-106">Parameters</span></span>  

 <span data-ttu-id="5c21a-107">riid</span><span class="sxs-lookup"><span data-stu-id="5c21a-107">riid</span></span>  
 <span data-ttu-id="5c21a-108">から返す COM インターフェイスの IID。</span><span class="sxs-lookup"><span data-stu-id="5c21a-108">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="5c21a-109">通常、これは [ISymUnmanagedReader インターフェイス](../diagnostics/isymunmanagedreader-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c21a-109">Typically, this is an [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="5c21a-110">ppObj</span><span class="sxs-lookup"><span data-stu-id="5c21a-110">ppObj</span></span>  
 <span data-ttu-id="5c21a-111">入出力返されたインターフェイスへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5c21a-111">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c21a-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="5c21a-112">Return Value</span></span>  

 <span data-ttu-id="5c21a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c21a-113">S_OK</span></span>  
 <span data-ttu-id="5c21a-114">リーダーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="5c21a-114">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="5c21a-115">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="5c21a-115">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="5c21a-116">モジュールがメモリ内または動的モジュールではありません。</span><span class="sxs-lookup"><span data-stu-id="5c21a-116">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="5c21a-117">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c21a-117">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="5c21a-118">シンボルは、アプリケーションによって提供されていないか、まだ使用できません。</span><span class="sxs-lookup"><span data-stu-id="5c21a-118">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="5c21a-119">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="5c21a-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="5c21a-120">リーダーを作成できません。</span><span class="sxs-lookup"><span data-stu-id="5c21a-120">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c21a-121">解説</span><span class="sxs-lookup"><span data-stu-id="5c21a-121">Remarks</span></span>  

 <span data-ttu-id="5c21a-122">このメソッドを使用して、インメモリ (非動的) モジュール用のシンボルリーダーオブジェクトを作成することもできますが、最初にシンボルを使用できるようになった後 ( [UpdateModuleSymbols メソッド](icordebugmanagedcallback-updatemodulesymbols-method.md) コールバックによって示されます) にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5c21a-122">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="5c21a-123">このメソッドは、呼び出されるたびに新しいリーダーインスタンスを返します ( [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)など)。</span><span class="sxs-lookup"><span data-stu-id="5c21a-123">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="5c21a-124">したがって、デバッガーは、基になるデータが変更されている (つまり、 [Loadclass メソッド](icordebugmanagedcallback-loadclass-method.md) のコールバックが受信された) 場合にのみ、結果をキャッシュし、新しいインスタンスを要求します。</span><span class="sxs-lookup"><span data-stu-id="5c21a-124">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="5c21a-125">動的モジュールでは、最初の型が読み込まれるまで ( [Loadclass メソッド](icordebugmanagedcallback-loadclass-method.md) コールバックによって示されるように) シンボルは使用できません。</span><span class="sxs-lookup"><span data-stu-id="5c21a-125">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c21a-126">要件</span><span class="sxs-lookup"><span data-stu-id="5c21a-126">Requirements</span></span>  

 <span data-ttu-id="5c21a-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c21a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c21a-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c21a-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c21a-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c21a-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c21a-130">**.NET Framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="5c21a-130">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c21a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c21a-131">See also</span></span>

- [<span data-ttu-id="5c21a-132">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c21a-132">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="5c21a-133">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c21a-133">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="5c21a-134">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c21a-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
