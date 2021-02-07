---
description: '詳細については、次を参照してください: Okframe:: CreateStepper メソッド'
title: ICorDebugFrame::CreateStepper メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
ms.openlocfilehash: 394418b89fd7a1c780a5bc33b97b8ef40bab8df2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693097"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="7ec26-103">ICorDebugFrame::CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="7ec26-103">ICorDebugFrame::CreateStepper Method</span></span>

<span data-ttu-id="7ec26-104">デバッガーがこのテキストフレームに対して相対的なステップ実行操作を実行できるようにするステッパを取得します。</span><span class="sxs-lookup"><span data-stu-id="7ec26-104">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec26-105">構文</span><span class="sxs-lookup"><span data-stu-id="7ec26-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ec26-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7ec26-106">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="7ec26-107">入出力デバッガーが現在のフレームに対して相対的なステップ実行操作を実行できるようにする ICorDebugStepper オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7ec26-107">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ec26-108">解説</span><span class="sxs-lookup"><span data-stu-id="7ec26-108">Remarks</span></span>  

 <span data-ttu-id="7ec26-109">フレームがアクティブでない場合、通常、ステッパオブジェクトは、手順が完了する前にフレームに戻る必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ec26-109">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ec26-110">要件</span><span class="sxs-lookup"><span data-stu-id="7ec26-110">Requirements</span></span>  

 <span data-ttu-id="7ec26-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ec26-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ec26-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ec26-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ec26-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ec26-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ec26-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ec26-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
