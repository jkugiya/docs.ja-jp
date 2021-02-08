---
description: 詳細については、「ICorDebugThread4 インターフェイス」を参照してください。
title: ICorDebugThread4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 4ad587cee81ce635df0a8917b7a6d68e60aaf0b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800917"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="5f9ff-103">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f9ff-103">ICorDebugThread4 Interface</span></span>

<span data-ttu-id="5f9ff-104">スレッドのブロック情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5f9ff-104">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f9ff-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5f9ff-105">Methods</span></span>  
  
|<span data-ttu-id="5f9ff-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5f9ff-106">Method</span></span>|<span data-ttu-id="5f9ff-107">説明</span><span class="sxs-lookup"><span data-stu-id="5f9ff-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f9ff-108">GetBlockingObjects メソッド</span><span class="sxs-lookup"><span data-stu-id="5f9ff-108">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="5f9ff-109">スレッドブロック情報を提供する [CorDebugBlockingObject](cordebugblockingobject-structure.md) 構造体の順序付けられた列挙体を提供します。</span><span class="sxs-lookup"><span data-stu-id="5f9ff-109">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="5f9ff-110">HadUnhandledException メソッド</span><span class="sxs-lookup"><span data-stu-id="5f9ff-110">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="5f9ff-111">スレッドで未処理の例外が発生したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5f9ff-111">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="5f9ff-112">GetCurrentCustomDebuggerNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="5f9ff-112">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="5f9ff-113">現在のスレッドの現在の [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="5f9ff-113">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f9ff-114">解説</span><span class="sxs-lookup"><span data-stu-id="5f9ff-114">Remarks</span></span>  

 <span data-ttu-id="5f9ff-115">このインターフェイスは、ICorDebugThread2、 [ICorDebugThread3](icordebugthread3-interface.md) の各インターフェイスの論理的な拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="5f9ff-115">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f9ff-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5f9ff-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f9ff-117">要件</span><span class="sxs-lookup"><span data-stu-id="5f9ff-117">Requirements</span></span>  

 <span data-ttu-id="5f9ff-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f9ff-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f9ff-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f9ff-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f9ff-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f9ff-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f9ff-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f9ff-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9ff-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f9ff-122">See also</span></span>

- [<span data-ttu-id="5f9ff-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f9ff-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5f9ff-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="5f9ff-124">Debugging</span></span>](index.md)
