---
description: '詳細について: ICorDebugILFrame3:: GetReturnValueForILOffset メソッド'
title: ICorDebugILFrame3::GetReturnValueForILOffset メソッド
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: 4be4cb3a108394f2701f6690b06f6c2252ae25cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791271"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="aad2e-103">ICorDebugILFrame3::GetReturnValueForILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="aad2e-103">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>

<span data-ttu-id="aad2e-104">関数の戻り値をカプセル化する "ICorDebugValue" オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="aad2e-104">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad2e-105">構文</span><span class="sxs-lookup"><span data-stu-id="aad2e-105">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aad2e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aad2e-106">Parameters</span></span>  

 `ILOffset`  
 <span data-ttu-id="aad2e-107">オフセット IL。</span><span class="sxs-lookup"><span data-stu-id="aad2e-107">The IL offset.</span></span> <span data-ttu-id="aad2e-108">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aad2e-108">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="aad2e-109">関数呼び出しの戻り値に関する情報を提供する "ICorDebugValue" インターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aad2e-109">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aad2e-110">解説</span><span class="sxs-lookup"><span data-stu-id="aad2e-110">Remarks</span></span>  

 <span data-ttu-id="aad2e-111">このメソッドは、メソッドの戻り値を取得するために、 [ICorDebugCode3:: Getreturnvalu Veoffset](icordebugcode3-getreturnvalueliveoffset-method.md) メソッドと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="aad2e-111">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="aad2e-112">次の 2 つのコード例で示すように、これは戻り値が無視されるメソッドの場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aad2e-112">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="aad2e-113">1 番目の例では、<xref:System.Int32.TryParse%2A?displayProperty=nameWithType> メソッドを呼び出しますが、メソッドの戻り値を無視します。</span><span class="sxs-lookup"><span data-stu-id="aad2e-113">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="aad2e-114">2 番目の例は、より一般的なデバッグの問題を示しています。</span><span class="sxs-lookup"><span data-stu-id="aad2e-114">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="aad2e-115">メソッド呼び出しで引数としてメソッドが使用されるため、デバッガーで呼び出されたメソッドをステップ実行する場合に限り、戻り値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="aad2e-115">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="aad2e-116">多くの場合、特に呼び出されたメソッドが外部ライブラリで定義されている場合にはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="aad2e-116">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="aad2e-117">[ICorDebugCode3:: Getreturnvalu veoffset](icordebugcode3-getreturnvalueliveoffset-method.md)メソッドに関数呼び出しサイトへの IL オフセットを渡すと、1つ以上のネイティブオフセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="aad2e-117">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="aad2e-118">これによってデバッガーは、関数内のこうしたネイティブ オフセット上でブレークポイントを設定できます。</span><span class="sxs-lookup"><span data-stu-id="aad2e-118">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="aad2e-119">デバッガーがいずれかのブレークポイントに到達すると、戻り値を取得するためにこのメソッドに同じ IL オフセットを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="aad2e-119">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="aad2e-120">この場合、デバッガーは設定したブレークポイントすべてをクリアする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aad2e-120">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="aad2e-121">[ICorDebugCode3:: Getreturnvalu Veoffset メソッド](icordebugcode3-getreturnvalueliveoffset-method.md)とメソッドを使用すると、 `ICorDebugILFrame3::GetReturnValueForILOffset` 参照型の戻り値の情報のみを取得できます。</span><span class="sxs-lookup"><span data-stu-id="aad2e-121">The [ICorDebugCode3::GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="aad2e-122">値型 (つまり、<xref:System.ValueType> から派生するすべての型) からの戻り値情報の取得はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="aad2e-122">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="aad2e-123">パラメーターで指定された IL オフセットは `ILOffset` 関数呼び出しサイトに存在する必要があります。また、同じ il オフセットの [ICorDebugCode3:: Getreturnvalu veoffset](icordebugcode3-getreturnvalueliveoffset-method.md) メソッドによって返されるネイティブオフセットに設定されているブレークポイントで、デバッグ対象を停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aad2e-123">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="aad2e-124">デバッグ対象が指定の IL オフセットに対して正確な場所で停止しない場合、API は失敗します。</span><span class="sxs-lookup"><span data-stu-id="aad2e-124">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="aad2e-125">関数呼び出しで値が返されない場合、API は失敗します。</span><span class="sxs-lookup"><span data-stu-id="aad2e-125">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="aad2e-126">`ICorDebugILFrame3::GetReturnValueForILOffset` メソッドは、x86 ベースおよび AMD64 システムでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="aad2e-126">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aad2e-127">要件</span><span class="sxs-lookup"><span data-stu-id="aad2e-127">Requirements</span></span>  

 <span data-ttu-id="aad2e-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aad2e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aad2e-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aad2e-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aad2e-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aad2e-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aad2e-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aad2e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad2e-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="aad2e-132">See also</span></span>

- [<span data-ttu-id="aad2e-133">GetReturnValueLiveOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="aad2e-133">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="aad2e-134">ICorDebugILFrame3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aad2e-134">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
