---
description: '詳細情報: Iclrio参照マネージャーインターフェイス'
title: ICLRIoCompletionManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: b2d18f9c9900d448f0c6517520c303eb4258f8d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789889"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="b8bb7-103">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8bb7-103">ICLRIoCompletionManager Interface</span></span>

<span data-ttu-id="b8bb7-104">ホストが、指定された i/o 要求のステータスの共通言語ランタイム (CLR) に通知するためのコールバックメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="b8bb7-104">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8bb7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b8bb7-105">Methods</span></span>  
  
|<span data-ttu-id="b8bb7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b8bb7-106">Method</span></span>|<span data-ttu-id="b8bb7-107">説明</span><span class="sxs-lookup"><span data-stu-id="b8bb7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8bb7-108">OnComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="b8bb7-108">OnComplete Method</span></span>](iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="b8bb7-109">[Ihohooの](ihostiocompletionmanager-bind-method.md)呼び出しを使用して作成された i/o 要求の状態を CLR に通知します:: Bind メソッド。</span><span class="sxs-lookup"><span data-stu-id="b8bb7-109">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8bb7-110">解説</span><span class="sxs-lookup"><span data-stu-id="b8bb7-110">Remarks</span></span>  

 <span data-ttu-id="b8bb7-111">ホストは、 [Ihohoocompletion manager](ihostiocompletionmanager-interface.md) インターフェイスを使用して i/o 完了の抽象化を実装します。</span><span class="sxs-lookup"><span data-stu-id="b8bb7-111">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="b8bb7-112">CLR はこのインターフェイスを介して i/o 要求を行い、ホストはインターフェイスを使用して、そのような要求の結果をランタイムに通知し `ICLRIoCompletionManager` ます。</span><span class="sxs-lookup"><span data-stu-id="b8bb7-112">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8bb7-113">要件</span><span class="sxs-lookup"><span data-stu-id="b8bb7-113">Requirements</span></span>  

 <span data-ttu-id="b8bb7-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8bb7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8bb7-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b8bb7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8bb7-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b8bb7-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8bb7-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8bb7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8bb7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8bb7-118">See also</span></span>

- [<span data-ttu-id="b8bb7-119">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8bb7-119">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="b8bb7-120">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8bb7-120">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="b8bb7-121">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8bb7-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
