---
description: '詳細について: ICLRAssemblyIdentityManager:: GetProbingAssembliesFromReference メソッド'
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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431426"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="07182-103">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference メソッド</span><span class="sxs-lookup"><span data-stu-id="07182-103">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>

<span data-ttu-id="07182-104">指定した id 型のアセンブリによって参照されるアセンブリ id の [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) 列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="07182-104">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07182-105">構文</span><span class="sxs-lookup"><span data-stu-id="07182-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07182-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="07182-106">Parameters</span></span>  

 `dwMachineType`  
 <span data-ttu-id="07182-107">からWinnt.h で定義されているプロセッサアーキテクチャを指定する有効な値。</span><span class="sxs-lookup"><span data-stu-id="07182-107">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="07182-108">から将来の拡張のために提供されます。</span><span class="sxs-lookup"><span data-stu-id="07182-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="07182-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンでサポートされている唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="07182-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="07182-110">から通常、 [ICLRAssemblyIdentityManager:: GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) または [ICLRAssemblyIdentityManager:: Getbinding fromstream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) メソッドの呼び出しから返される、不透明なアセンブリバインド id。</span><span class="sxs-lookup"><span data-stu-id="07182-110">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="07182-111">入出力 `ICLRProbingAssemblyEnum` によって識別されるアセンブリによって参照されるアセンブリへの参照を格納する列挙子へのインターフェイスポインター `pwzReferenceIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="07182-111">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07182-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="07182-112">Return Value</span></span>  
  
|<span data-ttu-id="07182-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07182-113">HRESULT</span></span>|<span data-ttu-id="07182-114">説明</span><span class="sxs-lookup"><span data-stu-id="07182-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07182-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="07182-115">S_OK</span></span>|<span data-ttu-id="07182-116">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="07182-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="07182-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="07182-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="07182-118">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="07182-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="07182-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07182-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="07182-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="07182-120">The call timed out.</span></span>|  
|<span data-ttu-id="07182-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="07182-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="07182-122">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="07182-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="07182-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="07182-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="07182-124">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="07182-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="07182-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="07182-125">E_FAIL</span></span>|<span data-ttu-id="07182-126">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="07182-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="07182-127">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="07182-127">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="07182-128">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="07182-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07182-129">要件</span><span class="sxs-lookup"><span data-stu-id="07182-129">Requirements</span></span>  

 <span data-ttu-id="07182-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07182-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07182-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="07182-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07182-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="07182-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07182-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07182-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07182-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="07182-134">See also</span></span>

- [<span data-ttu-id="07182-135">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="07182-135">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="07182-136">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="07182-136">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="07182-137">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="07182-137">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
