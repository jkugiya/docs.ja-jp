---
description: '詳細については、次を参照してください: Ihohoo参照マネージャー:: Bind メソッド'
title: IHostIoCompletionManager::Bind メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
ms.openlocfilehash: 2105bf06c23f70588d0c1bc0cd849b8e810d121e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784861"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="cb0e6-103">IHostIoCompletionManager::Bind メソッド</span><span class="sxs-lookup"><span data-stu-id="cb0e6-103">IHostIoCompletionManager::Bind Method</span></span>

<span data-ttu-id="cb0e6-104">以前に [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)を呼び出したときに作成された i/o 完了ポートに、指定されたハンドルをバインドします。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-104">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb0e6-105">構文</span><span class="sxs-lookup"><span data-stu-id="cb0e6-105">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb0e6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cb0e6-106">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="cb0e6-107">からバインド先の i/o 完了ポート `hHandle` 。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-107">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="cb0e6-108">の値 `hPort` が null の場合、 `hHandle` は既定の i/o 完了ポートにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-108">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="cb0e6-109">からバインド先のオペレーティングシステムハンドル `hPort` 。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-109">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb0e6-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="cb0e6-110">Return Value</span></span>  
  
|<span data-ttu-id="cb0e6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb0e6-111">HRESULT</span></span>|<span data-ttu-id="cb0e6-112">説明</span><span class="sxs-lookup"><span data-stu-id="cb0e6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb0e6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb0e6-113">S_OK</span></span>|<span data-ttu-id="cb0e6-114">`Bind` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-114">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="cb0e6-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb0e6-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb0e6-116">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb0e6-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb0e6-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb0e6-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-118">The call timed out.</span></span>|  
|<span data-ttu-id="cb0e6-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb0e6-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb0e6-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb0e6-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb0e6-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb0e6-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb0e6-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb0e6-123">E_FAIL</span></span>|<span data-ttu-id="cb0e6-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb0e6-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb0e6-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb0e6-127">解説</span><span class="sxs-lookup"><span data-stu-id="cb0e6-127">Remarks</span></span>  

 <span data-ttu-id="cb0e6-128">I/o 完了ポートは、の呼び出しを使用して作成され `CreateIoCompletionPort` ます。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-128">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="cb0e6-129">CLR はを呼び出し `Bind` て、そのポートにハンドルをバインドします。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-129">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb0e6-130">I/o 要求が完了すると、ホストは [Iclriocomplete manager:: OnComplete](iclriocompletionmanager-oncomplete-method.md) メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-130">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb0e6-131">要件</span><span class="sxs-lookup"><span data-stu-id="cb0e6-131">Requirements</span></span>  

 <span data-ttu-id="cb0e6-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb0e6-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb0e6-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cb0e6-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb0e6-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="cb0e6-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb0e6-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb0e6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb0e6-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb0e6-136">See also</span></span>

- [<span data-ttu-id="cb0e6-137">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb0e6-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
