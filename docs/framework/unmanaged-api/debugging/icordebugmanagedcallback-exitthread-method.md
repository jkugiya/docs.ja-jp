---
description: 詳細については、次を参照
title: ICorDebugManagedCallback::ExitThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: 4c9472d6377246833c7c30f072549da9c44f05d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790946"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="fa486-103">ICorDebugManagedCallback::ExitThread メソッド</span><span class="sxs-lookup"><span data-stu-id="fa486-103">ICorDebugManagedCallback::ExitThread Method</span></span>

<span data-ttu-id="fa486-104">マネージコードを実行していたスレッドが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="fa486-104">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa486-105">構文</span><span class="sxs-lookup"><span data-stu-id="fa486-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa486-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fa486-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="fa486-107">からマネージスレッドを含むアプリケーションドメインを表す、コードの Appdomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fa486-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="fa486-108">からマネージスレッドを表す、コードスレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fa486-108">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa486-109">解説</span><span class="sxs-lookup"><span data-stu-id="fa486-109">Remarks</span></span>  

 <span data-ttu-id="fa486-110">`ExitThread`コールバックが発生すると、スレッドはスレッド列挙に表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="fa486-110">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa486-111">要件</span><span class="sxs-lookup"><span data-stu-id="fa486-111">Requirements</span></span>  

 <span data-ttu-id="fa486-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa486-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa486-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa486-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa486-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa486-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa486-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa486-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa486-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa486-116">See also</span></span>

- [<span data-ttu-id="fa486-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa486-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
