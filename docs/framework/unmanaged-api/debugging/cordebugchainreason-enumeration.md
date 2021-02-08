---
description: '詳細については、次を参照してください: CorDebugChainReason 列挙型'
title: CorDebugChainReason 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
ms.openlocfilehash: 18b6ac9c50c3a44a77a0f63a680b84c70e667e9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801749"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="6f7c5-103">CorDebugChainReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="6f7c5-103">CorDebugChainReason Enumeration</span></span>

<span data-ttu-id="6f7c5-104">呼び出しチェーンが開始する理由を示します。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-104">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f7c5-105">構文</span><span class="sxs-lookup"><span data-stu-id="6f7c5-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a><span data-ttu-id="6f7c5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="6f7c5-106">Members</span></span>  
  
|<span data-ttu-id="6f7c5-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="6f7c5-107">Member</span></span>|<span data-ttu-id="6f7c5-108">説明</span><span class="sxs-lookup"><span data-stu-id="6f7c5-108">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="6f7c5-109">呼び出しチェーンが開始されていません。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-109">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="6f7c5-110">コンストラクターによって、チェーンが開始されました。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-110">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="6f7c5-111">例外フィルターによって、チェーンが開始されました。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-111">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="6f7c5-112">セキュリティを適用するコードによって、チェーンが開始されました。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-112">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="6f7c5-113">コンテキスト ポリシーによって、チェーンが開始されました。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-113">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="6f7c5-114">使用しません。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-114">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="6f7c5-115">使用しません。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-115">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="6f7c5-116">スレッド実行の開始によって、チェーンが開始されました。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-116">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="6f7c5-117">マネージド コードへのエントリによって、チェーンが開始されました。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-117">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="6f7c5-118">アンマネージ コードへのエントリによって、チェーンが開始されました。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-118">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="6f7c5-119">使用しません。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-119">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="6f7c5-120">使用しません。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-120">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="6f7c5-121">関数の評価によって、チェーンが開始されました。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-121">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f7c5-122">解説</span><span class="sxs-lookup"><span data-stu-id="6f7c5-122">Remarks</span></span>  

 <span data-ttu-id="6f7c5-123">呼び出しチェーンが開始された理由を確認するには、と [いう方法を使用します](icordebugchain-getreason-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-123">Use the [ICorDebugChain::GetReason](icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f7c5-124">要件</span><span class="sxs-lookup"><span data-stu-id="6f7c5-124">Requirements</span></span>  

 <span data-ttu-id="6f7c5-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f7c5-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f7c5-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f7c5-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f7c5-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f7c5-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f7c5-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f7c5-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7c5-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f7c5-129">See also</span></span>

- [<span data-ttu-id="6f7c5-130">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="6f7c5-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
