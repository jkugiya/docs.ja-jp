---
description: '詳細情報: Iデバッガ Threadcontrol インターフェイス'
title: IDebuggerThreadControl インターフェイス
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
ms.openlocfilehash: 293a120d44b9b04d7e367546c477fb273f535310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709770"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="50f13-103">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50f13-103">IDebuggerThreadControl Interface</span></span>

<span data-ttu-id="50f13-104">デバッグサービスによるスレッドのブロックおよびブロック解除についてホストに通知するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="50f13-104">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50f13-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="50f13-105">Methods</span></span>  
  
|<span data-ttu-id="50f13-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="50f13-106">Method</span></span>|<span data-ttu-id="50f13-107">説明</span><span class="sxs-lookup"><span data-stu-id="50f13-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50f13-108">ThreadIsBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="50f13-108">ThreadIsBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="50f13-109">このコールバックを送信しているスレッドがデバッグサービス内でブロックされようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="50f13-109">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="50f13-110">ReleaseAllRuntimeThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="50f13-110">ReleaseAllRuntimeThreads Method</span></span>](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="50f13-111">デバッグサービスがブロックされているすべてのスレッドを解放しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="50f13-111">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="50f13-112">StartBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="50f13-112">StartBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="50f13-113">デバッグサービスがすべてのスレッドのブロックを開始しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="50f13-113">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50f13-114">要件</span><span class="sxs-lookup"><span data-stu-id="50f13-114">Requirements</span></span>  

 <span data-ttu-id="50f13-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50f13-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50f13-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="50f13-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50f13-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="50f13-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50f13-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50f13-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f13-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="50f13-119">See also</span></span>

- [<span data-ttu-id="50f13-120">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50f13-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
