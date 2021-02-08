---
description: '詳細については、次を参照してください: CreateThread メソッド'
title: ICorDebugManagedCallback::CreateThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 20d5ce9da34e7082502252eeece2ab34b1f2e902
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791033"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="56b77-103">ICorDebugManagedCallback::CreateThread メソッド</span><span class="sxs-lookup"><span data-stu-id="56b77-103">ICorDebugManagedCallback::CreateThread Method</span></span>

<span data-ttu-id="56b77-104">スレッドがマネージコードの実行を開始したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="56b77-104">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b77-105">構文</span><span class="sxs-lookup"><span data-stu-id="56b77-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56b77-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="56b77-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="56b77-107">からスレッドを含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="56b77-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="56b77-108">からスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="56b77-108">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56b77-109">解説</span><span class="sxs-lookup"><span data-stu-id="56b77-109">Remarks</span></span>  

 <span data-ttu-id="56b77-110">スレッドは、実行される最初のマネージコード命令に配置されます。</span><span class="sxs-lookup"><span data-stu-id="56b77-110">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56b77-111">要件</span><span class="sxs-lookup"><span data-stu-id="56b77-111">Requirements</span></span>  

 <span data-ttu-id="56b77-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56b77-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56b77-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56b77-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56b77-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56b77-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56b77-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56b77-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b77-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="56b77-116">See also</span></span>

- [<span data-ttu-id="56b77-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56b77-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
