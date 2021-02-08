---
description: 詳細については、「CorDebugSetContextFlag 列挙型」を参照してください。
title: CorDebugSetContextFlag 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
ms.openlocfilehash: 625f24e516ff462cf3d0e628dfff6c08793807ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801554"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="b29ec-103">CorDebugSetContextFlag 列挙体</span><span class="sxs-lookup"><span data-stu-id="b29ec-103">CorDebugSetContextFlag Enumeration</span></span>

<span data-ttu-id="b29ec-104">スタック上のアクティブ (またはリーフ) フレーム上からのコンテキストなのか、別のフレームからのアンワインドにより計算されたコンテキストなのかを示します。</span><span class="sxs-lookup"><span data-stu-id="b29ec-104">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b29ec-105">構文</span><span class="sxs-lookup"><span data-stu-id="b29ec-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="b29ec-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b29ec-106">Members</span></span>  
  
|<span data-ttu-id="b29ec-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b29ec-107">Member</span></span>|<span data-ttu-id="b29ec-108">説明</span><span class="sxs-lookup"><span data-stu-id="b29ec-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b29ec-109">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="b29ec-109">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="b29ec-110">コンテキストは、スレッドのアクティブなコンテキストです。</span><span class="sxs-lookup"><span data-stu-id="b29ec-110">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="b29ec-111">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="b29ec-111">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="b29ec-112">コンテキストは、別のフレームからのアンワインドによって計算されています。</span><span class="sxs-lookup"><span data-stu-id="b29ec-112">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b29ec-113">解説</span><span class="sxs-lookup"><span data-stu-id="b29ec-113">Remarks</span></span>  

 <span data-ttu-id="b29ec-114">`CorDebugSetContextFlag` によって使用される値を提供する、には、「 [SetContext](icordebugstackwalk-setcontext-method.md) メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b29ec-114">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b29ec-115">要件</span><span class="sxs-lookup"><span data-stu-id="b29ec-115">Requirements</span></span>  

 <span data-ttu-id="b29ec-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b29ec-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b29ec-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b29ec-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b29ec-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b29ec-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b29ec-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b29ec-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29ec-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b29ec-120">See also</span></span>

- [<span data-ttu-id="b29ec-121">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="b29ec-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="b29ec-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b29ec-122">Debugging</span></span>](index.md)
