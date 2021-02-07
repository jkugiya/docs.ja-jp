---
description: '詳細情報: ICorDebugStepper:: StepRange メソッド'
title: ICorDebugStepper::StepRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
ms.openlocfilehash: 868925ef301cca15b7887505e879f5fff02002e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717564"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="ac016-103">ICorDebugStepper::StepRange メソッド</span><span class="sxs-lookup"><span data-stu-id="ac016-103">ICorDebugStepper::StepRange Method</span></span>

<span data-ttu-id="ac016-104">この ICorDebugStepper は、含まれているスレッドを1ステップずつ実行し、指定した範囲の最後のコードに到達したときにを返します。</span><span class="sxs-lookup"><span data-stu-id="ac016-104">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac016-105">構文</span><span class="sxs-lookup"><span data-stu-id="ac016-105">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac016-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac016-106">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="ac016-107">から `true` スレッド内で呼び出される関数にステップインするには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="ac016-107">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="ac016-108">関数を `false` ステップオーバーするには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="ac016-108">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="ac016-109">からCOR_DEBUG_STEP_RANGE 構造体の配列。それぞれが範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac016-109">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="ac016-110">[in] `ranges` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="ac016-110">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac016-111">解説</span><span class="sxs-lookup"><span data-stu-id="ac016-111">Remarks</span></span>  

 <span data-ttu-id="ac016-112">`StepRange`メソッドは[ICorDebugStepper:: Step](icordebugstepper-step-method.md)メソッドと同様に機能しますが、指定された範囲外のコードに到達するまでは完了しない点が異なります。</span><span class="sxs-lookup"><span data-stu-id="ac016-112">The `StepRange` method works like the [ICorDebugStepper::Step](icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="ac016-113">これは、一度に1つの命令をステップ実行するよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="ac016-113">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="ac016-114">範囲は、ステッパのフレームの先頭からのオフセットペアのリストとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="ac016-114">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="ac016-115">範囲は、メソッドの MSIL (Microsoft 中間言語) コードに対する相対値です。</span><span class="sxs-lookup"><span data-stu-id="ac016-115">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="ac016-116">[ICorDebugStepper:: SetRangeIL](icordebugstepper-setrangeil-method.md)をで呼び出し、 `false` メソッドのネイティブコードを基準として範囲を設定します。</span><span class="sxs-lookup"><span data-stu-id="ac016-116">Call [ICorDebugStepper::SetRangeIL](icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac016-117">要件</span><span class="sxs-lookup"><span data-stu-id="ac016-117">Requirements</span></span>  

 <span data-ttu-id="ac016-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac016-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac016-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac016-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac016-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac016-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac016-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac016-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
