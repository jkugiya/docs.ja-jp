---
description: '詳細について: ICLRGCManager:: SetGCStartupLimits メソッド'
title: ICLRGCManager::SetGCStartupLimits メソッド
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
ms.openlocfilehash: 5614b41cfd7a7938cdb653d879119ddbd9560b9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789984"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="358c1-103">ICLRGCManager::SetGCStartupLimits メソッド</span><span class="sxs-lookup"><span data-stu-id="358c1-103">ICLRGCManager::SetGCStartupLimits Method</span></span>

<span data-ttu-id="358c1-104">ガベージコレクションセグメントのサイズとガベージコレクションシステムのジェネレーション0の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="358c1-104">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="358c1-105">.NET Framework 4.5 以降では、 `DWORD` [ICLRGCManager2:: SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) メソッドを使用して、セグメントサイズと最大ジェネレーション0のサイズをより大きい値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="358c1-105">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="358c1-106">構文</span><span class="sxs-lookup"><span data-stu-id="358c1-106">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="358c1-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="358c1-107">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="358c1-108">からガベージコレクションセグメントの指定されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="358c1-108">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="358c1-109">セグメントの最小サイズは 4 MB です。</span><span class="sxs-lookup"><span data-stu-id="358c1-109">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="358c1-110">セグメントは、1 MB 以上の単位で増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="358c1-110">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="358c1-111">からジェネレーション0の指定された最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="358c1-111">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="358c1-112">ジェネレーション0の最小サイズは 64 KB です。</span><span class="sxs-lookup"><span data-stu-id="358c1-112">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="358c1-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="358c1-113">Return Value</span></span>  
  
|<span data-ttu-id="358c1-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="358c1-114">HRESULT</span></span>|<span data-ttu-id="358c1-115">説明</span><span class="sxs-lookup"><span data-stu-id="358c1-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="358c1-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="358c1-116">S_OK</span></span>|<span data-ttu-id="358c1-117">`SetGCStartupLimits` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="358c1-117">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="358c1-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="358c1-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="358c1-119">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="358c1-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="358c1-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="358c1-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="358c1-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="358c1-121">The call timed out.</span></span>|  
|<span data-ttu-id="358c1-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="358c1-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="358c1-123">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="358c1-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="358c1-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="358c1-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="358c1-125">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="358c1-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="358c1-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="358c1-126">E_FAIL</span></span>|<span data-ttu-id="358c1-127">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="358c1-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="358c1-128">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="358c1-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="358c1-129">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="358c1-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="358c1-130">解説</span><span class="sxs-lookup"><span data-stu-id="358c1-130">Remarks</span></span>  

 <span data-ttu-id="358c1-131">を設定する値は、 `SetGCStartupLimits` 1 回だけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="358c1-131">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="358c1-132">の後の呼び出し `SetGCStartupLimits` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="358c1-132">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="358c1-133">要件</span><span class="sxs-lookup"><span data-stu-id="358c1-133">Requirements</span></span>  

 <span data-ttu-id="358c1-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="358c1-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="358c1-135">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="358c1-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="358c1-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="358c1-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="358c1-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="358c1-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358c1-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="358c1-138">See also</span></span>

- [<span data-ttu-id="358c1-139">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="358c1-139">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="358c1-140">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="358c1-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="358c1-141">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="358c1-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="358c1-142">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="358c1-142">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
