---
description: '詳細については、次を参照してください: Cordebugexception/Type 列挙型'
title: CorDebugExceptionCallbackType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
ms.openlocfilehash: 41b9cdf707de017703ee3756b3d04a38163bb03b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801684"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="cc830-103">CorDebugExceptionCallbackType 列挙型</span><span class="sxs-lookup"><span data-stu-id="cc830-103">CorDebugExceptionCallbackType Enumeration</span></span>

<span data-ttu-id="cc830-104">[ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)イベントから作成されたコールバックの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="cc830-104">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc830-105">構文</span><span class="sxs-lookup"><span data-stu-id="cc830-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="cc830-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cc830-106">Members</span></span>  
  
|<span data-ttu-id="cc830-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="cc830-107">Member</span></span>|<span data-ttu-id="cc830-108">説明</span><span class="sxs-lookup"><span data-stu-id="cc830-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="cc830-109">例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="cc830-109">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="cc830-110">例外 windup プロセスによってユーザーコードが入力されました。</span><span class="sxs-lookup"><span data-stu-id="cc830-110">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="cc830-111">例外 windup プロセスにより、 `catch` ユーザーコードにブロックが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="cc830-111">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="cc830-112">例外は処理されませんでした。</span><span class="sxs-lookup"><span data-stu-id="cc830-112">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc830-113">要件</span><span class="sxs-lookup"><span data-stu-id="cc830-113">Requirements</span></span>  

 <span data-ttu-id="cc830-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc830-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc830-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc830-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc830-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc830-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc830-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc830-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc830-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc830-118">See also</span></span>

- [<span data-ttu-id="cc830-119">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="cc830-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
