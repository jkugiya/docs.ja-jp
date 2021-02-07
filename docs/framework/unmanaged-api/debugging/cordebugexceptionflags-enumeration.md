---
description: 詳細については、「CorDebugExceptionFlags 列挙型」を参照してください。
title: CorDebugExceptionFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
ms.openlocfilehash: c0036c2674f3202623da1a8fdeea14165a2a6e62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747050"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="d2fa4-103">CorDebugExceptionFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="d2fa4-103">CorDebugExceptionFlags Enumeration</span></span>

<span data-ttu-id="d2fa4-104">例外に関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d2fa4-104">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2fa4-105">構文</span><span class="sxs-lookup"><span data-stu-id="d2fa4-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d2fa4-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d2fa4-106">Members</span></span>  
  
|<span data-ttu-id="d2fa4-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="d2fa4-107">Member</span></span>|<span data-ttu-id="d2fa4-108">説明</span><span class="sxs-lookup"><span data-stu-id="d2fa4-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="d2fa4-109">例外がありません。</span><span class="sxs-lookup"><span data-stu-id="d2fa4-109">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="d2fa4-110">例外をインターセプトすることが可能です。</span><span class="sxs-lookup"><span data-stu-id="d2fa4-110">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="d2fa4-111">ただし例外のタイミングによっては、デバッガーが例外をインターセプトできないことがあります。</span><span class="sxs-lookup"><span data-stu-id="d2fa4-111">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="d2fa4-112">たとえば、現行のコールバックの下にマネージド コードがない場合、または just-in-time (JIT) アタッチメントから発生した例外イベントの場合には、例外をインターセプトできません。</span><span class="sxs-lookup"><span data-stu-id="d2fa4-112">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2fa4-113">解説</span><span class="sxs-lookup"><span data-stu-id="d2fa4-113">Remarks</span></span>  

 <span data-ttu-id="d2fa4-114">この列挙には今後のバージョンで新しい値が追加される可能性があるため、`CorDebugExceptionFlags` を使用するコードは予想外の値に対して準備しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2fa4-114">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2fa4-115">要件</span><span class="sxs-lookup"><span data-stu-id="d2fa4-115">Requirements</span></span>  

 <span data-ttu-id="d2fa4-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2fa4-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2fa4-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2fa4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2fa4-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2fa4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2fa4-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2fa4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2fa4-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2fa4-120">See also</span></span>

- [<span data-ttu-id="d2fa4-121">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="d2fa4-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
