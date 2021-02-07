---
description: '詳細情報: ICorDebugBreakpoint:: Activate メソッド'
title: ICorDebugBreakpoint::Activate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
ms.openlocfilehash: 1a3613ae071b3fc6c4f1005eafd515946d6b2685
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711868"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="1a653-103">ICorDebugBreakpoint::Activate メソッド</span><span class="sxs-lookup"><span data-stu-id="1a653-103">ICorDebugBreakpoint::Activate Method</span></span>

<span data-ttu-id="1a653-104">こののアクティブな状態を設定 `ICorDebugBreakpoint` します。</span><span class="sxs-lookup"><span data-stu-id="1a653-104">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a653-105">構文</span><span class="sxs-lookup"><span data-stu-id="1a653-105">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a653-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1a653-106">Parameters</span></span>  

 `bActive`  
 <span data-ttu-id="1a653-107">から状態をアクティブとして指定するには、この値をに設定します。 `true` それ以外の場合は、この値をに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="1a653-107">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a653-108">要件</span><span class="sxs-lookup"><span data-stu-id="1a653-108">Requirements</span></span>  

 <span data-ttu-id="1a653-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a653-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a653-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a653-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a653-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a653-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a653-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a653-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
