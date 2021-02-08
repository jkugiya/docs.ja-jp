---
description: 詳細については、「CorDebugStepReason 列挙型」を参照してください。
title: CorDebugStepReason 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 2a331b09709ffb6179f2e481baf4bf421d60ea99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801541"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="835b8-103">CorDebugStepReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="835b8-103">CorDebugStepReason Enumeration</span></span>

<span data-ttu-id="835b8-104">個々のステップの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="835b8-104">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="835b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="835b8-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="835b8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="835b8-106">Members</span></span>  
  
|<span data-ttu-id="835b8-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="835b8-107">Member</span></span>|<span data-ttu-id="835b8-108">説明</span><span class="sxs-lookup"><span data-stu-id="835b8-108">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="835b8-109">同じ関数内で通常どおりにステップ実行が完了しました。</span><span class="sxs-lookup"><span data-stu-id="835b8-109">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="835b8-110">関数が返された後、通常どおりにステップ実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="835b8-110">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="835b8-111">新しく呼び出された関数の先頭で、ステップ実行は通常どおり続行されます。</span><span class="sxs-lookup"><span data-stu-id="835b8-111">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="835b8-112">例外が生成され、制御が例外フィルターに渡されました。</span><span class="sxs-lookup"><span data-stu-id="835b8-112">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="835b8-113">例外が生成され、制御が例外ハンドラーに渡されました。</span><span class="sxs-lookup"><span data-stu-id="835b8-113">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="835b8-114">コントロールがインターセプターに渡されました。</span><span class="sxs-lookup"><span data-stu-id="835b8-114">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="835b8-115">ステップが完了する前にスレッドが終了しました。</span><span class="sxs-lookup"><span data-stu-id="835b8-115">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="835b8-116">要件</span><span class="sxs-lookup"><span data-stu-id="835b8-116">Requirements</span></span>  

 <span data-ttu-id="835b8-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="835b8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="835b8-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="835b8-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="835b8-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="835b8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="835b8-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="835b8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835b8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="835b8-121">See also</span></span>

- [<span data-ttu-id="835b8-122">StepComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="835b8-122">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="835b8-123">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="835b8-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
