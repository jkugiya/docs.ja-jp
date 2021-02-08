---
description: '詳細について: ICorDebugStepper:: SetInterceptMask メソッド'
title: ICorDebugStepper::SetInterceptMask メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: 33a42b154d063a29022034fd8061599a5e0e5503
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803545"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="12de8-103">ICorDebugStepper::SetInterceptMask メソッド</span><span class="sxs-lookup"><span data-stu-id="12de8-103">ICorDebugStepper::SetInterceptMask Method</span></span>

<span data-ttu-id="12de8-104">ステップインするコードの種類を指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="12de8-104">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12de8-105">構文</span><span class="sxs-lookup"><span data-stu-id="12de8-105">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12de8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12de8-106">Parameters</span></span>  

 `mask`  
 <span data-ttu-id="12de8-107">からコードの種類を指定する CorDebugIntercept 列挙子の値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="12de8-107">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12de8-108">解説</span><span class="sxs-lookup"><span data-stu-id="12de8-108">Remarks</span></span>  

 <span data-ttu-id="12de8-109">インターセプターのビットが設定されている場合、指定された種類のインターセプトコードが検出されると、ステッパが完了します。</span><span class="sxs-lookup"><span data-stu-id="12de8-109">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="12de8-110">ビットがオフの場合、インターセプトコードはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="12de8-110">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="12de8-111">メソッドは、 `SetInterceptMask` [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (ユーザーの視点から見た) との予期しない相互作用を持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="12de8-111">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="12de8-112">たとえば、クラス初期化コードの表示されている (つまり、内部ではない) 部分にマッピング情報がなく、STOP_NO_MAPPING_INFO が設定されていない場合 (「 [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) メソッドと CorDebugUnmappedStop 列挙を参照してください)、ステッパはクラスの初期化をステップオーバーします。</span><span class="sxs-lookup"><span data-stu-id="12de8-112">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="12de8-113">既定では、列挙体の INTERCEPT_NONE 値のみ `CorDebugIntercept` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="12de8-113">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12de8-114">要件</span><span class="sxs-lookup"><span data-stu-id="12de8-114">Requirements</span></span>  

 <span data-ttu-id="12de8-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12de8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12de8-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12de8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12de8-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12de8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12de8-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12de8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
