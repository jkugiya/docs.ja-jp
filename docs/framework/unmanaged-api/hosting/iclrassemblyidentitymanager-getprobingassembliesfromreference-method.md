---
description: '詳細情報: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference メソッド'
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
ms.openlocfilehash: 38fcea460537ebed0e54103b460a48c2e58d8173
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431426"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="2ad68-103">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference メソッド</span><span class="sxs-lookup"><span data-stu-id="2ad68-103">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>

<span data-ttu-id="2ad68-104">指定された ID 型を使用してアセンブリによって参照されるアセンブリ ID の [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) 列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="2ad68-104">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ad68-105">構文</span><span class="sxs-lookup"><span data-stu-id="2ad68-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ad68-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2ad68-106">Parameters</span></span>  

 `dwMachineType`  
 <span data-ttu-id="2ad68-107">[in] WinNT.h に定義されたとおりにプロセッサ アーキテクチャを指定する有効な値。</span><span class="sxs-lookup"><span data-stu-id="2ad68-107">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2ad68-108">[in] 将来の拡張用に用意されています。</span><span class="sxs-lookup"><span data-stu-id="2ad68-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="2ad68-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンでサポートされている唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="2ad68-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="2ad68-110">[in] 不透明なアセンブリ バインド ID。通常は、[ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) メソッドまたは [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) メソッドの呼び出しから返されます。</span><span class="sxs-lookup"><span data-stu-id="2ad68-110">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="2ad68-111">[out] `pwzReferenceIdentity` によって識別されるアセンブリで参照されるアセンブリへの参照を含む `ICLRProbingAssemblyEnum` 列挙子のインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="2ad68-111">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ad68-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="2ad68-112">Return Value</span></span>  
  
|<span data-ttu-id="2ad68-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ad68-113">HRESULT</span></span>|<span data-ttu-id="2ad68-114">説明</span><span class="sxs-lookup"><span data-stu-id="2ad68-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ad68-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ad68-115">S_OK</span></span>|<span data-ttu-id="2ad68-116">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="2ad68-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="2ad68-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ad68-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ad68-118">CLR がプロセスに読み込まれていない、または CLR が、マネージド コードを実行したり呼び出しを正常に処理したりできない状態にあります。</span><span class="sxs-lookup"><span data-stu-id="2ad68-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2ad68-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2ad68-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2ad68-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2ad68-120">The call timed out.</span></span>|  
|<span data-ttu-id="2ad68-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2ad68-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2ad68-122">呼び出し元はロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2ad68-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2ad68-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2ad68-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2ad68-124">ブロックされたスレッドまたはファイバーが待機しているイベントがキャンセルされました。</span><span class="sxs-lookup"><span data-stu-id="2ad68-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2ad68-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2ad68-125">E_FAIL</span></span>|<span data-ttu-id="2ad68-126">不明な壊滅的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2ad68-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2ad68-127">メソッドで E_FAIL が返される場合、CLR をプロセス内で使用することはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="2ad68-127">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2ad68-128">ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="2ad68-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ad68-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="2ad68-129">Requirements</span></span>  

 <span data-ttu-id="2ad68-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ad68-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ad68-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ad68-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ad68-132">**ライブラリ:** リソースとして MSCorEE.dll に含まれている</span><span class="sxs-lookup"><span data-stu-id="2ad68-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ad68-133">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ad68-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad68-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ad68-134">See also</span></span>

- [<span data-ttu-id="2ad68-135">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ad68-135">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="2ad68-136">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ad68-136">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="2ad68-137">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ad68-137">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
