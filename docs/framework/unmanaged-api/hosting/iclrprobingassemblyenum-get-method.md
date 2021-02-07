---
description: '詳細について: ICLRProbingAssemblyEnum:: Get メソッド'
title: ICLRProbingAssemblyEnum::Get メソッド
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
ms.openlocfilehash: 77fb93b30a3b9b01b32fef9af661c84f484ef758
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716524"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="da1e0-103">ICLRProbingAssemblyEnum::Get メソッド</span><span class="sxs-lookup"><span data-stu-id="da1e0-103">ICLRProbingAssemblyEnum::Get Method</span></span>

<span data-ttu-id="da1e0-104">指定したインデックス位置にあるアセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="da1e0-104">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da1e0-105">構文</span><span class="sxs-lookup"><span data-stu-id="da1e0-105">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da1e0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="da1e0-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="da1e0-107">から返されるアセンブリ id の0から始まるインデックス。</span><span class="sxs-lookup"><span data-stu-id="da1e0-107">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="da1e0-108">入出力アセンブリ id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="da1e0-108">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="da1e0-109">[入力、出力]バッファーのサイズ `pwzBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="da1e0-109">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da1e0-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="da1e0-110">Return Value</span></span>  
  
|<span data-ttu-id="da1e0-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da1e0-111">HRESULT</span></span>|<span data-ttu-id="da1e0-112">説明</span><span class="sxs-lookup"><span data-stu-id="da1e0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da1e0-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="da1e0-113">S_OK</span></span>|<span data-ttu-id="da1e0-114">`Get` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="da1e0-114">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="da1e0-115">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="da1e0-115">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="da1e0-116">`pwzBuffer` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="da1e0-116">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="da1e0-117">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="da1e0-117">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="da1e0-118">列挙には、これ以上項目が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="da1e0-118">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="da1e0-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da1e0-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da1e0-120">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="da1e0-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="da1e0-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="da1e0-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="da1e0-122">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="da1e0-122">The call timed out.</span></span>|  
|<span data-ttu-id="da1e0-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="da1e0-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="da1e0-124">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="da1e0-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="da1e0-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="da1e0-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="da1e0-126">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="da1e0-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="da1e0-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da1e0-127">E_FAIL</span></span>|<span data-ttu-id="da1e0-128">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="da1e0-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="da1e0-129">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="da1e0-129">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="da1e0-130">後続のホストメソッドを呼び出すと HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="da1e0-130">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da1e0-131">解説</span><span class="sxs-lookup"><span data-stu-id="da1e0-131">Remarks</span></span>  

 <span data-ttu-id="da1e0-132">インデックス0の id は、プロセッサアーキテクチャに固有の id です。</span><span class="sxs-lookup"><span data-stu-id="da1e0-132">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="da1e0-133">インデックス1の id は、Microsoft 中間言語 (MSIL) のアーキテクチャに依存しないアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="da1e0-133">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="da1e0-134">インデックス2の id にアーキテクチャ情報が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="da1e0-134">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="da1e0-135">`Get` は通常、2回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="da1e0-135">`Get` is typically called twice.</span></span> <span data-ttu-id="da1e0-136">最初の呼び出しでは、に null 値を指定し、に `pwzBuffer` `pcchBufferSize` 適したサイズに設定し `pwzBuffer` ます。</span><span class="sxs-lookup"><span data-stu-id="da1e0-136">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="da1e0-137">2番目の呼び出しでは、適切にサイズ `pwzBuffer` を指定し、完了時に正規のアセンブリ id データを格納します。</span><span class="sxs-lookup"><span data-stu-id="da1e0-137">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da1e0-138">要件</span><span class="sxs-lookup"><span data-stu-id="da1e0-138">Requirements</span></span>  

 <span data-ttu-id="da1e0-139">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da1e0-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da1e0-140">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="da1e0-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da1e0-141">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="da1e0-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da1e0-142">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da1e0-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da1e0-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="da1e0-143">See also</span></span>

- [<span data-ttu-id="da1e0-144">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da1e0-144">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="da1e0-145">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da1e0-145">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
