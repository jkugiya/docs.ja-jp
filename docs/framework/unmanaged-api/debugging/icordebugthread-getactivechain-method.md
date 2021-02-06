---
description: 詳細については、次を参照してください
title: ICorDebugThread::GetActiveChain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
ms.openlocfilehash: d9aff80801fa72a227a84b3b5216e3ffa72b0e24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659284"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="14dcc-103">ICorDebugThread::GetActiveChain メソッド</span><span class="sxs-lookup"><span data-stu-id="14dcc-103">ICorDebugThread::GetActiveChain Method</span></span>

<span data-ttu-id="14dcc-104">このスレッドオブジェクトのアクティブな (最新の) スタックチェーンへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="14dcc-104">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14dcc-105">構文</span><span class="sxs-lookup"><span data-stu-id="14dcc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14dcc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="14dcc-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="14dcc-107">入出力スタックチェーンを表す、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="14dcc-107">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14dcc-108">解説</span><span class="sxs-lookup"><span data-stu-id="14dcc-108">Remarks</span></span>  

 <span data-ttu-id="14dcc-109">`ppChain`現在アクティブになっているスタックチェーンがない場合、パラメーターは null になります。</span><span class="sxs-lookup"><span data-stu-id="14dcc-109">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14dcc-110">要件</span><span class="sxs-lookup"><span data-stu-id="14dcc-110">Requirements</span></span>  

 <span data-ttu-id="14dcc-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14dcc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14dcc-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14dcc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14dcc-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14dcc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14dcc-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14dcc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
