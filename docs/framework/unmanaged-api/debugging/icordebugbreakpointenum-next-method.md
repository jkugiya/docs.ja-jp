---
description: '詳細については、次の情報を参照してください: いいね Pointenum:: Next メソッド'
title: ICorDebugBreakpointEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
ms.openlocfilehash: 966494bbabaca99b6b5168db6fb7616c15c537e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711675"
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="17fb6-103">ICorDebugBreakpointEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="17fb6-103">ICorDebugBreakpointEnum::Next Method</span></span>

<span data-ttu-id="17fb6-104">現在の位置から開始して、指定した数の ICorDebugBreakpoint インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="17fb6-104">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17fb6-105">構文</span><span class="sxs-lookup"><span data-stu-id="17fb6-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17fb6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17fb6-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="17fb6-107">から `ICorDebugBreakpoint` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="17fb6-107">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="17fb6-108">入出力ポインターの配列。各ポインターは、 `ICorDebugBreakpoint` ブレークポイントを表すオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="17fb6-108">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="17fb6-109">入出力実際に返されたインスタンスの数へのポインター `ICorDebugBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="17fb6-109">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="17fb6-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="17fb6-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17fb6-111">要件</span><span class="sxs-lookup"><span data-stu-id="17fb6-111">Requirements</span></span>  

 <span data-ttu-id="17fb6-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17fb6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17fb6-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17fb6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17fb6-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17fb6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17fb6-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17fb6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
