---
description: '詳細について: ICorDebugStepper::D eactivate メソッド'
title: ICorDebugStepper::Deactivate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
ms.openlocfilehash: 039c52f5bc237506dcc648ace70789c8eb7ef8c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794664"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="b3363-103">ICorDebugStepper::Deactivate メソッド</span><span class="sxs-lookup"><span data-stu-id="b3363-103">ICorDebugStepper::Deactivate Method</span></span>

<span data-ttu-id="b3363-104">この ICorDebugStepper は、受け取った最後のステップコマンドをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="b3363-104">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3363-105">構文</span><span class="sxs-lookup"><span data-stu-id="b3363-105">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b3363-106">解説</span><span class="sxs-lookup"><span data-stu-id="b3363-106">Remarks</span></span>  

 <span data-ttu-id="b3363-107">最後に受信したステップコマンドが取り消された後に、新しいステップ実行コマンドが発行される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3363-107">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3363-108">要件</span><span class="sxs-lookup"><span data-stu-id="b3363-108">Requirements</span></span>  

 <span data-ttu-id="b3363-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3363-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3363-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3363-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3363-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3363-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3363-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3363-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
