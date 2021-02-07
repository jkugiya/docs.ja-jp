---
description: '詳細について: IHostThreadPoolManager:: QueueUserWorkItem メソッド'
title: IHostThreadPoolManager::QueueUserWorkItem メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
ms.openlocfilehash: edfbf5cfb34473a5fd920307981237fd5deab9aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753784"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="dd790-103">IHostThreadPoolManager::QueueUserWorkItem メソッド</span><span class="sxs-lookup"><span data-stu-id="dd790-103">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>

<span data-ttu-id="dd790-104">実行する関数をキューに配置し、その関数によって使用されるデータを格納しているオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="dd790-104">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="dd790-105">関数は、スレッドが使用可能になったときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="dd790-105">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd790-106">構文</span><span class="sxs-lookup"><span data-stu-id="dd790-106">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd790-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd790-107">Parameters</span></span>  

 `Function`  
 <span data-ttu-id="dd790-108">から実行する関数を表す関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="dd790-108">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="dd790-109">からによって使用されるデータを格納しているオブジェクト `Function` 。</span><span class="sxs-lookup"><span data-stu-id="dd790-109">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="dd790-110">からWin32 メソッドに対して定義されている、実行を制御するフラグ値の1つ `QueueUserWorkItem` 。</span><span class="sxs-lookup"><span data-stu-id="dd790-110">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd790-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="dd790-111">Return Value</span></span>  
  
|<span data-ttu-id="dd790-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd790-112">HRESULT</span></span>|<span data-ttu-id="dd790-113">説明</span><span class="sxs-lookup"><span data-stu-id="dd790-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd790-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd790-114">S_OK</span></span>|<span data-ttu-id="dd790-115">`QueueUserWorkItem` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="dd790-115">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="dd790-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dd790-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dd790-117">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="dd790-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dd790-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dd790-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dd790-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="dd790-119">The call timed out.</span></span>|  
|<span data-ttu-id="dd790-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd790-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dd790-121">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="dd790-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dd790-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dd790-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dd790-123">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="dd790-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dd790-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dd790-124">E_FAIL</span></span>|<span data-ttu-id="dd790-125">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="dd790-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dd790-126">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="dd790-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dd790-127">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd790-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd790-128">解説</span><span class="sxs-lookup"><span data-stu-id="dd790-128">Remarks</span></span>  

 <span data-ttu-id="dd790-129">`QueueUserWorkItem` スレッドプール内のワーカースレッドに作業項目をキューします。</span><span class="sxs-lookup"><span data-stu-id="dd790-129">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="dd790-130">そのシグネチャとパラメーターの型は、同じ名前を持つ対応する Win32 関数と同じです。</span><span class="sxs-lookup"><span data-stu-id="dd790-130">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="dd790-131">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd790-131">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd790-132">要件</span><span class="sxs-lookup"><span data-stu-id="dd790-132">Requirements</span></span>  

 <span data-ttu-id="dd790-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd790-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd790-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="dd790-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd790-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="dd790-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd790-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd790-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd790-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd790-137">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="dd790-138">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd790-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
