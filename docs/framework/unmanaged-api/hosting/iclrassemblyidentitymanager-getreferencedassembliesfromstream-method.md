---
description: '詳細について: ICLRAssemblyIdentityManager:: GetReferencedAssembliesFromStream メソッド'
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
ms.openlocfilehash: 9173587125e7b528e203dcb7e6a19d3e3f2fb990
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746114"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="5f313-103">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="5f313-103">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>

<span data-ttu-id="5f313-104">指定したストリーム内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納する [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) オブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5f313-104">Gets a pointer to an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f313-105">構文</span><span class="sxs-lookup"><span data-stu-id="5f313-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f313-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5f313-106">Parameters</span></span>  

 `pStream`  
 <span data-ttu-id="5f313-107">から `IStream` 評価されるアセンブリを格納しているへのインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="5f313-107">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5f313-108">から将来の拡張のために提供されます。</span><span class="sxs-lookup"><span data-stu-id="5f313-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="5f313-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンでサポートされている唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="5f313-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="5f313-110">から除外されるアセンブリのアセンブリ id データを格納する [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) オブジェクトへのポインター `ppReferenceEnum` 。</span><span class="sxs-lookup"><span data-stu-id="5f313-110">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="5f313-111">入出力内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納するオブジェクトのアドレスへのポインター `ICLRReferenceAssemblyEnum` `pStream` (内のアセンブリは除く) `pExcludeAssembliesList` 。</span><span class="sxs-lookup"><span data-stu-id="5f313-111">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f313-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="5f313-112">Return Value</span></span>  
  
|<span data-ttu-id="5f313-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f313-113">HRESULT</span></span>|<span data-ttu-id="5f313-114">説明</span><span class="sxs-lookup"><span data-stu-id="5f313-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f313-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f313-115">S_OK</span></span>|<span data-ttu-id="5f313-116">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="5f313-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="5f313-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5f313-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5f313-118">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="5f313-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5f313-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5f313-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5f313-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5f313-120">The call timed out.</span></span>|  
|<span data-ttu-id="5f313-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5f313-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5f313-122">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5f313-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5f313-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5f313-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5f313-124">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="5f313-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5f313-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5f313-125">E_FAIL</span></span>|<span data-ttu-id="5f313-126">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5f313-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5f313-127">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5f313-127">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5f313-128">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="5f313-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f313-129">解説</span><span class="sxs-lookup"><span data-stu-id="5f313-129">Remarks</span></span>  

 <span data-ttu-id="5f313-130">呼び出し元は、返された一覧から一連の既知のアセンブリ参照を除外することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="5f313-130">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="5f313-131">このセットはによって定義され `pExcludeAssembliesList` ます。</span><span class="sxs-lookup"><span data-stu-id="5f313-131">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f313-132">要件</span><span class="sxs-lookup"><span data-stu-id="5f313-132">Requirements</span></span>  

 <span data-ttu-id="5f313-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f313-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f313-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5f313-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f313-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5f313-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f313-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f313-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f313-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f313-137">See also</span></span>

- [<span data-ttu-id="5f313-138">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f313-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="5f313-139">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f313-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="5f313-140">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f313-140">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
