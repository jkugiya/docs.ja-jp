---
description: '詳細について: IHostAssemblyStore::P rovideAssembly メソッド'
title: IHostAssemblyStore::ProvideAssembly メソッド
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
ms.openlocfilehash: f8917cb28dd3898343a7b6ee08bd54096df8cfa7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789503"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="44d5f-103">IHostAssemblyStore::ProvideAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="44d5f-103">IHostAssemblyStore::ProvideAssembly Method</span></span>

<span data-ttu-id="44d5f-104">[IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)から返された[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)によって参照されていないアセンブリへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="44d5f-104">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="44d5f-105">共通言語ランタイム (CLR) は、 `ProvideAssembly` 一覧に表示されない各アセンブリに対してを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="44d5f-105">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d5f-106">構文</span><span class="sxs-lookup"><span data-stu-id="44d5f-106">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44d5f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="44d5f-107">Parameters</span></span>  

 `pBindInfo`  
 <span data-ttu-id="44d5f-108">からホストが特定のバインド特性 (バージョン管理ポリシーの有無、バインド先のアセンブリなど) を決定するために使用する [Assemblybindinfo](assemblybindinfo-structure.md) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="44d5f-108">[in] A pointer to an [AssemblyBindInfo](assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="44d5f-109">入出力このの要求されたアセンブリの一意の識別子へのポインター `IStream` 。</span><span class="sxs-lookup"><span data-stu-id="44d5f-109">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="44d5f-110">入出力プラットフォーム呼び出しを必要とせずに、要求されたアセンブリの証拠を決定するために使用されるホスト固有のデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="44d5f-110">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="44d5f-111">`pHostContext`<xref:System.Reflection.Assembly.HostContext%2A>マネージクラスのプロパティに対応 <xref:System.Reflection.Assembly> します。</span><span class="sxs-lookup"><span data-stu-id="44d5f-111">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="44d5f-112">入出力 `IStream` 読み込むポータブル実行可能 (PE) イメージが格納されているのアドレスへのポインター。アセンブリが見つからなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="44d5f-112">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="44d5f-113">入出力プログラムデバッグ (PDB) 情報を格納しているのアドレスへのポインター、 `IStream` または .pdb ファイルが見つからなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="44d5f-113">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44d5f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="44d5f-114">Return Value</span></span>  
  
|<span data-ttu-id="44d5f-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44d5f-115">HRESULT</span></span>|<span data-ttu-id="44d5f-116">説明</span><span class="sxs-lookup"><span data-stu-id="44d5f-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44d5f-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="44d5f-117">S_OK</span></span>|<span data-ttu-id="44d5f-118">`ProvideAssembly` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="44d5f-118">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="44d5f-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44d5f-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44d5f-120">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="44d5f-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44d5f-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44d5f-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44d5f-122">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="44d5f-122">The call timed out.</span></span>|  
|<span data-ttu-id="44d5f-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44d5f-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44d5f-124">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="44d5f-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44d5f-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44d5f-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44d5f-126">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="44d5f-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44d5f-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44d5f-127">E_FAIL</span></span>|<span data-ttu-id="44d5f-128">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="44d5f-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44d5f-129">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="44d5f-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44d5f-130">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="44d5f-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="44d5f-131">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="44d5f-131">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="44d5f-132">要求されたアセンブリが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="44d5f-132">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="44d5f-133">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="44d5f-133">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="44d5f-134">によって指定されたバッファーサイズ `pAssemblyId` が、ホストが返す識別子を保持するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="44d5f-134">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44d5f-135">解説</span><span class="sxs-lookup"><span data-stu-id="44d5f-135">Remarks</span></span>  

 <span data-ttu-id="44d5f-136">に対して返される id 値 `pAssemblyId` は、ホストによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="44d5f-136">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="44d5f-137">識別子は、プロセスの有効期間内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="44d5f-137">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="44d5f-138">CLR は、この値をストリームの一意の識別子として使用します。</span><span class="sxs-lookup"><span data-stu-id="44d5f-138">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="44d5f-139">このメソッドは、 `pAssemblyId` の他の呼び出しによって返された値と比較して、それぞれの値をチェック `ProvideAssembly` します。</span><span class="sxs-lookup"><span data-stu-id="44d5f-139">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="44d5f-140">ホストが別のと同じ値を返す場合、 `pAssemblyId` `IStream` CLR は、そのストリームの内容が既にマップされているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="44d5f-140">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="44d5f-141">その場合、ランタイムは新しいイメージをマップするのではなく、イメージの既存のコピーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="44d5f-141">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44d5f-142">要件</span><span class="sxs-lookup"><span data-stu-id="44d5f-142">Requirements</span></span>  

 <span data-ttu-id="44d5f-143">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44d5f-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d5f-144">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="44d5f-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44d5f-145">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="44d5f-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44d5f-146">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d5f-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d5f-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="44d5f-147">See also</span></span>

- [<span data-ttu-id="44d5f-148">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44d5f-148">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="44d5f-149">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44d5f-149">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="44d5f-150">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44d5f-150">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
