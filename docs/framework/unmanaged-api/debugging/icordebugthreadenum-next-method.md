---
description: '詳細については、次のメソッドを参照してください。: いいね。'
title: ICorDebugThreadEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
ms.openlocfilehash: 2cfb651d65eaf0f5797444ea1bec587cebdde2f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658426"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="57703-103">ICorDebugThreadEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="57703-103">ICorDebugThreadEnum::Next Method</span></span>

<span data-ttu-id="57703-104">現在の位置から開始して、列挙体から指定されたスレッドインスタンスの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="57703-104">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57703-105">構文</span><span class="sxs-lookup"><span data-stu-id="57703-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57703-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="57703-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="57703-107">から `ICorDebugThread` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="57703-107">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="57703-108">入出力ポインターの配列。各ポインターは、 `ICorDebugThread` スレッドを表すオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="57703-108">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="57703-109">入出力実際に返されたインスタンスの数へのポインター `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="57703-109">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="57703-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="57703-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57703-111">要件</span><span class="sxs-lookup"><span data-stu-id="57703-111">Requirements</span></span>  

 <span data-ttu-id="57703-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57703-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57703-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57703-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57703-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57703-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57703-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57703-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
