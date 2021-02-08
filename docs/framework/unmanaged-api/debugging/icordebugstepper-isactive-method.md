---
description: '詳細について: ICorDebugStepper:: IsActive メソッド'
title: ICorDebugStepper::IsActive メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: 7ef937ac3c1e6f3ad9ad83b5fa84382cac3ac9c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803569"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="47dd4-103">ICorDebugStepper::IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="47dd4-103">ICorDebugStepper::IsActive Method</span></span>

<span data-ttu-id="47dd4-104">この ICorDebugStepper が現在ステップを実行しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="47dd4-104">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47dd4-105">構文</span><span class="sxs-lookup"><span data-stu-id="47dd4-105">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47dd4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47dd4-106">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="47dd4-107">入出力 `true` ステッパが現在ステップを実行している場合はを返します。それ以外の場合はを返し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="47dd4-107">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47dd4-108">解説</span><span class="sxs-lookup"><span data-stu-id="47dd4-108">Remarks</span></span>  

 <span data-ttu-id="47dd4-109">すべてのステップアクションは、デバッガーが完了していない場合は、次のように [実行](icordebugmanagedcallback-stepcomplete-method.md) されます。この呼び出しは、ステッパを自動的に非アクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="47dd4-109">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="47dd4-110">[ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md)を呼び出してコールバック条件に到達する前に、ステッパを途中で非アクティブにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="47dd4-110">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47dd4-111">要件</span><span class="sxs-lookup"><span data-stu-id="47dd4-111">Requirements</span></span>  

 <span data-ttu-id="47dd4-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47dd4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47dd4-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47dd4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47dd4-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47dd4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47dd4-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47dd4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
