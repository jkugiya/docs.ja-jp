---
description: '詳細については、次のページを参照してください: モジュールのブレークポイント:: GetModule メソッド'
title: ICorDebugModuleBreakpoint::GetModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type:
- apiref
ms.openlocfilehash: 3498f9d644d6195f2cd0f83d30417c447d200f3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790790"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="eb8c8-103">ICorDebugModuleBreakpoint::GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="eb8c8-103">ICorDebugModuleBreakpoint::GetModule Method</span></span>

<span data-ttu-id="eb8c8-104">このブレークポイントが設定されているモジュールを参照する "ツールモジュール" へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="eb8c8-104">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb8c8-105">構文</span><span class="sxs-lookup"><span data-stu-id="eb8c8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb8c8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb8c8-106">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="eb8c8-107">入出力 `ICorDebugModule` ブレークポイントが設定されているモジュールを参照するインターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eb8c8-107">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb8c8-108">要件</span><span class="sxs-lookup"><span data-stu-id="eb8c8-108">Requirements</span></span>  

 <span data-ttu-id="eb8c8-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb8c8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb8c8-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb8c8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb8c8-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb8c8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb8c8-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb8c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb8c8-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb8c8-113">See also</span></span>
