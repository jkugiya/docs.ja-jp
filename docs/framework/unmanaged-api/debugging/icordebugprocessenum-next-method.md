---
description: '詳細については、次のページを参照してください:: は、次のメソッド'
title: ICorDebugProcessEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
ms.openlocfilehash: e32ff2e67f3f8a0242e0a0f93ed00229fee9cc26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691173"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="83f91-103">ICorDebugProcessEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="83f91-103">ICorDebugProcessEnum::Next Method</span></span>

<span data-ttu-id="83f91-104">現在の位置から開始して、指定された数の処理インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="83f91-104">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f91-105">構文</span><span class="sxs-lookup"><span data-stu-id="83f91-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83f91-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83f91-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="83f91-107">から `ICorDebugProcess` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="83f91-107">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="83f91-108">入出力ポインターの配列。各ポインターは、 `ICorDebugProcess` プロセスを表すオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="83f91-108">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="83f91-109">入出力実際に返されたインスタンスの数へのポインター `ICorDebugProcess` 。</span><span class="sxs-lookup"><span data-stu-id="83f91-109">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="83f91-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="83f91-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83f91-111">要件</span><span class="sxs-lookup"><span data-stu-id="83f91-111">Requirements</span></span>  

 <span data-ttu-id="83f91-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83f91-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f91-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83f91-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83f91-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83f91-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83f91-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83f91-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
