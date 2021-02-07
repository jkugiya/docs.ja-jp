---
description: 詳細については、「CorDebugIntercept 列挙型」を参照してください。
title: CorDebugIntercept 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: ddd17aff309396fdcda37c731ff907224ee17db2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661975"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="474cb-103">CorDebugIntercept 列挙型</span><span class="sxs-lookup"><span data-stu-id="474cb-103">CorDebugIntercept Enumeration</span></span>

<span data-ttu-id="474cb-104">インターセプト (ステップ イン) できるコードの型を示します。</span><span class="sxs-lookup"><span data-stu-id="474cb-104">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="474cb-105">構文</span><span class="sxs-lookup"><span data-stu-id="474cb-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="474cb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="474cb-106">Members</span></span>  
  
|<span data-ttu-id="474cb-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="474cb-107">Member</span></span>|<span data-ttu-id="474cb-108">説明</span><span class="sxs-lookup"><span data-stu-id="474cb-108">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="474cb-109">インターセプトできるコードはありません。</span><span class="sxs-lookup"><span data-stu-id="474cb-109">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="474cb-110">コンストラクターをインターセプトできます。</span><span class="sxs-lookup"><span data-stu-id="474cb-110">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="474cb-111">例外フィルターをインターセプトできます。</span><span class="sxs-lookup"><span data-stu-id="474cb-111">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="474cb-112">セキュリティを適用するコードをインターセプトできます。</span><span class="sxs-lookup"><span data-stu-id="474cb-112">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="474cb-113">コンテキスト ポリシーをインターセプトできます。</span><span class="sxs-lookup"><span data-stu-id="474cb-113">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="474cb-114">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="474cb-114">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="474cb-115">すべてのコードをインターセプトできます。</span><span class="sxs-lookup"><span data-stu-id="474cb-115">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="474cb-116">解説</span><span class="sxs-lookup"><span data-stu-id="474cb-116">Remarks</span></span>  

 <span data-ttu-id="474cb-117">インターセプトできるコードの型を確立するには、 [ICorDebugStepper:: SetInterceptMask](icordebugstepper-setinterceptmask-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="474cb-117">Use the [ICorDebugStepper::SetInterceptMask](icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="474cb-118">要件</span><span class="sxs-lookup"><span data-stu-id="474cb-118">Requirements</span></span>  

 <span data-ttu-id="474cb-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="474cb-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="474cb-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="474cb-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="474cb-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="474cb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="474cb-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="474cb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="474cb-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="474cb-123">See also</span></span>

- [<span data-ttu-id="474cb-124">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="474cb-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
