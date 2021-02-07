---
description: '詳細については、次のメソッドを参照してください: いいね。'
title: ICorDebugStepperEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
ms.openlocfilehash: e0c17fbc570d5ea8a4a56c89a5a2c855ed045bd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717460"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="6194d-103">ICorDebugStepperEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="6194d-103">ICorDebugStepperEnum::Next Method</span></span>

<span data-ttu-id="6194d-104">現在の位置から開始して、指定した数の ICorDebugStepper インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="6194d-104">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6194d-105">構文</span><span class="sxs-lookup"><span data-stu-id="6194d-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6194d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6194d-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="6194d-107">から `ICorDebugStepper` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="6194d-107">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="6194d-108">入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugStepper` ます。</span><span class="sxs-lookup"><span data-stu-id="6194d-108">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6194d-109">入出力実際に返されたインスタンスの数へのポインター `ICorDebugStepper` 。</span><span class="sxs-lookup"><span data-stu-id="6194d-109">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="6194d-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="6194d-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6194d-111">要件</span><span class="sxs-lookup"><span data-stu-id="6194d-111">Requirements</span></span>  

 <span data-ttu-id="6194d-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6194d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6194d-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6194d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6194d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6194d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6194d-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6194d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
