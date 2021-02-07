---
description: '詳細情報: 「コード:: GetILToNativeMapping メソッド」を参照してください。'
title: ICorDebugCode::GetILToNativeMapping メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 808ed450fced8afecc2b637a3b990a894897b350
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711194"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="69130-103">ICorDebugCode::GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="69130-103">ICorDebugCode::GetILToNativeMapping Method</span></span>

<span data-ttu-id="69130-104">Microsoft 中間言語 (MSIL) オフセットからネイティブオフセットへのマッピングを表す "COR_DEBUG_IL_TO_NATIVE_MAP" インスタンスの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="69130-104">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69130-105">構文</span><span class="sxs-lookup"><span data-stu-id="69130-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69130-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="69130-106">Parameters</span></span>  

 `cMap`  
 <span data-ttu-id="69130-107">[in] `map` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="69130-107">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="69130-108">入出力配列で返された実際の要素数へのポインター `map` 。</span><span class="sxs-lookup"><span data-stu-id="69130-108">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="69130-109">入出力構造体の配列。 `COR_DEBUG_IL_TO_NATIVE_MAP` それぞれが MSIL オフセットからネイティブオフセットへのマッピングを表します。</span><span class="sxs-lookup"><span data-stu-id="69130-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="69130-110">返される要素の配列への順序はありません。</span><span class="sxs-lookup"><span data-stu-id="69130-110">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69130-111">解説</span><span class="sxs-lookup"><span data-stu-id="69130-111">Remarks</span></span>  

 <span data-ttu-id="69130-112">メソッドは、 `GetILToNativeMapping` この "" コード "インスタンスが MSIL コードからコンパイルされた just-in-time (JIT) コードを表している場合にのみ、意味のある結果を返します。</span><span class="sxs-lookup"><span data-stu-id="69130-112">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69130-113">要件</span><span class="sxs-lookup"><span data-stu-id="69130-113">Requirements</span></span>  

 <span data-ttu-id="69130-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69130-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69130-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69130-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69130-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69130-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69130-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69130-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69130-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="69130-118">See also</span></span>

- [<span data-ttu-id="69130-119">ICorDebugCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69130-119">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
