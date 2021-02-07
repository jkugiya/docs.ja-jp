---
description: '詳細については、次を参照してください: GetOffset メソッド'
title: ICorDebugFunctionBreakpoint::GetOffset メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetOffset
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: e619eae4-3ac3-4c37-bba4-55e59989b9cb
topic_type:
- apiref
ms.openlocfilehash: 94238b761e0a42a72037f7d44d5e9609f86ac03b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661169"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="c5e4a-103">ICorDebugFunctionBreakpoint::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="c5e4a-103">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>

<span data-ttu-id="c5e4a-104">関数内のブレークポイントのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="c5e4a-104">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5e4a-105">構文</span><span class="sxs-lookup"><span data-stu-id="c5e4a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5e4a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5e4a-106">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="c5e4a-107">入出力ブレークポイントのオフセットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c5e4a-107">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5e4a-108">要件</span><span class="sxs-lookup"><span data-stu-id="c5e4a-108">Requirements</span></span>  

 <span data-ttu-id="c5e4a-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5e4a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5e4a-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5e4a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5e4a-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5e4a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5e4a-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5e4a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
