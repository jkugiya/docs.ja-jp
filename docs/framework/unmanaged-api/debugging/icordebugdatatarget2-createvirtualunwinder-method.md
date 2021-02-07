---
description: '詳細について: ICorDebugDataTarget2:: CreateVirtualUnwinder メソッド'
title: ICorDebugDataTarget2::CreateVirtualUnwinder メソッド
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 0646c85000f42b303769d6587354b3105e2deabd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764412"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="f2a99-103">ICorDebugDataTarget2::CreateVirtualUnwinder メソッド</span><span class="sxs-lookup"><span data-stu-id="f2a99-103">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>

<span data-ttu-id="f2a99-104">初期コンテキストからアンワインドを開始する新しいスタック アンワインダーを作成します (これは、必ずしもスレッドのリーフではありません)。</span><span class="sxs-lookup"><span data-stu-id="f2a99-104">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a99-105">構文</span><span class="sxs-lookup"><span data-stu-id="f2a99-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2a99-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f2a99-106">Parameters</span></span>  

 <span data-ttu-id="f2a99-107">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="f2a99-107">nativeThreadID</span></span>  
 <span data-ttu-id="f2a99-108">[入力] スタックをアンワインドするスレッドのネイティブ スレッド ID。</span><span class="sxs-lookup"><span data-stu-id="f2a99-108">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="f2a99-109">contextFlags</span><span class="sxs-lookup"><span data-stu-id="f2a99-109">contextFlags</span></span>  
 <span data-ttu-id="f2a99-110">[入力] コンテキストのどの部分が `initialContext` で定義されるかを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="f2a99-110">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="f2a99-111">cbContext</span><span class="sxs-lookup"><span data-stu-id="f2a99-111">cbContext</span></span>  
 <span data-ttu-id="f2a99-112">[入力] `initialContext` のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f2a99-112">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="f2a99-113">initialContext</span><span class="sxs-lookup"><span data-stu-id="f2a99-113">initialContext</span></span>  
 <span data-ttu-id="f2a99-114">[入力] コンテキストのデータ。</span><span class="sxs-lookup"><span data-stu-id="f2a99-114">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="f2a99-115">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="f2a99-115">ppUnwinder</span></span>  
 <span data-ttu-id="f2a99-116">[出力] ICorDebugVirtualUnwinder インターフェイス オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f2a99-116">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2a99-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="f2a99-117">Return Value</span></span>  

 <span data-ttu-id="f2a99-118">正常終了した場合は、`S_OK`。</span><span class="sxs-lookup"><span data-stu-id="f2a99-118">`S_OK` if successful.</span></span> <span data-ttu-id="f2a99-119">それ以外の `HRESULT` は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="f2a99-119">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="f2a99-120">`HRESULT`Mscordbi.dll によって受信された失敗は、致命的と見なされ、 [ICorDebug](icordebug-interface.md)メソッドによって返さ `CORDBG_E_DATA_TARGET_ERROR` れます。</span><span class="sxs-lookup"><span data-stu-id="f2a99-120">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2a99-121">解説</span><span class="sxs-lookup"><span data-stu-id="f2a99-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2a99-122">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2a99-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2a99-123">要件</span><span class="sxs-lookup"><span data-stu-id="f2a99-123">Requirements</span></span>  

 <span data-ttu-id="f2a99-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2a99-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2a99-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2a99-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2a99-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2a99-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2a99-127">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a99-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a99-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2a99-128">See also</span></span>

- [<span data-ttu-id="f2a99-129">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2a99-129">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="f2a99-130">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2a99-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
