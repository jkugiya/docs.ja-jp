---
description: '詳細については、次を参照してください: CorDebugBlockingReason 列挙型'
title: CorDebugBlockingReason 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
ms.openlocfilehash: c2d9c805549d046fe40ab5ea00f30e2fd0a680a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747106"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="e5edf-103">CorDebugBlockingReason 列挙体</span><span class="sxs-lookup"><span data-stu-id="e5edf-103">CorDebugBlockingReason Enumeration</span></span>

<span data-ttu-id="e5edf-104">指定されたオブジェクト上でスレッドがブロックされる理由を指定します。</span><span class="sxs-lookup"><span data-stu-id="e5edf-104">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5edf-105">構文</span><span class="sxs-lookup"><span data-stu-id="e5edf-105">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="e5edf-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e5edf-106">Members</span></span>  
  
|<span data-ttu-id="e5edf-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="e5edf-107">Member</span></span>|<span data-ttu-id="e5edf-108">説明</span><span class="sxs-lookup"><span data-stu-id="e5edf-108">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="e5edf-109">内部使用のみ。</span><span class="sxs-lookup"><span data-stu-id="e5edf-109">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="e5edf-110">スレッドが、オブジェクトのモニターロックに関連付けられているクリティカルセクションを取得しようとしています。</span><span class="sxs-lookup"><span data-stu-id="e5edf-110">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="e5edf-111">通常、このエラー <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> は、メソッドまたはメソッドのいずれかを呼び出すと発生し <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="e5edf-111">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="e5edf-112">スレッドが、オブジェクトのモニターロックに関連付けられているイベントを待機しています。</span><span class="sxs-lookup"><span data-stu-id="e5edf-112">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="e5edf-113">通常、これは、メソッドのいずれかを呼び出すと発生し <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` ます。</span><span class="sxs-lookup"><span data-stu-id="e5edf-113">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5edf-114">解説</span><span class="sxs-lookup"><span data-stu-id="e5edf-114">Remarks</span></span>  

 <span data-ttu-id="e5edf-115">`BLOCKING_MONITOR_CRITICAL_SECTION`メンバーまたは `BLOCKING_MONITOR_EVENT` メンバーが[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体で使用されている場合、 `pBlockingObject` 構造体のメンバーは、入力されるオブジェクトを表す "ICorDebugValue" インターフェイスを指します。</span><span class="sxs-lookup"><span data-stu-id="e5edf-115">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="e5edf-116">また、 [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) インターフェイスを実装することも保証されます。</span><span class="sxs-lookup"><span data-stu-id="e5edf-116">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5edf-117">要件</span><span class="sxs-lookup"><span data-stu-id="e5edf-117">Requirements</span></span>  

 <span data-ttu-id="e5edf-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5edf-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5edf-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5edf-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5edf-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5edf-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5edf-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5edf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5edf-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5edf-122">See also</span></span>

- [<span data-ttu-id="e5edf-123">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="e5edf-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="e5edf-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="e5edf-124">Debugging</span></span>](index.md)
