---
description: '詳細情報: テキストスレッド:: GetActiveFrame メソッド'
title: ICorDebugThread::GetActiveFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
ms.openlocfilehash: 3b15aad39503dfec9ac8f98f839ee1a6b16b3f90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659258"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="e5bf7-103">ICorDebugThread::GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="e5bf7-103">ICorDebugThread::GetActiveFrame Method</span></span>

<span data-ttu-id="e5bf7-104">このテキストスレッドオブジェクトのアクティブな (最新の) フレームへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="e5bf7-104">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5bf7-105">構文</span><span class="sxs-lookup"><span data-stu-id="e5bf7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5bf7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e5bf7-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="e5bf7-107">入出力フレームを表す、テキストフレームインターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e5bf7-107">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5bf7-108">解説</span><span class="sxs-lookup"><span data-stu-id="e5bf7-108">Remarks</span></span>  

 <span data-ttu-id="e5bf7-109">`ppFrame`現在アクティブなフレームがない場合、パラメーターは null になります。</span><span class="sxs-lookup"><span data-stu-id="e5bf7-109">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5bf7-110">要件</span><span class="sxs-lookup"><span data-stu-id="e5bf7-110">Requirements</span></span>  

 <span data-ttu-id="e5bf7-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5bf7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5bf7-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5bf7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5bf7-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5bf7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5bf7-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5bf7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
