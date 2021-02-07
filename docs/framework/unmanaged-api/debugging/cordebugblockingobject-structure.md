---
description: '詳細については、次を参照してください: CorDebugBlockingObject 構造体'
title: CorDebugBlockingObject 構造体
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
ms.openlocfilehash: 2b16af5eecb01067c2ee6811613f964af391f345
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712220"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="29799-103">CorDebugBlockingObject 構造体</span><span class="sxs-lookup"><span data-stu-id="29799-103">CorDebugBlockingObject Structure</span></span>

<span data-ttu-id="29799-104">スレッドをブロックしているオブジェクトと、スレッドがブロックされている具体的な理由を定義します。</span><span class="sxs-lookup"><span data-stu-id="29799-104">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29799-105">構文</span><span class="sxs-lookup"><span data-stu-id="29799-105">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="29799-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="29799-106">Members</span></span>  
  
|<span data-ttu-id="29799-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="29799-107">Member</span></span>|<span data-ttu-id="29799-108">説明</span><span class="sxs-lookup"><span data-stu-id="29799-108">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="29799-109">スレッドがブロックされているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="29799-109">The object on which the thread is blocking.</span></span> <span data-ttu-id="29799-110">このオブジェクトは、現在の同期済みの状態の間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="29799-110">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="29799-111">2つのスレッドが同じ同期状態内の同じオブジェクトでブロックしている場合は、 [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) メソッドで同じ値が返されることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="29799-111">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="29799-112">ただし、インターフェイスは、同等のポインターである場合とない場合があります。</span><span class="sxs-lookup"><span data-stu-id="29799-112">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="29799-113">ブロッキング操作がタイムアウトするまでのミリ秒数。または、タイムアウトしないことを示す値が無限であることを示します。タイムアウト値は、残りの時間ではなく、ブロック操作の合計時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="29799-113">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="29799-114">このオブジェクトでスレッドがブロックされた理由。</span><span class="sxs-lookup"><span data-stu-id="29799-114">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29799-115">解説</span><span class="sxs-lookup"><span data-stu-id="29799-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29799-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="29799-116">Requirements</span></span>  

 <span data-ttu-id="29799-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29799-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29799-118">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="29799-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="29799-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29799-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29799-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29799-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29799-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="29799-121">See also</span></span>

- [<span data-ttu-id="29799-122">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="29799-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="29799-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="29799-123">Debugging</span></span>](index.md)
