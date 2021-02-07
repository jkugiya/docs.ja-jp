---
description: 詳細については、次のメソッドを参照してください。
title: ICorDebugHeapEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 22e81b9b0c4ac2027f932187b6f860d08adf6f97
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691953"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="1f565-103">ICorDebugHeapEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="1f565-103">ICorDebugHeapEnum::Next Method</span></span>

<span data-ttu-id="1f565-104">マネージヒープ上のオブジェクトに関する情報を格納している、指定した数の [COR_HEAPOBJECT](cor-heapobject-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="1f565-104">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f565-105">構文</span><span class="sxs-lookup"><span data-stu-id="1f565-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f565-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1f565-106">Parameters</span></span>  

 <span data-ttu-id="1f565-107">celt</span><span class="sxs-lookup"><span data-stu-id="1f565-107">celt</span></span>  
 <span data-ttu-id="1f565-108">[in] 取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="1f565-108">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="1f565-109">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="1f565-109">objects</span></span>  
 <span data-ttu-id="1f565-110">入出力ポインターの配列。各ポインターは、マネージヒープ上のオブジェクトに関する情報を提供する [COR_HEAPOBJECT](cor-heapobject-structure.md) オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="1f565-110">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="1f565-111">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="1f565-111">pceltFetched</span></span>  
 <span data-ttu-id="1f565-112">入出力実際にで返される [COR_HEAPOBJECT](cor-heapobject-structure.md) オブジェクトの数へのポインター `objects` 。</span><span class="sxs-lookup"><span data-stu-id="1f565-112">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="1f565-113">`celt` が 1 の場合、この値は`null` になることがあります。</span><span class="sxs-lookup"><span data-stu-id="1f565-113">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f565-114">解説</span><span class="sxs-lookup"><span data-stu-id="1f565-114">Remarks</span></span>  

 <span data-ttu-id="1f565-115">`COR_HEAPOBJECT.type` フィールドは、入れ子になった参照カウントの COM インターフェイスの識別子です。</span><span class="sxs-lookup"><span data-stu-id="1f565-115">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="1f565-116">この参照は、`ICorDebugHeapEnum::Next` の呼び出し元によって解放される必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f565-116">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f565-117">要件</span><span class="sxs-lookup"><span data-stu-id="1f565-117">Requirements</span></span>  

 <span data-ttu-id="1f565-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f565-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f565-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f565-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f565-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f565-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f565-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f565-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f565-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f565-122">See also</span></span>

- [<span data-ttu-id="1f565-123">ICorDebugHeapEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f565-123">ICorDebugHeapEnum Interface</span></span>](icordebugheapenum-interface.md)
- [<span data-ttu-id="1f565-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f565-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
