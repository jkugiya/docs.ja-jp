---
description: '詳細情報: ICorConfiguration:: Setデバッガ Threadcontrol メソッド'
title: ICorConfiguration::SetDebuggerThreadControl メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
ms.openlocfilehash: 9bf024f3feb6df44a94f8a5f1a626bb6e0c91d31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636664"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="7d3fa-103">ICorConfiguration::SetDebuggerThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="7d3fa-103">ICorConfiguration::SetDebuggerThreadControl Method</span></span>

<span data-ttu-id="7d3fa-104">共通言語ランタイム (CLR) スレッドがブロックされ、デバッグのためにブロック解除されると、デバッグサービスが呼び出すコールバックインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="7d3fa-104">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d3fa-105">構文</span><span class="sxs-lookup"><span data-stu-id="7d3fa-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d3fa-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d3fa-106">Parameters</span></span>  

 `pDebuggerThreadControl`  
 <span data-ttu-id="7d3fa-107">からデバッグサービスによるスレッドのブロックおよびブロック解除についてホストに通知する [Iデバッガ Threadcontrol](idebuggerthreadcontrol-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7d3fa-107">[in] A pointer to an [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d3fa-108">要件</span><span class="sxs-lookup"><span data-stu-id="7d3fa-108">Requirements</span></span>  

 <span data-ttu-id="7d3fa-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d3fa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d3fa-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7d3fa-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d3fa-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7d3fa-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d3fa-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d3fa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d3fa-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d3fa-113">See also</span></span>

- [<span data-ttu-id="7d3fa-114">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d3fa-114">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
