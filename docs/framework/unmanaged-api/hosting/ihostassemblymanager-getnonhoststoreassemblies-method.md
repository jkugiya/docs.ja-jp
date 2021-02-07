---
description: '詳細については、次を参照してください: IHostAssemblyManager:: GetNonHostStoreAssemblies メソッド'
title: IHostAssemblyManager::GetNonHostStoreAssemblies メソッド
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
ms.openlocfilehash: ef551db45428b2381dfeae8f722257241a4deaf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709049"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="f12d2-103">IHostAssemblyManager::GetNonHostStoreAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="f12d2-103">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>

<span data-ttu-id="f12d2-104">ホストが読み込みのために共通言語ランタイム (CLR) を必要とするアセンブリのリストを表す [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f12d2-104">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12d2-105">構文</span><span class="sxs-lookup"><span data-stu-id="f12d2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f12d2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f12d2-106">Parameters</span></span>  

 `ppReferenceList`  
 <span data-ttu-id="f12d2-107">入出力 `ICLRAssemblyReferenceList` ホストが CLR を読み込むことを想定しているアセンブリへの参照の一覧を含むのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f12d2-107">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f12d2-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f12d2-108">Return Value</span></span>  
  
|<span data-ttu-id="f12d2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f12d2-109">HRESULT</span></span>|<span data-ttu-id="f12d2-110">説明</span><span class="sxs-lookup"><span data-stu-id="f12d2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f12d2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f12d2-111">S_OK</span></span>|<span data-ttu-id="f12d2-112">`GetNonHostStoreAssemblies` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f12d2-112">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="f12d2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f12d2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f12d2-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f12d2-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f12d2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f12d2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f12d2-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f12d2-116">The call timed out.</span></span>|  
|<span data-ttu-id="f12d2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f12d2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f12d2-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f12d2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f12d2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f12d2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f12d2-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f12d2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f12d2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f12d2-121">E_FAIL</span></span>|<span data-ttu-id="f12d2-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f12d2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f12d2-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f12d2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f12d2-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f12d2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f12d2-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f12d2-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f12d2-126">要求されたの参照の一覧を作成するのに十分なメモリがありませんでした `ICLRAssemblyReferenceList` 。</span><span class="sxs-lookup"><span data-stu-id="f12d2-126">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f12d2-127">解説</span><span class="sxs-lookup"><span data-stu-id="f12d2-127">Remarks</span></span>  

 <span data-ttu-id="f12d2-128">CLR は、次の一連のガイドラインを使用して参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="f12d2-128">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="f12d2-129">まず、によって返されるアセンブリ参照の一覧を参照し `GetNonHostStoreAssemblies` ます。</span><span class="sxs-lookup"><span data-stu-id="f12d2-129">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="f12d2-130">アセンブリが一覧に表示されている場合、CLR は通常どおりにバインドします。</span><span class="sxs-lookup"><span data-stu-id="f12d2-130">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="f12d2-131">アセンブリが一覧に表示されず、ホストが [IHostAssemblyStore](ihostassemblystore-interface.md)の実装を提供した場合、CLR は [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) を呼び出して、バインド先のアセンブリをホストが指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f12d2-131">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="f12d2-132">それ以外の場合、CLR はアセンブリへのバインドに失敗します。</span><span class="sxs-lookup"><span data-stu-id="f12d2-132">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="f12d2-133">ホストが null に設定されている場合、 `ppReferenceList` CLR はまずグローバルアセンブリキャッシュをプローブし、 `ProvideAssembly` を呼び出してから、アプリケーションベースをプローブしてアセンブリ参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="f12d2-133">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f12d2-134">初期化時に、CLR は `GetNonHostStoreAssemblies` 1 回だけを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f12d2-134">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="f12d2-135">メソッドが再度呼び出されていません。</span><span class="sxs-lookup"><span data-stu-id="f12d2-135">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f12d2-136">要件</span><span class="sxs-lookup"><span data-stu-id="f12d2-136">Requirements</span></span>  

 <span data-ttu-id="f12d2-137">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f12d2-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12d2-138">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f12d2-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f12d2-139">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f12d2-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f12d2-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f12d2-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12d2-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="f12d2-141">See also</span></span>

- [<span data-ttu-id="f12d2-142">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f12d2-142">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f12d2-143">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f12d2-143">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="f12d2-144">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f12d2-144">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
