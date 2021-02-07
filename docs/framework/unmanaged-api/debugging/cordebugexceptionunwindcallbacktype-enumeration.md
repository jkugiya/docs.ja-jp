---
description: '詳細については、次を参照してください: CorDebugExceptionUnwindCallbackType 列挙型'
title: CorDebugExceptionUnwindCallbackType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
ms.openlocfilehash: 3e12cffcdf1eb921330f658215c52501dce83eff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747024"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="f23ee-103">CorDebugExceptionUnwindCallbackType 列挙型</span><span class="sxs-lookup"><span data-stu-id="f23ee-103">CorDebugExceptionUnwindCallbackType Enumeration</span></span>

<span data-ttu-id="f23ee-104">アンワインド フェーズ中にコールバックによって通知されるイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="f23ee-104">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f23ee-105">構文</span><span class="sxs-lookup"><span data-stu-id="f23ee-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="f23ee-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f23ee-106">Members</span></span>  
  
|<span data-ttu-id="f23ee-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="f23ee-107">Member</span></span>|<span data-ttu-id="f23ee-108">説明</span><span class="sxs-lookup"><span data-stu-id="f23ee-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="f23ee-109">アンワインドプロセスの開始。</span><span class="sxs-lookup"><span data-stu-id="f23ee-109">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="f23ee-110">例外がインターセプトされました。</span><span class="sxs-lookup"><span data-stu-id="f23ee-110">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f23ee-111">要件</span><span class="sxs-lookup"><span data-stu-id="f23ee-111">Requirements</span></span>  

 <span data-ttu-id="f23ee-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f23ee-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f23ee-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f23ee-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f23ee-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f23ee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f23ee-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f23ee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f23ee-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f23ee-116">See also</span></span>

- [<span data-ttu-id="f23ee-117">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="f23ee-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
