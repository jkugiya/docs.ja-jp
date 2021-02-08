---
description: 詳細については、「ICorDebugManagedCallback3 インターフェイス」を参照してください。
title: ICorDebugManagedCallback3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: 9fb3d44b1d793935ac997e8e4d8d86de4466f7b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801190"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="cc7cb-103">ICorDebugManagedCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc7cb-103">ICorDebugManagedCallback3 Interface</span></span>

<span data-ttu-id="cc7cb-104">有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="cc7cb-104">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc7cb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cc7cb-105">Methods</span></span>  
  
|<span data-ttu-id="cc7cb-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cc7cb-106">Method</span></span>|<span data-ttu-id="cc7cb-107">説明</span><span class="sxs-lookup"><span data-stu-id="cc7cb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc7cb-108">CustomNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="cc7cb-108">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="cc7cb-109">有効なカスタムデバッガー通知が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="cc7cb-109">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc7cb-110">解説</span><span class="sxs-lookup"><span data-stu-id="cc7cb-110">Remarks</span></span>  

 <span data-ttu-id="cc7cb-111">このインターフェイスは、" [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) [" というインターフェイスを論理的](icordebugmanagedcallback-interface.md)に拡張したものです。</span><span class="sxs-lookup"><span data-stu-id="cc7cb-111">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc7cb-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cc7cb-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc7cb-113">要件</span><span class="sxs-lookup"><span data-stu-id="cc7cb-113">Requirements</span></span>  

 <span data-ttu-id="cc7cb-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc7cb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc7cb-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc7cb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc7cb-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc7cb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc7cb-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc7cb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7cb-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc7cb-118">See also</span></span>

- [<span data-ttu-id="cc7cb-119">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc7cb-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="cc7cb-120">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc7cb-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="cc7cb-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc7cb-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cc7cb-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="cc7cb-122">Debugging</span></span>](index.md)
