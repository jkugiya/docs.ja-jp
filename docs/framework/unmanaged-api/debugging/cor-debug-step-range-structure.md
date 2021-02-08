---
description: '詳細情報: COR_DEBUG_STEP_RANGE 構造'
title: COR_DEBUG_STEP_RANGE 構造体
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
ms.openlocfilehash: 40462be4b165351b3265fa0833d19f18e0fa3a37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801840"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="1ca4f-103">COR_DEBUG_STEP_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="1ca4f-103">COR_DEBUG_STEP_RANGE Structure</span></span>

<span data-ttu-id="1ca4f-104">コードの範囲に関するオフセット情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1ca4f-104">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="1ca4f-105">この構造体は、 [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="1ca4f-105">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ca4f-106">構文</span><span class="sxs-lookup"><span data-stu-id="1ca4f-106">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="1ca4f-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="1ca4f-107">Members</span></span>  
  
|<span data-ttu-id="1ca4f-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="1ca4f-108">Member</span></span>|<span data-ttu-id="1ca4f-109">説明</span><span class="sxs-lookup"><span data-stu-id="1ca4f-109">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="1ca4f-110">範囲の先頭のオフセット。</span><span class="sxs-lookup"><span data-stu-id="1ca4f-110">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="1ca4f-111">範囲の末尾のオフセット。</span><span class="sxs-lookup"><span data-stu-id="1ca4f-111">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ca4f-112">要件</span><span class="sxs-lookup"><span data-stu-id="1ca4f-112">Requirements</span></span>  

 <span data-ttu-id="1ca4f-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ca4f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ca4f-114">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="1ca4f-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="1ca4f-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ca4f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ca4f-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ca4f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca4f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ca4f-117">See also</span></span>

- [<span data-ttu-id="1ca4f-118">StepRange メソッド</span><span class="sxs-lookup"><span data-stu-id="1ca4f-118">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="1ca4f-119">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="1ca4f-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="1ca4f-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="1ca4f-120">Debugging</span></span>](index.md)
