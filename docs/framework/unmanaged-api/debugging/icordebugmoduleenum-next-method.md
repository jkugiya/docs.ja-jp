---
description: '詳細については、次のメソッドを参照してください: いいね。'
title: ICorDebugModuleEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: ed9558edad80c67e7bf3febb10c3adcd027e180a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650275"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="b0ef9-103">ICorDebugModuleEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="b0ef9-103">ICorDebugModuleEnum::Next Method</span></span>

<span data-ttu-id="b0ef9-104">によって指定された "のモジュール" インスタンスの数を列挙から取得します。この数は `celt` 、現在の位置から開始します。</span><span class="sxs-lookup"><span data-stu-id="b0ef9-104">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ef9-105">構文</span><span class="sxs-lookup"><span data-stu-id="b0ef9-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0ef9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0ef9-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="b0ef9-107">から `ICorDebugModule` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="b0ef9-107">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="b0ef9-108">入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugModule` ます。</span><span class="sxs-lookup"><span data-stu-id="b0ef9-108">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b0ef9-109">入出力実際に返されたインスタンスの数へのポインター `ICorDebugModule` 。</span><span class="sxs-lookup"><span data-stu-id="b0ef9-109">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="b0ef9-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="b0ef9-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ef9-111">要件</span><span class="sxs-lookup"><span data-stu-id="b0ef9-111">Requirements</span></span>  

 <span data-ttu-id="b0ef9-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0ef9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0ef9-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0ef9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0ef9-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0ef9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0ef9-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0ef9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ef9-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0ef9-116">See also</span></span>
