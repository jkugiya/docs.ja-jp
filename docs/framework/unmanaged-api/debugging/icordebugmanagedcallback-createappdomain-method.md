---
description: '詳細については、次の情報を参照してください: ICorDebugManagedCallback:: CreateAppDomain メソッド'
title: ICorDebugManagedCallback::CreateAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
ms.openlocfilehash: 5f4aa49ce90e8ec1343794db71ae3aa911c9e09f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791073"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="f018e-103">ICorDebugManagedCallback::CreateAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="f018e-103">ICorDebugManagedCallback::CreateAppDomain Method</span></span>

<span data-ttu-id="f018e-104">アプリケーションドメインが作成されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f018e-104">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f018e-105">構文</span><span class="sxs-lookup"><span data-stu-id="f018e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f018e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f018e-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="f018e-107">からアプリケーションドメインが作成されたプロセスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f018e-107">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="f018e-108">から作成されたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f018e-108">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f018e-109">要件</span><span class="sxs-lookup"><span data-stu-id="f018e-109">Requirements</span></span>  

 <span data-ttu-id="f018e-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f018e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f018e-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f018e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f018e-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f018e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f018e-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f018e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f018e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f018e-114">See also</span></span>

- [<span data-ttu-id="f018e-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f018e-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
