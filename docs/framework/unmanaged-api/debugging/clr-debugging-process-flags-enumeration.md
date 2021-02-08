---
description: '詳細情報: CLR_DEBUGGING_PROCESS_FLAGS 列挙型'
title: CLR_DEBUGGING_PROCESS_FLAGS 列挙体
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
ms.openlocfilehash: 81510bde123ef9a8adefaec5b0708086dacbbf2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772810"
---
# <a name="clr_debugging_process_flags-enumeration"></a><span data-ttu-id="f29df-103">CLR_DEBUGGING_PROCESS_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="f29df-103">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>

<span data-ttu-id="f29df-104">[ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md)メソッドによって使用される値を提供します。</span><span class="sxs-lookup"><span data-stu-id="f29df-104">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f29df-105">構文</span><span class="sxs-lookup"><span data-stu-id="f29df-105">Syntax</span></span>  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="f29df-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f29df-106">Members</span></span>  
  
|<span data-ttu-id="f29df-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="f29df-107">Member</span></span>|<span data-ttu-id="f29df-108">説明</span><span class="sxs-lookup"><span data-stu-id="f29df-108">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="f29df-109">このランタイムには、送信するキャッチアップマネージデバッガーイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="f29df-109">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="f29df-110">キャッチアップイベントと非キャッチアップイベントの違いについては、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f29df-110">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="f29df-111">保留中のマネージイベントは、 <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> 要求です。</span><span class="sxs-lookup"><span data-stu-id="f29df-111">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f29df-112">解説</span><span class="sxs-lookup"><span data-stu-id="f29df-112">Remarks</span></span>  

 <span data-ttu-id="f29df-113">キャッチアップイベントには、プロセスにアタッチした後にデバッガーが現在の状態になるようにするプロセス、アプリケーションドメイン、アセンブリ、モジュール、スレッド作成通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f29df-113">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="f29df-114">フラグによって示されるキャッチアップ以外のイベントには、 `CLR_DEBUGGING_MANAGED_EVENT_PENDING` 例外やマネージデバッグアシスタント (MDA) 通知など、他のすべてのデバッガーイベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f29df-114">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="f29df-115">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`フラグにより、ランタイムは、終了した例外と、キャンセル可能なマネージデバッガーをアタッチする要求を区別できます。</span><span class="sxs-lookup"><span data-stu-id="f29df-115">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f29df-116">要件</span><span class="sxs-lookup"><span data-stu-id="f29df-116">Requirements</span></span>  

 <span data-ttu-id="f29df-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f29df-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f29df-118">**ヘッダー:** メタホスト .idl、メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="f29df-118">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="f29df-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f29df-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f29df-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f29df-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f29df-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f29df-121">See also</span></span>

- [<span data-ttu-id="f29df-122">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="f29df-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="f29df-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f29df-123">Debugging</span></span>](index.md)
