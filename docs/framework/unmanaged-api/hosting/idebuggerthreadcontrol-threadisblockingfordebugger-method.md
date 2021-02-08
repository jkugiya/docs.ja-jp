---
description: '詳細情報: Iデバッガ Threadcontrol:: ThreadIsBlockingForDebugger メソッド'
title: IDebuggerThreadControl::ThreadIsBlockingForDebugger メソッド
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
ms.openlocfilehash: 0fa96b2e36ea6653e1698dd32fa1e73d223afb94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789516"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="f0423-103">IDebuggerThreadControl::ThreadIsBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="f0423-103">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>

<span data-ttu-id="f0423-104">このコールバックを送信しているスレッドがデバッグサービス内でブロックされようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="f0423-104">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0423-105">構文</span><span class="sxs-lookup"><span data-stu-id="f0423-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="f0423-106">解説</span><span class="sxs-lookup"><span data-stu-id="f0423-106">Remarks</span></span>  

 <span data-ttu-id="f0423-107">`ThreadIsBlockingForDebugger`メソッドは常にランタイムスレッドで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f0423-107">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="f0423-108">メソッドは、 `ThreadIsBlockingForDebugger` スレッドがブロックされている間に、ホストに別のアクションを実行する機会を与えます。</span><span class="sxs-lookup"><span data-stu-id="f0423-108">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0423-109">要件</span><span class="sxs-lookup"><span data-stu-id="f0423-109">Requirements</span></span>  

 <span data-ttu-id="f0423-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0423-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0423-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f0423-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0423-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f0423-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0423-113">**.Net Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0423-113">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0423-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0423-114">See also</span></span>

- [<span data-ttu-id="f0423-115">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f0423-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
