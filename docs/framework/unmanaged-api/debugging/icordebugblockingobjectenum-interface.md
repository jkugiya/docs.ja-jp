---
description: 詳細については、「ICorDebugBlockingObjectEnum インターフェイス」を参照してください。
title: ICorDebugBlockingObjectEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
ms.openlocfilehash: 4f28039cb8a9bdcb376a9acf22572d29e41a2adf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754070"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="3936c-103">ICorDebugBlockingObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3936c-103">ICorDebugBlockingObjectEnum Interface</span></span>

<span data-ttu-id="3936c-104">[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体のリストの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="3936c-104">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="3936c-105">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="3936c-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3936c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3936c-106">Methods</span></span>  
  
|<span data-ttu-id="3936c-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="3936c-107">Method</span></span>|<span data-ttu-id="3936c-108">説明</span><span class="sxs-lookup"><span data-stu-id="3936c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3936c-109">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="3936c-109">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="3936c-110">[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体のリストを使用して列挙します。</span><span class="sxs-lookup"><span data-stu-id="3936c-110">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3936c-111">解説</span><span class="sxs-lookup"><span data-stu-id="3936c-111">Remarks</span></span>  

 <span data-ttu-id="3936c-112">各 `CorDebugBlockingObject` 構造体は、スレッドをブロックしているオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="3936c-112">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3936c-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3936c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3936c-114">要件</span><span class="sxs-lookup"><span data-stu-id="3936c-114">Requirements</span></span>  

 <span data-ttu-id="3936c-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3936c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3936c-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3936c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3936c-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3936c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3936c-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3936c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3936c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3936c-119">See also</span></span>

- [<span data-ttu-id="3936c-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3936c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3936c-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3936c-121">Debugging</span></span>](index.md)
