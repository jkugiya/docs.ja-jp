---
description: 詳細については、「ICorDebugProcess8 インターフェイス」を参照してください。
title: ICorDebugProcess8 インターフェイス
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
ms.openlocfilehash: d858470216cfe64c60902836e552f750f4b2d5ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691290"
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="d30cd-103">ICorDebugProcess8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d30cd-103">ICorDebugProcess8 Interface</span></span>

<span data-ttu-id="d30cd-104">[.NET Framework 4.6 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="d30cd-104">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="d30cd-105">ICorDebugManagedCallback2 Process インターフェイスを論理的に拡張して、特定の種類の[](icordebugmanagedcallback2-interface.md)例外コールバックを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="d30cd-105">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d30cd-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d30cd-106">Methods</span></span>  
  
|<span data-ttu-id="d30cd-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="d30cd-107">Method</span></span>|<span data-ttu-id="d30cd-108">説明</span><span class="sxs-lookup"><span data-stu-id="d30cd-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d30cd-109">EnableExceptionCallbacksOutsideOfMyCode メソッド</span><span class="sxs-lookup"><span data-stu-id="d30cd-109">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="d30cd-110">特定の種類の [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外コールバックを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="d30cd-110">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d30cd-111">解説</span><span class="sxs-lookup"><span data-stu-id="d30cd-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d30cd-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="d30cd-112">Requirements</span></span>  

 <span data-ttu-id="d30cd-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d30cd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d30cd-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d30cd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d30cd-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d30cd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d30cd-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d30cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d30cd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d30cd-117">See also</span></span>

- [<span data-ttu-id="d30cd-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d30cd-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d30cd-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="d30cd-119">Debugging</span></span>](index.md)
