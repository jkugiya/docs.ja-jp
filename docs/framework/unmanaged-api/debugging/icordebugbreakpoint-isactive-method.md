---
description: '詳細について: ICorDebugBreakpoint:: IsActive メソッド'
title: ICorDebugBreakpoint::IsActive メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type:
- apiref
ms.openlocfilehash: 49e98ccc3722c37b3ff5968215ef3f658601ea10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711792"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="48755-103">ICorDebugBreakpoint::IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="48755-103">ICorDebugBreakpoint::IsActive Method</span></span>

<span data-ttu-id="48755-104">このがアクティブかどうかを示す値を取得し `ICorDebugBreakpoint` ます。</span><span class="sxs-lookup"><span data-stu-id="48755-104">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48755-105">構文</span><span class="sxs-lookup"><span data-stu-id="48755-105">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48755-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48755-106">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="48755-107">[出力] `true` このブレークポイントがアクティブである場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="48755-107">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48755-108">要件</span><span class="sxs-lookup"><span data-stu-id="48755-108">Requirements</span></span>  

 <span data-ttu-id="48755-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48755-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48755-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48755-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48755-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48755-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48755-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48755-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
