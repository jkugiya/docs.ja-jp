---
description: '詳細について: ICLRGCManager2:: SetGCStartupLimitsEx メソッド'
title: ICLRGCManager2::SetGCStartupLimitsEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
ms.openlocfilehash: 2a4801d2f6255f5f84e0a4bae7a1886689ee8dc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689239"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="cd23f-103">ICLRGCManager2::SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="cd23f-103">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="cd23f-104">ガベージコレクションセグメントのサイズとガベージコレクションシステムのジェネレーション0の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="cd23f-104">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd23f-105">構文</span><span class="sxs-lookup"><span data-stu-id="cd23f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd23f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd23f-106">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="cd23f-107">からガベージコレクションセグメントの指定されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="cd23f-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="cd23f-108">セグメントの最小サイズは 4 MB です。</span><span class="sxs-lookup"><span data-stu-id="cd23f-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="cd23f-109">セグメントは、1 MB 以上の単位で増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="cd23f-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="cd23f-110">からジェネレーション0の指定された最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="cd23f-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="cd23f-111">ジェネレーション0の最小サイズは 64 KB です。</span><span class="sxs-lookup"><span data-stu-id="cd23f-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd23f-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="cd23f-112">Return Value</span></span>  
  
|<span data-ttu-id="cd23f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd23f-113">HRESULT</span></span>|<span data-ttu-id="cd23f-114">説明</span><span class="sxs-lookup"><span data-stu-id="cd23f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd23f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd23f-115">S_OK</span></span>|<span data-ttu-id="cd23f-116">`SetGCStartupLimitsEx` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="cd23f-116">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="cd23f-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd23f-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd23f-118">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="cd23f-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cd23f-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cd23f-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cd23f-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="cd23f-120">The call timed out.</span></span>|  
|<span data-ttu-id="cd23f-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cd23f-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cd23f-122">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="cd23f-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cd23f-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cd23f-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cd23f-124">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="cd23f-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cd23f-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd23f-125">E_FAIL</span></span>|<span data-ttu-id="cd23f-126">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="cd23f-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd23f-127">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cd23f-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd23f-128">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="cd23f-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd23f-129">解説</span><span class="sxs-lookup"><span data-stu-id="cd23f-129">Remarks</span></span>  

 <span data-ttu-id="cd23f-130">を設定する値は、 `SetGCStartupLimitsEx` ホストを開始する前にのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="cd23f-130">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="cd23f-131">の後の呼び出し `SetGCStartupLimitsEx` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="cd23f-131">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="cd23f-132">どちらか一方のパラメーターに影響を及ぼさずに設定するには、変更しないパラメーターに 0 (ゼロ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd23f-132">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd23f-133">要件</span><span class="sxs-lookup"><span data-stu-id="cd23f-133">Requirements</span></span>  

 <span data-ttu-id="cd23f-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd23f-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd23f-135">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cd23f-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd23f-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="cd23f-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd23f-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd23f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd23f-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd23f-138">See also</span></span>

- [<span data-ttu-id="cd23f-139">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="cd23f-139">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="cd23f-140">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="cd23f-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="cd23f-141">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd23f-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="cd23f-142">ICLRGCManager2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd23f-142">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)
