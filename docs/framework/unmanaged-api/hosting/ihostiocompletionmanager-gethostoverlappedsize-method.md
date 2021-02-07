---
description: '詳細については、次を参照してください: IhohooGetHostOverlappedSize Manager:: メソッド'
title: IHostIoCompletionManager::GetHostOverlappedSize メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: 2a2ebe1da82c5702269b634eadfe98b72739e3df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708568"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="6441e-103">IHostIoCompletionManager::GetHostOverlappedSize メソッド</span><span class="sxs-lookup"><span data-stu-id="6441e-103">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>

<span data-ttu-id="6441e-104">ホストが i/o 要求に追加しようとしているカスタムデータのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="6441e-104">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6441e-105">構文</span><span class="sxs-lookup"><span data-stu-id="6441e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6441e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6441e-106">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="6441e-107">入出力Win32 オブジェクトのサイズに加えて、共通言語ランタイム (CLR: common language runtime) によって割り当てられるバイト数へのポインター `OVERLAPPED` 。</span><span class="sxs-lookup"><span data-stu-id="6441e-107">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6441e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="6441e-108">Return Value</span></span>  
  
|<span data-ttu-id="6441e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6441e-109">HRESULT</span></span>|<span data-ttu-id="6441e-110">説明</span><span class="sxs-lookup"><span data-stu-id="6441e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6441e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6441e-111">S_OK</span></span>|<span data-ttu-id="6441e-112">`GetHostOverlappedSize` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="6441e-112">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="6441e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6441e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6441e-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6441e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6441e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6441e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6441e-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6441e-116">The call timed out.</span></span>|  
|<span data-ttu-id="6441e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6441e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6441e-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6441e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6441e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6441e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6441e-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="6441e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6441e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6441e-121">E_FAIL</span></span>|<span data-ttu-id="6441e-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6441e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6441e-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6441e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6441e-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6441e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6441e-125">解説</span><span class="sxs-lookup"><span data-stu-id="6441e-125">Remarks</span></span>  

 <span data-ttu-id="6441e-126">Windows プラットフォーム Api に対するすべての非同期 i/o 呼び出しは、 `OVERLAPPED` ファイルポインターの位置などの情報を提供する Win32 オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="6441e-126">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="6441e-127">状態を維持するために、非同期 i/o 呼び出しを行うアプリケーションは、通常、カスタムデータを構造に追加します。</span><span class="sxs-lookup"><span data-stu-id="6441e-127">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="6441e-128">`GetHostOverlappedSize` と [Iho、O補完 manager:: InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) は、このようなカスタムデータをホストに含める機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="6441e-128">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="6441e-129">CLR は、メソッドを呼び出して、 `GetHostOverlappedSize` ホストがオブジェクトに追加するカスタムデータのサイズを決定し `OVERLAPPED` ます。</span><span class="sxs-lookup"><span data-stu-id="6441e-129">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6441e-130">`GetHostOverlappedSize` は1回だけ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6441e-130">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="6441e-131">ホストのカスタムデータは、すべての i/o 要求に対して同じサイズである必要があります。</span><span class="sxs-lookup"><span data-stu-id="6441e-131">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6441e-132">オブジェクト自体のサイズ `OVERLAPPED` は、の値には含まれません `pcbSize` 。</span><span class="sxs-lookup"><span data-stu-id="6441e-132">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="6441e-133">構造体の詳細については、 `OVERLAPPED` Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6441e-133">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6441e-134">要件</span><span class="sxs-lookup"><span data-stu-id="6441e-134">Requirements</span></span>  

 <span data-ttu-id="6441e-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6441e-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6441e-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6441e-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6441e-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6441e-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6441e-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6441e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6441e-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="6441e-139">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="6441e-140">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6441e-140">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="6441e-141">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6441e-141">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
