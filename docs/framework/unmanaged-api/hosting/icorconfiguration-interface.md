---
description: 詳細については、「ICorConfiguration インターフェイス」を参照してください。
title: ICorConfiguration インターフェイス
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
ms.openlocfilehash: f75e9e445c7fe4615abcae27756bcc420b5255b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636678"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="79a0a-103">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79a0a-103">ICorConfiguration Interface</span></span>

<span data-ttu-id="79a0a-104">共通言語ランタイム (CLR: common language runtime) を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="79a0a-104">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79a0a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="79a0a-105">Methods</span></span>  
  
|<span data-ttu-id="79a0a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="79a0a-106">Method</span></span>|<span data-ttu-id="79a0a-107">説明</span><span class="sxs-lookup"><span data-stu-id="79a0a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79a0a-108">AddDebuggerSpecialThread メソッド</span><span class="sxs-lookup"><span data-stu-id="79a0a-108">AddDebuggerSpecialThread Method</span></span>](icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="79a0a-109">デバッグサービスに対して、マネージまたはアンマネージのデバッグシナリオでデバッガーがアプリケーションを停止している間に、特定のスレッドの実行を継続できるようにする必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="79a0a-109">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="79a0a-110">SetDebuggerThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="79a0a-110">SetDebuggerThreadControl Method</span></span>](icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="79a0a-111">CLR スレッドがデバッグのためにブロックおよびブロック解除されるため、デバッグサービスが呼び出すコールバックインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="79a0a-111">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="79a0a-112">SetGCHostControl メソッド</span><span class="sxs-lookup"><span data-stu-id="79a0a-112">SetGCHostControl Method</span></span>](icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="79a0a-113">仮想メモリの制限を変更するようにホストに要求するために、ガベージコレクターによって使用されるコールバックインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="79a0a-113">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="79a0a-114">SetGCThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="79a0a-114">SetGCThreadControl Method</span></span>](icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="79a0a-115">ガベージコレクションに対してブロックされる非ランタイムタスクのスレッドをスケジュールするためのコールバックインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="79a0a-115">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79a0a-116">要件</span><span class="sxs-lookup"><span data-stu-id="79a0a-116">Requirements</span></span>  

 <span data-ttu-id="79a0a-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79a0a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79a0a-118">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="79a0a-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79a0a-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="79a0a-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79a0a-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79a0a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a0a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="79a0a-121">See also</span></span>

- [<span data-ttu-id="79a0a-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79a0a-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="79a0a-123">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="79a0a-123">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
