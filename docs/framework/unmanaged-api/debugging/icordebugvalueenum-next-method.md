---
description: '詳細については、次のメソッドを参照してください。: いいね Enum:: Next メソッド'
title: ICorDebugValueEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: 9a02c769f69651227669eb4b3f8c5ce41b670a73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690107"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="79f06-103">ICorDebugValueEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="79f06-103">ICorDebugValueEnum::Next Method</span></span>

<span data-ttu-id="79f06-104">現在の位置から開始して、指定した数の "ICorDebugValue" インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="79f06-104">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79f06-105">構文</span><span class="sxs-lookup"><span data-stu-id="79f06-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79f06-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="79f06-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="79f06-107">から `ICorDebugValue` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="79f06-107">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="79f06-108">入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugValue` ます。</span><span class="sxs-lookup"><span data-stu-id="79f06-108">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="79f06-109">入出力実際に返されたインスタンスの数へのポインター `ICorDebugValue` 。</span><span class="sxs-lookup"><span data-stu-id="79f06-109">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="79f06-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="79f06-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79f06-111">要件</span><span class="sxs-lookup"><span data-stu-id="79f06-111">Requirements</span></span>  

 <span data-ttu-id="79f06-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79f06-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79f06-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79f06-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79f06-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79f06-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79f06-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79f06-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f06-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="79f06-116">See also</span></span>
