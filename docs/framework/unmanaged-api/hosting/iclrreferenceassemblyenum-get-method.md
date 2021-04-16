---
description: '詳細情報: ICLRReferenceAssemblyEnum::Get メソッド'
title: ICLRReferenceAssemblyEnum::Get メソッド
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
ms.openlocfilehash: ea4e71631a9ebb381f721b78f17507603891a032
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637301"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="07123-103">ICLRReferenceAssemblyEnum::Get メソッド</span><span class="sxs-lookup"><span data-stu-id="07123-103">ICLRReferenceAssemblyEnum::Get Method</span></span>

<span data-ttu-id="07123-104">指定されたインデックス位置にあるアセンブリ ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="07123-104">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07123-105">構文</span><span class="sxs-lookup"><span data-stu-id="07123-105">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07123-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="07123-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="07123-107">[in] 返されるアセンブリ ID の、0 から始まるインデックス。</span><span class="sxs-lookup"><span data-stu-id="07123-107">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="07123-108">[out] アセンブリ ID データが含まれるバッファー。</span><span class="sxs-lookup"><span data-stu-id="07123-108">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="07123-109">[in、out] `pwzBuffer` バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="07123-109">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07123-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="07123-110">Return Value</span></span>  
  
|<span data-ttu-id="07123-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07123-111">HRESULT</span></span>|<span data-ttu-id="07123-112">説明</span><span class="sxs-lookup"><span data-stu-id="07123-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07123-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="07123-113">S_OK</span></span>|<span data-ttu-id="07123-114">`Get` が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="07123-114">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="07123-115">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="07123-115">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="07123-116">`pwzBuffer` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="07123-116">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="07123-117">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="07123-117">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="07123-118">列挙型には、これ以上項目が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="07123-118">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="07123-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="07123-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="07123-120">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージド コードを実行できないまたは呼び出しを正常に処理できない状態です。</span><span class="sxs-lookup"><span data-stu-id="07123-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="07123-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07123-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="07123-122">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="07123-122">The call timed out.</span></span>|  
|<span data-ttu-id="07123-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="07123-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="07123-124">呼び出し元はロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="07123-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="07123-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="07123-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="07123-126">ブロックされたスレッドまたはファイバーが待機しているイベントがキャンセルされました。</span><span class="sxs-lookup"><span data-stu-id="07123-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="07123-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="07123-127">E_FAIL</span></span>|<span data-ttu-id="07123-128">不明な壊滅的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="07123-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="07123-129">メソッドで E_FAIL が返される場合、CLR をプロセス内で使用することはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="07123-129">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="07123-130">ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="07123-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07123-131">解説</span><span class="sxs-lookup"><span data-stu-id="07123-131">Remarks</span></span>  

 <span data-ttu-id="07123-132">通常、`Get` は 2 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="07123-132">`Get` is typically called twice.</span></span> <span data-ttu-id="07123-133">最初の呼び出しでは、`pwzBuffer` に null 値を指定し、`pcchBufferSize` を `pwzBuffer` に適したサイズに設定します。</span><span class="sxs-lookup"><span data-stu-id="07123-133">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="07123-134">2 番目の呼び出しでは、適切なサイズの `pwzBuffer` が供給され、完了時に正規のアセンブリ ID データが格納されます。</span><span class="sxs-lookup"><span data-stu-id="07123-134">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07123-135">必要条件</span><span class="sxs-lookup"><span data-stu-id="07123-135">Requirements</span></span>  

 <span data-ttu-id="07123-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07123-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07123-137">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="07123-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07123-138">**ライブラリ:** リソースとして MSCorEE.dll に含まれている</span><span class="sxs-lookup"><span data-stu-id="07123-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07123-139">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07123-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07123-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="07123-140">See also</span></span>

- [<span data-ttu-id="07123-141">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="07123-141">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="07123-142">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="07123-142">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
