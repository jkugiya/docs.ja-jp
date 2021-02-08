---
description: '詳細については、次を参照してください: いいね:: EnumerateBreakpoints メソッド'
title: ICorDebugAppDomain::EnumerateBreakpoints メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
ms.openlocfilehash: 4bd9857b9c662bc76c7c9481f306b20e823e446f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772466"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="ebb36-103">ICorDebugAppDomain::EnumerateBreakpoints メソッド</span><span class="sxs-lookup"><span data-stu-id="ebb36-103">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>

<span data-ttu-id="ebb36-104">アプリケーションドメイン内のすべてのアクティブなブレークポイントの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="ebb36-104">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebb36-105">構文</span><span class="sxs-lookup"><span data-stu-id="ebb36-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebb36-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ebb36-106">Parameters</span></span>  

 `ppBreakpoints`  
 <span data-ttu-id="ebb36-107">入出力アプリケーションドメイン内のすべてのアクティブなブレークポイントの列挙子である、の各オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ebb36-107">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebb36-108">解説</span><span class="sxs-lookup"><span data-stu-id="ebb36-108">Remarks</span></span>  

 <span data-ttu-id="ebb36-109">列挙子には、関数ブレークポイントやデータブレークポイントなど、すべての種類のブレークポイントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ebb36-109">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebb36-110">要件</span><span class="sxs-lookup"><span data-stu-id="ebb36-110">Requirements</span></span>  

 <span data-ttu-id="ebb36-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebb36-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebb36-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebb36-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebb36-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebb36-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebb36-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebb36-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
