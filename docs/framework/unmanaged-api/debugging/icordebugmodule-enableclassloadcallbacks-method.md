---
description: '詳細については、「EnableClassLoadCallbacks Module:: メソッド」を参照してください。'
title: ICorDebugModule::EnableClassLoadCallbacks メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: 16516cceae9a10288f8660fa69d8e0c018953777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801086"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="dfa35-103">ICorDebugModule::EnableClassLoadCallbacks メソッド</span><span class="sxs-lookup"><span data-stu-id="dfa35-103">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>

<span data-ttu-id="dfa35-104">このモジュールに対して、" [UnloadClass](icordebugmanagedcallback-unloadclass-method.md) " コール[バック:: loadclass](icordebugmanagedcallback-loadclass-method.md)との各コールバックを呼び出すかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="dfa35-104">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa35-105">構文</span><span class="sxs-lookup"><span data-stu-id="dfa35-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfa35-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dfa35-106">Parameters</span></span>  

 `bClassLoadCallbacks`  
 <span data-ttu-id="dfa35-107">からこの値をに設定する `true` と、共通言語ランタイム (CLR) が、 `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` 関連付けられたイベントが発生したときにメソッドとメソッドを呼び出すことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="dfa35-107">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="dfa35-108">既定値は `false` 非動的モジュールの場合はです。</span><span class="sxs-lookup"><span data-stu-id="dfa35-108">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="dfa35-109">値は、動的モジュールの場合は常にであり `true` 、変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="dfa35-109">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfa35-110">解説</span><span class="sxs-lookup"><span data-stu-id="dfa35-110">Remarks</span></span>  

 <span data-ttu-id="dfa35-111">`ICorDebugManagedCallback::LoadClass`および `ICorDebugManagedCallback::UnloadClass` コールバックは動的モジュールに対して常に有効であり、無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="dfa35-111">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa35-112">要件</span><span class="sxs-lookup"><span data-stu-id="dfa35-112">Requirements</span></span>  

 <span data-ttu-id="dfa35-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfa35-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa35-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfa35-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfa35-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfa35-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfa35-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa35-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa35-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfa35-117">See also</span></span>
