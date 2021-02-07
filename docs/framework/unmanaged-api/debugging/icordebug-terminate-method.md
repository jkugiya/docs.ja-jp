---
description: '詳細情報: ICorDebug:: Terminate メソッド'
title: ICorDebug::Terminate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: c2de27a47bfd4c364a09180c75109679234f3cae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754291"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="7b20b-103">ICorDebug::Terminate メソッド</span><span class="sxs-lookup"><span data-stu-id="7b20b-103">ICorDebug::Terminate Method</span></span>

<span data-ttu-id="7b20b-104">オブジェクトを終了 `ICorDebug` します。</span><span class="sxs-lookup"><span data-stu-id="7b20b-104">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b20b-105">`Terminate` デバッグされているすべてのプロセスに対して、 [ExitProcess Callback callback::](icordebugmanagedcallback-exitprocess-method.md) callback が受信されるまでは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="7b20b-105">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b20b-106">構文</span><span class="sxs-lookup"><span data-stu-id="7b20b-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7b20b-107">解説</span><span class="sxs-lookup"><span data-stu-id="7b20b-107">Remarks</span></span>  

 <span data-ttu-id="7b20b-108">`Terminate` オブジェクトが不要になった場合は、を呼び出す必要があり `ICorDebug` ます。</span><span class="sxs-lookup"><span data-stu-id="7b20b-108">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b20b-109">要件</span><span class="sxs-lookup"><span data-stu-id="7b20b-109">Requirements</span></span>  

 <span data-ttu-id="7b20b-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b20b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b20b-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b20b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b20b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b20b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b20b-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b20b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b20b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b20b-114">See also</span></span>

- [<span data-ttu-id="7b20b-115">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b20b-115">ICorDebug Interface</span></span>](icordebug-interface.md)
