---
description: '詳細について: ICorDebugCode3:: Getreturnvalu Veoffset メソッド'
title: ICorDebugCode3::GetReturnValueLiveOffset メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
ms.openlocfilehash: 6ec9a342805c047d7331c3ce2af2a4ffba596a26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711012"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="bfe5d-103">ICorDebugCode3::GetReturnValueLiveOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="bfe5d-103">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>

<span data-ttu-id="bfe5d-104">指定した IL オフセットについて、デバッガーが関数からの戻り値を取得できるように、ブレークポイントを配置する必要があるネイティブなオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-104">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfe5d-105">構文</span><span class="sxs-lookup"><span data-stu-id="bfe5d-105">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfe5d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bfe5d-106">Parameters</span></span>  

 `ILoffset`  
 <span data-ttu-id="bfe5d-107">オフセット IL。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-107">The IL offset.</span></span> <span data-ttu-id="bfe5d-108">関数呼び出しサイトであることが必要です。そうでない場合、関数呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-108">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="bfe5d-109">`pOffsets` を格納できるバイト数。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-109">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="bfe5d-110">実際に返されたオフセットの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-110">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="bfe5d-111">通常、この値は 1 ですが、単一の IL 命令が複数の `CALL` アセンブリ命令にマップする場合があります。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-111">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="bfe5d-112">ネイティブ オフセットの配列。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-112">An array of native offsets.</span></span> <span data-ttu-id="bfe5d-113">通常、`pOffsets` には単一のオフセットが含まれますが、単一の IL 命令が複数の `CALL` アセンブリ命令に対する複数のマップに対応する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-113">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfe5d-114">解説</span><span class="sxs-lookup"><span data-stu-id="bfe5d-114">Remarks</span></span>  

 <span data-ttu-id="bfe5d-115">このメソッドは、参照型を返すメソッドの戻り値を取得するために、 [ICorDebugILFrame3:: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) メソッドと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-115">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="bfe5d-116">関数呼び出しサイトに対する IL オフセットをこのメソッドに渡すと、1 つ以上のネイティブ オフセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-116">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="bfe5d-117">これによってデバッガーは、関数内のこうしたネイティブ オフセット上でブレークポイントを設定できます。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="bfe5d-118">デバッガーがいずれかのブレークポイントにヒットすると、このメソッドに渡された同じ IL オフセットを [ICorDebugILFrame3:: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) メソッドに渡して、戻り値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="bfe5d-119">この場合、デバッガーは設定したブレークポイントすべてをクリアする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="bfe5d-120">`ICorDebugCode3::GetReturnValueLiveOffset`および[ICorDebugILFrame3:: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)メソッドを使用すると、参照型の戻り値の情報のみを取得できます。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-120">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="bfe5d-121">値型 (つまり、<xref:System.ValueType> から派生するすべての型) からの戻り値情報の取得はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="bfe5d-122">この関数は、次の表に示す `HRESULT` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-122">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="bfe5d-123">`HRESULT` 値</span><span class="sxs-lookup"><span data-stu-id="bfe5d-123">`HRESULT` value</span></span>|<span data-ttu-id="bfe5d-124">説明</span><span class="sxs-lookup"><span data-stu-id="bfe5d-124">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="bfe5d-125">正常終了しました。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-125">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="bfe5d-126">指定した IL オフセット サイトが呼び出し命令ではないか、関数が `void` を返しています。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-126">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="bfe5d-127">指定した IL オフセットは適切な呼び出しですが、取得する戻り値の型がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-127">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="bfe5d-128">`ICorDebugCode3::GetReturnValueLiveOffset` メソッドは、x86 ベースおよび AMD64 システムでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-128">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfe5d-129">要件</span><span class="sxs-lookup"><span data-stu-id="bfe5d-129">Requirements</span></span>  

 <span data-ttu-id="bfe5d-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfe5d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfe5d-131">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bfe5d-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfe5d-132">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfe5d-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfe5d-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfe5d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe5d-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfe5d-134">See also</span></span>

- [<span data-ttu-id="bfe5d-135">GetReturnValueForILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="bfe5d-135">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="bfe5d-136">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfe5d-136">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
