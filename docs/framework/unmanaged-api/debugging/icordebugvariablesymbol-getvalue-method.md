---
description: '詳細情報: ICorDebugVariableSymbol:: GetValue メソッド'
title: ICorDebugVariableSymbol::GetValue メソッド
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: ccd7eae5cc4740e83d0210a903ba0e7778aa8896
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790569"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="d619c-103">ICorDebugVariableSymbol::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="d619c-103">ICorDebugVariableSymbol::GetValue Method</span></span>

<span data-ttu-id="d619c-104">変数の値をバイト配列として取得します。</span><span class="sxs-lookup"><span data-stu-id="d619c-104">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d619c-105">構文</span><span class="sxs-lookup"><span data-stu-id="d619c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d619c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d619c-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="d619c-107">[in] 値を読み取る変数内の開始オフセットです。</span><span class="sxs-lookup"><span data-stu-id="d619c-107">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="d619c-108">このパラメーターは、オブジェクトのメンバー フィールドを読み取る際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d619c-108">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="d619c-109">[in] `context` 引数のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="d619c-109">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="d619c-110">[in] 値の読み取りに使用されるスレッド コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="d619c-110">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="d619c-111">[in] `pValue` バッファーのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="d619c-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="d619c-112">[out] `pValue` バッファーに実際に書き込まれたバイト数。</span><span class="sxs-lookup"><span data-stu-id="d619c-112">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d619c-113">[out] 変数の値が格納されているバイト配列。</span><span class="sxs-lookup"><span data-stu-id="d619c-113">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d619c-114">解説</span><span class="sxs-lookup"><span data-stu-id="d619c-114">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d619c-115">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d619c-115">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d619c-116">要件</span><span class="sxs-lookup"><span data-stu-id="d619c-116">Requirements</span></span>  

 <span data-ttu-id="d619c-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d619c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d619c-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d619c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d619c-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d619c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d619c-120">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d619c-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d619c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d619c-121">See also</span></span>

- [<span data-ttu-id="d619c-122">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d619c-122">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="d619c-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d619c-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
