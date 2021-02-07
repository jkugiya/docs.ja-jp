---
description: '詳細情報: ICorDebugChainEnum:: Next メソッド'
title: ICorDebugChainEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
ms.openlocfilehash: 5ab6665eb5af6d9f145f9aab67aeb75b4769e7e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711571"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="3f7a2-103">ICorDebugChainEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="3f7a2-103">ICorDebugChainEnum::Next Method</span></span>

<span data-ttu-id="3f7a2-104">現在の位置から開始して、指定された数の値を列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="3f7a2-104">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7a2-105">構文</span><span class="sxs-lookup"><span data-stu-id="3f7a2-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f7a2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f7a2-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="3f7a2-107">から `ICorDebugChain` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="3f7a2-107">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="3f7a2-108">入出力ポインターの配列。各ポインターは、 `ICorDebugChain` チェーンを表すオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="3f7a2-108">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3f7a2-109">入出力実際に返されたインスタンスの数へのポインター `ICorDebugChain` 。</span><span class="sxs-lookup"><span data-stu-id="3f7a2-109">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="3f7a2-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="3f7a2-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f7a2-111">要件</span><span class="sxs-lookup"><span data-stu-id="3f7a2-111">Requirements</span></span>  

 <span data-ttu-id="3f7a2-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f7a2-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f7a2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f7a2-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f7a2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f7a2-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f7a2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
