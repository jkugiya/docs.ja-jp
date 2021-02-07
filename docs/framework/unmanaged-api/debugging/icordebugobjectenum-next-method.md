---
description: 詳細については、次のメソッドを参照してください。
title: ICorDebugObjectEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: dd7d4240827e14962edf7573b59b273f65231bcf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729043"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="1c2c8-103">ICorDebugObjectEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="1c2c8-103">ICorDebugObjectEnum::Next Method</span></span>

<span data-ttu-id="1c2c8-104">列挙から、指定した数のオブジェクトの相対仮想アドレス (RVAs) を取得します。この値は、現在の位置から開始されます。</span><span class="sxs-lookup"><span data-stu-id="1c2c8-104">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c2c8-105">構文</span><span class="sxs-lookup"><span data-stu-id="1c2c8-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c2c8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c2c8-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="1c2c8-107">[in] 取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="1c2c8-107">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="1c2c8-108">入出力ポインターの配列。それぞれが CORDB_ADDRESS オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="1c2c8-108">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1c2c8-109">入出力実際に返されたオブジェクトの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1c2c8-109">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="1c2c8-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="1c2c8-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c2c8-111">要件</span><span class="sxs-lookup"><span data-stu-id="1c2c8-111">Requirements</span></span>  

 <span data-ttu-id="1c2c8-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c2c8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c2c8-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c2c8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c2c8-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c2c8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c2c8-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c2c8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c2c8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c2c8-116">See also</span></span>
