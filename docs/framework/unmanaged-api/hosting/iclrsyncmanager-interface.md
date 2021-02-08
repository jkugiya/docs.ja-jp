---
description: 詳細については、「ICLRSyncManager インターフェイス」を参照してください。
title: ICLRSyncManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
ms.openlocfilehash: 188d1c913d75666aea09b17244012401d377fa10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785014"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="a6754-103">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6754-103">ICLRSyncManager Interface</span></span>

<span data-ttu-id="a6754-104">ホストが要求されたタスクに関する情報を取得し、その同期実装でデッドロックを検出できるようにするメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="a6754-104">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a6754-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a6754-105">Methods</span></span>  
  
|<span data-ttu-id="a6754-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a6754-106">Method</span></span>|<span data-ttu-id="a6754-107">説明</span><span class="sxs-lookup"><span data-stu-id="a6754-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6754-108">CreateRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="a6754-108">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="a6754-109">リーダーライターロックを待機しているタスクのセットを決定するために使用するホストの反復子を共通言語ランタイム (CLR) が作成することを要求します。</span><span class="sxs-lookup"><span data-stu-id="a6754-109">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="a6754-110">DeleteRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="a6754-110">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="a6754-111">の呼び出しによって作成された反復子が CLR によって破棄されることを要求 `CreateRWLockOwnerIterator` します。</span><span class="sxs-lookup"><span data-stu-id="a6754-111">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="a6754-112">GetMonitorOwner メソッド</span><span class="sxs-lookup"><span data-stu-id="a6754-112">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="a6754-113">指定したモニターを所有しているタスクを取得します。</span><span class="sxs-lookup"><span data-stu-id="a6754-113">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="a6754-114">GetRWLockOwnerNext メソッド</span><span class="sxs-lookup"><span data-stu-id="a6754-114">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="a6754-115">現在のリーダーライターロックを待機している次のタスクを取得します。</span><span class="sxs-lookup"><span data-stu-id="a6754-115">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6754-116">要件</span><span class="sxs-lookup"><span data-stu-id="a6754-116">Requirements</span></span>  

 <span data-ttu-id="a6754-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6754-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6754-118">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a6754-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6754-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a6754-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6754-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6754-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6754-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6754-121">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="a6754-122">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6754-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="a6754-123">[マネージド スレッドとアンマネージド スレッド](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a6754-123">[Managed and Unmanaged Threading](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="a6754-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6754-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
