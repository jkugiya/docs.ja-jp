---
description: '詳細情報: ICorConfiguration インターフェイス'
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636678"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="f9935-103">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9935-103">ICorConfiguration Interface</span></span>

<span data-ttu-id="f9935-104">共通言語ランタイム (CLR) を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9935-104">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9935-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f9935-105">Methods</span></span>  
  
|<span data-ttu-id="f9935-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="f9935-106">Method</span></span>|<span data-ttu-id="f9935-107">説明</span><span class="sxs-lookup"><span data-stu-id="f9935-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9935-108">AddDebuggerSpecialThread メソッド</span><span class="sxs-lookup"><span data-stu-id="f9935-108">AddDebuggerSpecialThread Method</span></span>](icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="f9935-109">マネージまたはアンマネージのデバッグ シナリオ時にデバッガーによってアプリケーションが停止されている間に、特定のスレッドの実行を継続できるようにする必要があることを、デバッグ サービスに対して示します。</span><span class="sxs-lookup"><span data-stu-id="f9935-109">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="f9935-110">SetDebuggerThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="f9935-110">SetDebuggerThreadControl Method</span></span>](icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="f9935-111">CLR スレッドがデバッグのためにブロックおよびブロック解除される際にデバッグ サービスによって呼び出されるコールバック インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="f9935-111">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="f9935-112">SetGCHostControl メソッド</span><span class="sxs-lookup"><span data-stu-id="f9935-112">SetGCHostControl Method</span></span>](icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="f9935-113">仮想メモリの制限を変更するようにホストに要求するために、ガベージ コレクターによって使用されるコールバック インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="f9935-113">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="f9935-114">SetGCThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="f9935-114">SetGCThreadControl Method</span></span>](icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="f9935-115">本来ならガベージ コレクションのためにブロックされる非ランタイム タスク用のスレッドをスケジュールするための、コールバック インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="f9935-115">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9935-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="f9935-116">Requirements</span></span>  

 <span data-ttu-id="f9935-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9935-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9935-118">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f9935-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9935-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="f9935-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9935-120">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9935-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9935-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9935-121">See also</span></span>

- [<span data-ttu-id="f9935-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9935-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f9935-123">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="f9935-123">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
