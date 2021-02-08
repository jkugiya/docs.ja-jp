---
description: 詳細については、次のページを参照してください
title: ICorDebugManagedCallback::ExitAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
ms.openlocfilehash: a08f29c6c4c8196b968118433c31afb715935aec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803621"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="7985b-103">ICorDebugManagedCallback::ExitAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="7985b-103">ICorDebugManagedCallback::ExitAppDomain Method</span></span>

<span data-ttu-id="7985b-104">アプリケーションドメインが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7985b-104">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7985b-105">構文</span><span class="sxs-lookup"><span data-stu-id="7985b-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7985b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7985b-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="7985b-107">から指定されたアプリケーションドメインを含むプロセスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7985b-107">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="7985b-108">から終了したアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7985b-108">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7985b-109">要件</span><span class="sxs-lookup"><span data-stu-id="7985b-109">Requirements</span></span>  

 <span data-ttu-id="7985b-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7985b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7985b-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7985b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7985b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7985b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7985b-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7985b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7985b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7985b-114">See also</span></span>

- [<span data-ttu-id="7985b-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7985b-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
