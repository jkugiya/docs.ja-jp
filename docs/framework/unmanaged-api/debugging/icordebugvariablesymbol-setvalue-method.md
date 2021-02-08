---
description: '詳細について: ICorDebugVariableSymbol:: SetValue メソッド'
title: ICorDebugVariableSymbol::SetValue メソッド
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: aa36712defcf44039f17fe846113c15814549e09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800852"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="c51d0-103">ICorDebugVariableSymbol::SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="c51d0-103">ICorDebugVariableSymbol::SetValue Method</span></span>

<span data-ttu-id="c51d0-104">バイト配列の値を変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="c51d0-104">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c51d0-105">構文</span><span class="sxs-lookup"><span data-stu-id="c51d0-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c51d0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c51d0-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="c51d0-107">[in] 値を設定する変数内の開始オフセットです。</span><span class="sxs-lookup"><span data-stu-id="c51d0-107">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="c51d0-108">このパラメーターは、オブジェクトのメンバー フィールドに書き込む際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c51d0-108">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="c51d0-109">[in] 新しい値を反映させるためにコンテキストを更新する必要があるスレッドのスレッド ID。</span><span class="sxs-lookup"><span data-stu-id="c51d0-109">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="c51d0-110">[in] スレッド コンテキストのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="c51d0-110">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="c51d0-111">[in] 値の書き込みに使用されるスレッド コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="c51d0-111">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="c51d0-112">[in] `pValue` バッファーのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="c51d0-112">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="c51d0-113">[in] 設定する値が含まれるバッファー。</span><span class="sxs-lookup"><span data-stu-id="c51d0-113">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c51d0-114">解説</span><span class="sxs-lookup"><span data-stu-id="c51d0-114">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c51d0-115">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c51d0-115">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c51d0-116">要件</span><span class="sxs-lookup"><span data-stu-id="c51d0-116">Requirements</span></span>  

 <span data-ttu-id="c51d0-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c51d0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c51d0-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c51d0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c51d0-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c51d0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c51d0-120">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c51d0-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51d0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c51d0-121">See also</span></span>

- [<span data-ttu-id="c51d0-122">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c51d0-122">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="c51d0-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c51d0-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
