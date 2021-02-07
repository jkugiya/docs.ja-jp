---
description: '詳細については、次を参照してください: Ihohoo参照マネージャーインターフェイス'
title: IHostIoCompletionManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
ms.openlocfilehash: 30cb0ecbfd9645bc0374e3570751832d6fa8eced
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708321"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="473a8-103">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="473a8-103">IHostIoCompletionManager Interface</span></span>

<span data-ttu-id="473a8-104">共通言語ランタイム (CLR) がホストによって提供される i/o 完了ポートと対話できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="473a8-104">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="473a8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-105">Methods</span></span>  
  
|<span data-ttu-id="473a8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-106">Method</span></span>|<span data-ttu-id="473a8-107">説明</span><span class="sxs-lookup"><span data-stu-id="473a8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="473a8-108">Bind メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-108">Bind Method</span></span>](ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="473a8-109">I/o 完了ポートにハンドルをバインドします。</span><span class="sxs-lookup"><span data-stu-id="473a8-109">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="473a8-110">CloseIoCompletionPort メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-110">CloseIoCompletionPort Method</span></span>](ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="473a8-111">以前のの呼び出しによって作成されたポートを閉じ `CreateIoCompletionPort` ます。</span><span class="sxs-lookup"><span data-stu-id="473a8-111">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="473a8-112">CreateIoCompletionPort メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-112">CreateIoCompletionPort Method</span></span>](ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="473a8-113">ホストが新しい i/o 完了ポートを作成することを要求します。</span><span class="sxs-lookup"><span data-stu-id="473a8-113">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="473a8-114">GetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-114">GetAvailableThreads Method</span></span>](ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="473a8-115">現在要求を処理していない i/o 完了スレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="473a8-115">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="473a8-116">GetHostOverlappedSize メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-116">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="473a8-117">ホストが i/o 要求に追加しようとしているカスタムデータのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="473a8-117">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="473a8-118">GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-118">GetMaxThreads Method</span></span>](ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="473a8-119">ホストがサービス i/o 要求に割り当てることができるスレッドの最大数を取得します。</span><span class="sxs-lookup"><span data-stu-id="473a8-119">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="473a8-120">GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-120">GetMinThreads Method</span></span>](ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="473a8-121">ホストが i/o 要求を処理するために提供するスレッドの最小数を取得します。</span><span class="sxs-lookup"><span data-stu-id="473a8-121">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="473a8-122">InitializeHostOverlapped メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-122">InitializeHostOverlapped Method</span></span>](ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="473a8-123">I/o 要求に関するカスタムデータを初期化する機会をホストに提供します。</span><span class="sxs-lookup"><span data-stu-id="473a8-123">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="473a8-124">SetCLRIoCompletionManager メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-124">SetCLRIoCompletionManager Method</span></span>](ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="473a8-125">CLR によって実装されている [Iclrio提供マネージャー](iclriocompletionmanager-interface.md) インスタンスへのインターフェイスポインターをホストに提供します。</span><span class="sxs-lookup"><span data-stu-id="473a8-125">Provides the host with an interface pointer to an [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="473a8-126">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-126">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="473a8-127">ホストが大量の i/o 要求を処理するスレッドの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="473a8-127">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="473a8-128">SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="473a8-128">SetMinThreads Method</span></span>](ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="473a8-129">ホストが i/o 完了に割り当てる必要があるスレッドの最小数を設定します。</span><span class="sxs-lookup"><span data-stu-id="473a8-129">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="473a8-130">解説</span><span class="sxs-lookup"><span data-stu-id="473a8-130">Remarks</span></span>  

 <span data-ttu-id="473a8-131">`IHostIoCompletionManager` CLR によって実装されるインターフェイスに対応し `ICLRIoCompletionManager` ます。</span><span class="sxs-lookup"><span data-stu-id="473a8-131">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="473a8-132">CLR は、のメソッドを呼び出して、 `IHostIoCompletionManager` ホストが提供するポートにハンドルをバインドします。また、ホストはのメソッドを呼び出して、i/o `ICLRIoCompletionManager` 要求の完了を報告します。</span><span class="sxs-lookup"><span data-stu-id="473a8-132">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="473a8-133">要件</span><span class="sxs-lookup"><span data-stu-id="473a8-133">Requirements</span></span>  

 <span data-ttu-id="473a8-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="473a8-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="473a8-135">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="473a8-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="473a8-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="473a8-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="473a8-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="473a8-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473a8-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="473a8-138">See also</span></span>

- [<span data-ttu-id="473a8-139">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="473a8-139">Hosting Interfaces</span></span>](hosting-interfaces.md)
