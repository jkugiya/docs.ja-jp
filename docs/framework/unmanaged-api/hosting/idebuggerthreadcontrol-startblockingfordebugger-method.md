---
description: '詳細情報: Iデバッガ Threadcontrol:: StartBlockingForDebugger メソッド'
title: IDebuggerThreadControl::StartBlockingForDebugger メソッド
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
ms.openlocfilehash: 3e19817c4adbefd1dd70be047656b3fea261c389
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709675"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="81734-103">IDebuggerThreadControl::StartBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="81734-103">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>

<span data-ttu-id="81734-104">デバッグサービスがすべてのスレッドのブロックを開始しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="81734-104">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81734-105">構文</span><span class="sxs-lookup"><span data-stu-id="81734-105">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81734-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81734-106">Parameters</span></span>  

 `dwUnused`  
 <span data-ttu-id="81734-107">から将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="81734-107">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81734-108">解説</span><span class="sxs-lookup"><span data-stu-id="81734-108">Remarks</span></span>  

 <span data-ttu-id="81734-109">`StartBlockingForDebugger`ランタイムスレッドでメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="81734-109">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81734-110">要件</span><span class="sxs-lookup"><span data-stu-id="81734-110">Requirements</span></span>  

 <span data-ttu-id="81734-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81734-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81734-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="81734-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81734-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="81734-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81734-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81734-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81734-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="81734-115">See also</span></span>

- [<span data-ttu-id="81734-116">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81734-116">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
