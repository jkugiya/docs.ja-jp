---
description: '詳細については、次のページを参照してください: いいでしょう:: GetThread メソッド'
title: ICorDebugChain::GetThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
ms.openlocfilehash: 090cb40c3681792ce4a30cd342e65dc02ac3f381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694921"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="4915c-103">ICorDebugChain::GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="4915c-103">ICorDebugChain::GetThread Method</span></span>

<span data-ttu-id="4915c-104">この呼び出しチェーンが含まれている物理スレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="4915c-104">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4915c-105">構文</span><span class="sxs-lookup"><span data-stu-id="4915c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4915c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4915c-106">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="4915c-107">入出力この呼び出しチェーンが含まれている物理スレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4915c-107">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4915c-108">要件</span><span class="sxs-lookup"><span data-stu-id="4915c-108">Requirements</span></span>  

 <span data-ttu-id="4915c-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4915c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4915c-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4915c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4915c-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4915c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4915c-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4915c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
