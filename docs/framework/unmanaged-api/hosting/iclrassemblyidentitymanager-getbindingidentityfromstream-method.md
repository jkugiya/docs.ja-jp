---
description: '詳細については、次を参照してください: ICLRAssemblyIdentityManager:: Getbinding Fromstream メソッド'
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
ms.openlocfilehash: aed5968a5f5c22a2f5cbea66a350dbe452368325
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716889"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="c3dc3-103">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="c3dc3-103">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>

<span data-ttu-id="c3dc3-104">指定したストリーム内のアセンブリの正規アセンブリ id データを取得します。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-104">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3dc3-105">構文</span><span class="sxs-lookup"><span data-stu-id="c3dc3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3dc3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c3dc3-106">Parameters</span></span>  

 `pStream`  
 <span data-ttu-id="c3dc3-107">から評価されるアセンブリストリーム。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-107">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c3dc3-108">から将来の拡張のために提供されます。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="c3dc3-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンでサポートされている唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="c3dc3-110">入出力非透過アセンブリ id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="c3dc3-111">[入力、出力]のサイズ `pwzBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-111">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3dc3-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="c3dc3-112">Return Value</span></span>  
  
|<span data-ttu-id="c3dc3-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3dc3-113">HRESULT</span></span>|<span data-ttu-id="c3dc3-114">説明</span><span class="sxs-lookup"><span data-stu-id="c3dc3-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3dc3-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3dc3-115">S_OK</span></span>|<span data-ttu-id="c3dc3-116">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="c3dc3-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c3dc3-117">E_INVALIDARG</span></span>|<span data-ttu-id="c3dc3-118">指定された `pStream` が null です。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-118">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="c3dc3-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c3dc3-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c3dc3-120">のサイズ `pwzBuffer` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="c3dc3-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c3dc3-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c3dc3-122">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c3dc3-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c3dc3-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c3dc3-124">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-124">The call timed out.</span></span>|  
|<span data-ttu-id="c3dc3-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c3dc3-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c3dc3-126">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c3dc3-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c3dc3-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c3dc3-128">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c3dc3-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c3dc3-129">E_FAIL</span></span>|<span data-ttu-id="c3dc3-130">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c3dc3-131">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c3dc3-132">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3dc3-133">要件</span><span class="sxs-lookup"><span data-stu-id="c3dc3-133">Requirements</span></span>  

 <span data-ttu-id="c3dc3-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3dc3-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3dc3-135">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c3dc3-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3dc3-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c3dc3-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3dc3-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3dc3-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3dc3-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3dc3-138">See also</span></span>

- [<span data-ttu-id="c3dc3-139">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3dc3-139">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="c3dc3-140">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3dc3-140">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
