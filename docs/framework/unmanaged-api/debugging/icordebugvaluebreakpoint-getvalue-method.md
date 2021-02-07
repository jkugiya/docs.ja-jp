---
description: 詳細については、次を参照
title: ICorDebugValueBreakpoint::GetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugValueBreakpoint interface [.NET Framework debugging]
- ICorDebugValueBreakpoint::GetValue method [.NET Framework debugging]
ms.assetid: 52a73654-bc47-48b6-b2b1-a4456b10140c
topic_type:
- apiref
ms.openlocfilehash: b690ea7a39ac70edd8e3e6be7682bae1e808555d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690172"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="3ecfe-103">ICorDebugValueBreakpoint::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="3ecfe-103">ICorDebugValueBreakpoint::GetValue Method</span></span>

<span data-ttu-id="3ecfe-104">ブレークポイントが設定されているオブジェクトの値を表す "ICorDebugValue" オブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="3ecfe-104">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ecfe-105">構文</span><span class="sxs-lookup"><span data-stu-id="3ecfe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ecfe-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3ecfe-106">Parameters</span></span>  

 `ppValue`  
 <span data-ttu-id="3ecfe-107">入出力オブジェクトのアドレスへのポインター `ICorDebugValue` 。</span><span class="sxs-lookup"><span data-stu-id="3ecfe-107">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ecfe-108">要件</span><span class="sxs-lookup"><span data-stu-id="3ecfe-108">Requirements</span></span>  

 <span data-ttu-id="3ecfe-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ecfe-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ecfe-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ecfe-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ecfe-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ecfe-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ecfe-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ecfe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ecfe-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ecfe-113">See also</span></span>
