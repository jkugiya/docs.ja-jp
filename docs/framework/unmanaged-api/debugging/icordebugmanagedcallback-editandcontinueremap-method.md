---
description: 詳細については、次の情報を参照
title: ICorDebugManagedCallback::EditAndContinueRemap メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
ms.openlocfilehash: ad8932e41236cdb8ed213024efb4175292a5d5f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791007"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="f6d77-103">ICorDebugManagedCallback::EditAndContinueRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="f6d77-103">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>

<span data-ttu-id="f6d77-104">このメソッドの使用は非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="f6d77-104">This method has been deprecated.</span></span> <span data-ttu-id="f6d77-105">これは、マップイベントが統合開発環境 (IDE) に送信されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f6d77-105">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6d77-106">構文</span><span class="sxs-lookup"><span data-stu-id="f6d77-106">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="f6d77-107">解説</span><span class="sxs-lookup"><span data-stu-id="f6d77-107">Remarks</span></span>  

 <span data-ttu-id="f6d77-108">更新された `EditAndContinueRemap` 関数の古いバージョンでコードを実行しようとすると、メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f6d77-108">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="f6d77-109">共通言語ランタイムは、メソッドを呼び出して、 `EditAndContinueRemap` リマップイベントを IDE に送信します。</span><span class="sxs-lookup"><span data-stu-id="f6d77-109">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6d77-110">要件</span><span class="sxs-lookup"><span data-stu-id="f6d77-110">Requirements</span></span>  

 <span data-ttu-id="f6d77-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6d77-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6d77-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6d77-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6d77-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6d77-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6d77-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6d77-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d77-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6d77-115">See also</span></span>

- [<span data-ttu-id="f6d77-116">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6d77-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
