---
description: '詳細については、次を参照してください: CorDebugThreadState 列挙型'
title: CorDebugThreadState 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 0cf83ee31547e49ccc7d09e0ab4ee85548688b36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661806"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="f5fb9-103">CorDebugThreadState 列挙型</span><span class="sxs-lookup"><span data-stu-id="f5fb9-103">CorDebugThreadState Enumeration</span></span>

<span data-ttu-id="f5fb9-104">デバッグのスレッドの状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="f5fb9-104">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5fb9-105">構文</span><span class="sxs-lookup"><span data-stu-id="f5fb9-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="f5fb9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f5fb9-106">Members</span></span>  
  
|<span data-ttu-id="f5fb9-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="f5fb9-107">Member</span></span>|<span data-ttu-id="f5fb9-108">説明</span><span class="sxs-lookup"><span data-stu-id="f5fb9-108">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="f5fb9-109">デバッグイベントが発生しない限り、スレッドは自由に実行できます。</span><span class="sxs-lookup"><span data-stu-id="f5fb9-109">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="f5fb9-110">スレッドを実行できません。</span><span class="sxs-lookup"><span data-stu-id="f5fb9-110">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5fb9-111">解説</span><span class="sxs-lookup"><span data-stu-id="f5fb9-111">Remarks</span></span>  

 <span data-ttu-id="f5fb9-112">デバッガーは、列挙体を使用して `CorDebugThreadState` スレッドの実行を制御します。</span><span class="sxs-lookup"><span data-stu-id="f5fb9-112">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="f5fb9-113">スレッドの状態を設定するには、次のように指定する必要があります: [: SetDebugState](icordebugthread-setdebugstate-method.md) または、モジュール [:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) メソッド。</span><span class="sxs-lookup"><span data-stu-id="f5fb9-113">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="f5fb9-114">[ホスティング API](../hosting/index.md)に提供されるコールバックによってメッセージポンプが可能になるため、中断された状態は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f5fb9-114">A callback provided to the [hosting API](../hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5fb9-115">要件</span><span class="sxs-lookup"><span data-stu-id="f5fb9-115">Requirements</span></span>  

 <span data-ttu-id="f5fb9-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5fb9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5fb9-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5fb9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5fb9-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5fb9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5fb9-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5fb9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5fb9-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5fb9-120">See also</span></span>

- [<span data-ttu-id="f5fb9-121">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="f5fb9-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
