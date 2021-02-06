---
description: '詳細については、次の情報を参照してください:: echange Managedcallback:: NameChange メソッド'
title: ICorDebugManagedCallback::NameChange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 5f337f5e05b80c97e8b8e48f8b7bc76b3232b2c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660415"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="33156-103">ICorDebugManagedCallback::NameChange メソッド</span><span class="sxs-lookup"><span data-stu-id="33156-103">ICorDebugManagedCallback::NameChange Method</span></span>

<span data-ttu-id="33156-104">アプリケーションドメインまたはスレッドの名前が変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="33156-104">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33156-105">構文</span><span class="sxs-lookup"><span data-stu-id="33156-105">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33156-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="33156-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="33156-107">から名前が変更されたか、または名前の変更があったスレッドを含むアプリケーションドメインを表す、ツールオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="33156-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="33156-108">から名前の変更があったスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="33156-108">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33156-109">要件</span><span class="sxs-lookup"><span data-stu-id="33156-109">Requirements</span></span>  

 <span data-ttu-id="33156-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33156-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33156-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33156-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33156-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33156-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33156-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33156-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33156-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="33156-114">See also</span></span>

- [<span data-ttu-id="33156-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="33156-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
