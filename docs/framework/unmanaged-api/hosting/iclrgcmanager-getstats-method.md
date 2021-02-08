---
description: '詳細について: ICLRGCManager:: GetStats メソッド'
title: ICLRGCManager::GetStats メソッド
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 94b20fb313f06d73f1e7fafd1f46fefb0da3fe95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790023"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="33306-103">ICLRGCManager::GetStats メソッド</span><span class="sxs-lookup"><span data-stu-id="33306-103">ICLRGCManager::GetStats Method</span></span>

<span data-ttu-id="33306-104">共通言語ランタイムのガベージコレクションシステムに関する現在の統計のセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="33306-104">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33306-105">構文</span><span class="sxs-lookup"><span data-stu-id="33306-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33306-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="33306-106">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="33306-107">[入力、出力]要求された統計情報を含む [COR_GC_STATS](cor-gc-stats-structure.md) インスタンス。</span><span class="sxs-lookup"><span data-stu-id="33306-107">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33306-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="33306-108">Return Value</span></span>  
  
|<span data-ttu-id="33306-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33306-109">HRESULT</span></span>|<span data-ttu-id="33306-110">説明</span><span class="sxs-lookup"><span data-stu-id="33306-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33306-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="33306-111">S_OK</span></span>|<span data-ttu-id="33306-112">`GetStats` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="33306-112">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="33306-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="33306-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="33306-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="33306-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="33306-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="33306-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="33306-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="33306-116">The call timed out.</span></span>|  
|<span data-ttu-id="33306-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="33306-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="33306-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="33306-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="33306-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="33306-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="33306-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="33306-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="33306-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33306-121">E_FAIL</span></span>|<span data-ttu-id="33306-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="33306-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="33306-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="33306-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="33306-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="33306-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33306-125">解説</span><span class="sxs-lookup"><span data-stu-id="33306-125">Remarks</span></span>  

 <span data-ttu-id="33306-126">CLR は、のフィールドによって指定された統計のみを計算して返し `Flags` `pStats` ます。</span><span class="sxs-lookup"><span data-stu-id="33306-126">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="33306-127">フィールドを `Flags` [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) 列挙体の1つ以上の値に設定して、 [COR_GC_STATS](cor-gc-stats-structure.md) 構造内のどの統計情報を設定するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="33306-127">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="33306-128">使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="33306-128">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="33306-129">要件</span><span class="sxs-lookup"><span data-stu-id="33306-129">Requirements</span></span>  

 <span data-ttu-id="33306-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33306-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33306-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="33306-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33306-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="33306-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33306-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33306-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33306-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="33306-134">See also</span></span>

- [<span data-ttu-id="33306-135">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="33306-135">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="33306-136">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="33306-136">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="33306-137">COR_GC_STAT_TYPES 列挙体</span><span class="sxs-lookup"><span data-stu-id="33306-137">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="33306-138">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="33306-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="33306-139">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="33306-139">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="33306-140">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="33306-140">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="33306-141">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="33306-141">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="33306-142">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="33306-142">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="33306-143">ホスティング</span><span class="sxs-lookup"><span data-stu-id="33306-143">Hosting</span></span>](index.md)
