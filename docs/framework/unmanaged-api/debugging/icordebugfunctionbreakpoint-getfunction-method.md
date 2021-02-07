---
description: 詳細については、次を参照
title: ICorDebugFunctionBreakpoint::GetFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetFunction
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetFunction method [.NET Framework debugging]
- GetFunction method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 2a62dae5-dd8a-4696-b817-0e1e586c24a0
topic_type:
- apiref
ms.openlocfilehash: 1e407acda81e5e6397da003a9b91a48d4d171e5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754096"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="817e0-103">ICorDebugFunctionBreakpoint::GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="817e0-103">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>

<span data-ttu-id="817e0-104">ブレークポイントが設定されている関数を参照する、のオブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="817e0-104">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="817e0-105">構文</span><span class="sxs-lookup"><span data-stu-id="817e0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="817e0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="817e0-106">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="817e0-107">入出力ブレークポイントが設定されている関数のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="817e0-107">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="817e0-108">要件</span><span class="sxs-lookup"><span data-stu-id="817e0-108">Requirements</span></span>  

 <span data-ttu-id="817e0-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="817e0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="817e0-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="817e0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="817e0-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="817e0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="817e0-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="817e0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
