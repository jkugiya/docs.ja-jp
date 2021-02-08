---
description: '詳細について: ICorProfilerCallback6:: GetAssemblyReferences メソッド'
title: ICorProfilerCallback6::GetAssemblyReferences メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
ms.openlocfilehash: 27c2b5e0ed935501de551bac32b6d229d5c59f79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788645"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="0f611-103">ICorProfilerCallback6::GetAssemblyReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="0f611-103">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>

<span data-ttu-id="0f611-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="0f611-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0f611-105">共通言語ランタイムがアセンブリ参照クロージャのウォークを実行するときに、アセンブリがごく初期のローディング状態であることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0f611-105">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f611-106">構文</span><span class="sxs-lookup"><span data-stu-id="0f611-106">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f611-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f611-107">Parameters</span></span>  

 `wszAssemblyPath`  
 <span data-ttu-id="0f611-108">[in] メタデータが変更されるアセンブリのパスおよび名前。</span><span class="sxs-lookup"><span data-stu-id="0f611-108">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="0f611-109">から追加するアセンブリ参照を指定する [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) インターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f611-109">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f611-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="0f611-110">Return Value</span></span>  

 <span data-ttu-id="0f611-111">このコールバックからの戻り値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="0f611-111">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f611-112">解説</span><span class="sxs-lookup"><span data-stu-id="0f611-112">Remarks</span></span>  

 <span data-ttu-id="0f611-113">このコールバックは、 [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)メソッドを呼び出すときに、 [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md)イベントマスクフラグを設定することによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="0f611-113">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="0f611-114">プロファイラーが [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback メソッドを登録すると、ランタイムは、読み込まれるアセンブリのパスと名前、およびそのメソッドへの [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) インターフェイスオブジェクトへのポインターを渡します。</span><span class="sxs-lookup"><span data-stu-id="0f611-114">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="0f611-115">その後、プロファイラーは、 [](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) `COR_PRF_ASSEMBLY_REFERENCE_INFO` コールバックで指定されたアセンブリから参照するターゲットアセンブリごとに、オブジェクトを使用して ICorProfilerAssemblyReferenceProvider:: addassemblyreference メソッドを呼び出すことができます `GetAssemblyReferences` 。</span><span class="sxs-lookup"><span data-stu-id="0f611-115">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="0f611-116">`GetAssemblyReferences` コールバックを使用するのは、プロファイラーがアセンブリのメタデータを変更してアセンブリ参照を追加する必要がある場合のみです</span><span class="sxs-lookup"><span data-stu-id="0f611-116">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="0f611-117">(ただし、アセンブリのメタデータの実際の変更は、 [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)コールバックメソッドで行われることに注意してください)。プロファイラーは、 `GetAssemblyReferences` モジュールが読み込まれたときにアセンブリ参照が追加されることを共通言語ランタイム (CLR) に通知するために、コールバックメソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f611-117">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="0f611-118">これにより、プロファイラーが後でメタデータのアセンブリ参照を変更するつもりでも、アセンブリが共有している "初期の段階で CLR によって行われた決定" は有効なままになります。</span><span class="sxs-lookup"><span data-stu-id="0f611-118">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="0f611-119">このため一部のインスタンスでの、プロファイラーのメタデータ変更による `SECURITY_E_INCOMPATIBLE_SHARE` エラーの発生を回避できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0f611-119">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="0f611-120">プロファイラーは、このメソッドによって提供される [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) オブジェクトを使用して、CLR アセンブリ参照クロージャのウォーカーにアセンブリ参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="0f611-120">The profiler uses the [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="0f611-121">[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)オブジェクトは、このコールバック内からのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f611-121">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="0f611-122">このコールバックから [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) メソッドを呼び出すと、変更されたメタデータは生成されませんが、変更されたアセンブリ参照クロージャウォークでのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="0f611-122">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="0f611-123">また、コールバックが実装され[](../metadata/imetadataassemblyemit-interface.md)ている場合でも、参照元のアセンブリの[ICorProfilerCallback:: moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md)コールバック内からアセンブリ参照を明示的に追加するには、プロファイラーでは、そのオブジェクトを使用する必要があり `GetAssemblyReferences` ます。</span><span class="sxs-lookup"><span data-stu-id="0f611-123">The profiler will still have to use an [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="0f611-124">プロファイラーは、同じアセンブリに対してこのコールバックへの重複する呼び出しを受け取るように準備する必要があります。また、同じ [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) 呼び出しのセットを作成することによって、重複する各呼び出しに対して同じように応答する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f611-124">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f611-125">要件</span><span class="sxs-lookup"><span data-stu-id="0f611-125">Requirements</span></span>  

 <span data-ttu-id="0f611-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f611-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f611-127">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f611-127">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f611-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f611-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f611-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f611-129">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f611-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f611-130">See also</span></span>

- [<span data-ttu-id="0f611-131">ICorProfilerCallback6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f611-131">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)
- [<span data-ttu-id="0f611-132">ModuleLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="0f611-132">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="0f611-133">COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="0f611-133">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)
- [<span data-ttu-id="0f611-134">ICorProfilerAssemblyReferenceProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f611-134">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
