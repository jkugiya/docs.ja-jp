---
description: '詳細については、次を参照してください: CorDebugExceptionObjectStackFrame 構造体'
title: CorDebugExceptionObjectStackFrame 構造体
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
ms.openlocfilehash: abeb5a9f6385c494745a34c6f37d6fbc1376ad7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662157"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="10409-103">CorDebugExceptionObjectStackFrame 構造体</span><span class="sxs-lookup"><span data-stu-id="10409-103">CorDebugExceptionObjectStackFrame Structure</span></span>

<span data-ttu-id="10409-104">例外オブジェクトのスタック フレームの情報を表しています。</span><span class="sxs-lookup"><span data-stu-id="10409-104">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10409-105">構文</span><span class="sxs-lookup"><span data-stu-id="10409-105">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="10409-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="10409-106">Members</span></span>  
  
|<span data-ttu-id="10409-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="10409-107">Member</span></span>|<span data-ttu-id="10409-108">説明</span><span class="sxs-lookup"><span data-stu-id="10409-108">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="10409-109">現在のフレームのモジュールオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="10409-109">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="10409-110">現在のフレームの命令ポインター (EIP/RIP) の値。</span><span class="sxs-lookup"><span data-stu-id="10409-110">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="10409-111">現在のフレームのメソッドトークン。</span><span class="sxs-lookup"><span data-stu-id="10409-111">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="10409-112">フレームが外部例外の最後のフレームであるかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="10409-112">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10409-113">解説</span><span class="sxs-lookup"><span data-stu-id="10409-113">Remarks</span></span>  

 <span data-ttu-id="10409-114">呼び出し元は、使用されなくなったときに、モジュールオブジェクトへのポインターを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10409-114">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10409-115">要件</span><span class="sxs-lookup"><span data-stu-id="10409-115">Requirements</span></span>  

 <span data-ttu-id="10409-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10409-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10409-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10409-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10409-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10409-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10409-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10409-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10409-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="10409-120">See also</span></span>

- [<span data-ttu-id="10409-121">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="10409-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="10409-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="10409-122">Debugging</span></span>](index.md)
