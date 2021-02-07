---
description: '詳細情報: Ihohoo参照マネージャー:: InitializeHostOverlapped メソッド'
title: IHostIoCompletionManager::InitializeHostOverlapped メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
ms.openlocfilehash: 10be7edb67143937dec6efc6e35466466374d32d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708464"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="d6a0c-103">IHostIoCompletionManager::InitializeHostOverlapped メソッド</span><span class="sxs-lookup"><span data-stu-id="d6a0c-103">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>

<span data-ttu-id="d6a0c-104">非同期 i/o 要求に使用される Win32 構造体に追加するカスタムデータを初期化する機会をホストに提供し `OVERLAPPED` ます。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-104">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6a0c-105">構文</span><span class="sxs-lookup"><span data-stu-id="d6a0c-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6a0c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6a0c-106">Parameters</span></span>  

 `pvOverlapped`  
 <span data-ttu-id="d6a0c-107">から `OVERLAPPED` I/o 要求に含まれる Win32 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-107">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6a0c-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="d6a0c-108">Return Value</span></span>  
  
|<span data-ttu-id="d6a0c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6a0c-109">HRESULT</span></span>|<span data-ttu-id="d6a0c-110">説明</span><span class="sxs-lookup"><span data-stu-id="d6a0c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6a0c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6a0c-111">S_OK</span></span>|<span data-ttu-id="d6a0c-112">`InitializeHostOverlapped` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-112">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="d6a0c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6a0c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6a0c-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6a0c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6a0c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6a0c-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-116">The call timed out.</span></span>|  
|<span data-ttu-id="d6a0c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6a0c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6a0c-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6a0c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6a0c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6a0c-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6a0c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6a0c-121">E_FAIL</span></span>|<span data-ttu-id="d6a0c-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6a0c-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6a0c-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d6a0c-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d6a0c-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d6a0c-126">要求されたリソースを割り当てるのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-126">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6a0c-127">解説</span><span class="sxs-lookup"><span data-stu-id="d6a0c-127">Remarks</span></span>  

 <span data-ttu-id="d6a0c-128">Windows プラットフォーム関数は、構造体を使用して `OVERLAPPED` 非同期 i/o 要求の状態を格納します。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-128">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="d6a0c-129">CLR は、メソッドを呼び出して、 `InitializeHostOverlapped` ホストにカスタムデータをインスタンスに追加する機会を与え `OVERLAPPED` ます。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-129">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d6a0c-130">カスタムデータブロックの先頭に到達するには、ホストで、オフセットを構造体のサイズ () に設定する必要があり `OVERLAPPED` `sizeof(OVERLAPPED)` ます。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-130">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="d6a0c-131">E_OUTOFMEMORY の戻り値は、ホストがカスタムデータを初期化できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-131">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="d6a0c-132">この場合、CLR はエラーを報告し、呼び出しに失敗します。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-132">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6a0c-133">要件</span><span class="sxs-lookup"><span data-stu-id="d6a0c-133">Requirements</span></span>  

 <span data-ttu-id="d6a0c-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6a0c-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6a0c-135">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d6a0c-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6a0c-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d6a0c-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6a0c-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6a0c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a0c-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6a0c-138">See also</span></span>

- [<span data-ttu-id="d6a0c-139">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6a0c-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="d6a0c-140">GetHostOverlappedSize メソッド</span><span class="sxs-lookup"><span data-stu-id="d6a0c-140">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="d6a0c-141">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6a0c-141">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
