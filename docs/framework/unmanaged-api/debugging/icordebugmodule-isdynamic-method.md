---
description: '詳細情報: ヘルプモジュール:: IsDynamic メソッド'
title: ICorDebugModule::IsDynamic メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 06ecb7aaffbe73da29bbdbba9446839db54c58c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660103"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="12a3f-103">ICorDebugModule::IsDynamic メソッド</span><span class="sxs-lookup"><span data-stu-id="12a3f-103">ICorDebugModule::IsDynamic Method</span></span>

<span data-ttu-id="12a3f-104">このモジュールが動的かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="12a3f-104">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a3f-105">構文</span><span class="sxs-lookup"><span data-stu-id="12a3f-105">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12a3f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12a3f-106">Parameters</span></span>  

 `pDynamic`  
 <span data-ttu-id="12a3f-107">[出力] `true` このモジュールが動的である場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="12a3f-107">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12a3f-108">解説</span><span class="sxs-lookup"><span data-stu-id="12a3f-108">Remarks</span></span>  

 <span data-ttu-id="12a3f-109">動的モジュールは、モジュールが読み込まれた後でも、新しいクラスを追加したり、既存のクラスを削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="12a3f-109">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="12a3f-110">は、クラスが追加または削除されたときに、 [UnloadClass](icordebugmanagedcallback-unloadclass-method.md) [Callback:: loadclass](icordebugmanagedcallback-loadclass-method.md)コールバックとによって、デバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="12a3f-110">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12a3f-111">要件</span><span class="sxs-lookup"><span data-stu-id="12a3f-111">Requirements</span></span>  

 <span data-ttu-id="12a3f-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12a3f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12a3f-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12a3f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12a3f-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12a3f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12a3f-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12a3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
