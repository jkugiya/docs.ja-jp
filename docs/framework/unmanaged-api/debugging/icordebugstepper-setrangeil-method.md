---
description: '詳細について: ICorDebugStepper:: SetRangeIL メソッド'
title: ICorDebugStepper::SetRangeIL メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: 8bccaf8ba8e52a7fe94555fa99b1c3cf92842efe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717702"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="2519f-103">ICorDebugStepper::SetRangeIL メソッド</span><span class="sxs-lookup"><span data-stu-id="2519f-103">ICorDebugStepper::SetRangeIL Method</span></span>

<span data-ttu-id="2519f-104">[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md)の呼び出しで、ネイティブコードに対して相対的な引数値を渡すか、またはステップスルー中のメソッドの MSIL (Microsoft 中間言語) コードに対する相対パスを指定するかを指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="2519f-104">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2519f-105">構文</span><span class="sxs-lookup"><span data-stu-id="2519f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2519f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2519f-106">Parameters</span></span>  

 `bIL`  
 <span data-ttu-id="2519f-107">から `true` 範囲が MSIL コードに対して相対的であることを指定するには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="2519f-107">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="2519f-108">`false`範囲がネイティブコードに対して相対的であることを指定するには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="2519f-108">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="2519f-109">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="2519f-109">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2519f-110">要件</span><span class="sxs-lookup"><span data-stu-id="2519f-110">Requirements</span></span>  

 <span data-ttu-id="2519f-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2519f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2519f-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2519f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2519f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2519f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2519f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2519f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
