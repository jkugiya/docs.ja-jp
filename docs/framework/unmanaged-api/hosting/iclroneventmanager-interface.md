---
description: 詳細については、「ICLROnEventManager インターフェイス」を参照してください。
title: ICLROnEventManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: 7a9c0beec5083bc93f5361bb0e701da5beeedea2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789828"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="807d2-103">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="807d2-103">ICLROnEventManager Interface</span></span>

<span data-ttu-id="807d2-104">ホストが共通言語ランタイム (CLR) イベントのコールバックを登録および登録解除できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="807d2-104">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="807d2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="807d2-105">Methods</span></span>  
  
|<span data-ttu-id="807d2-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="807d2-106">Method</span></span>|<span data-ttu-id="807d2-107">説明</span><span class="sxs-lookup"><span data-stu-id="807d2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="807d2-108">RegisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="807d2-108">RegisterActionOnEvent Method</span></span>](iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="807d2-109">指定されたイベントのコールバックポインターを登録します。</span><span class="sxs-lookup"><span data-stu-id="807d2-109">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="807d2-110">UnregisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="807d2-110">UnregisterActionOnEvent Method</span></span>](iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="807d2-111">指定されたイベントに対して、以前に登録されたコールバックポインターの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="807d2-111">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="807d2-112">解説</span><span class="sxs-lookup"><span data-stu-id="807d2-112">Remarks</span></span>  

 <span data-ttu-id="807d2-113">イベントコールバックの登録と登録解除を行うために、ホストは `ICLROnEventManager` [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) メソッドを呼び出すことによってへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="807d2-113">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="807d2-114">[Eclrevent](eclrevent-enumeration.md)によって説明されているイベントは、異なるスレッドから、または CLR のアンロードまたは無効化を通知するために、複数回発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="807d2-114">The events described by [EClrEvent](eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="807d2-115">要件</span><span class="sxs-lookup"><span data-stu-id="807d2-115">Requirements</span></span>  

 <span data-ttu-id="807d2-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="807d2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="807d2-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="807d2-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="807d2-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="807d2-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="807d2-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="807d2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="807d2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="807d2-120">See also</span></span>

- [<span data-ttu-id="807d2-121">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="807d2-121">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="807d2-122">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="807d2-122">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="807d2-123">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="807d2-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="807d2-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="807d2-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
