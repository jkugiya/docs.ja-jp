---
description: '詳細について: ICorProfilerInfo7:: ApplyMetaData メソッド'
title: 'ICorProfilerInfo7:: ApplyMetaData メソッド'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: 3a4554357ede85d936e8bf9c87c6b9c096dab188
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737130"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="3fb98-103">ICorProfilerInfo7:: ApplyMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="3fb98-103">ICorProfilerInfo7::ApplyMetaData Method</span></span>

<span data-ttu-id="3fb98-104">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="3fb98-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="3fb98-105">メソッドによって新たに定義されたメタデータ `IMetadataEmit::Define*` を、指定したモジュールに適用します。</span><span class="sxs-lookup"><span data-stu-id="3fb98-105">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb98-106">構文</span><span class="sxs-lookup"><span data-stu-id="3fb98-106">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fb98-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3fb98-107">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="3fb98-108">からメタデータが変更されたモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="3fb98-108">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fb98-109">解説</span><span class="sxs-lookup"><span data-stu-id="3fb98-109">Remarks</span></span>  

 <span data-ttu-id="3fb98-110">[Moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md)コールバックの後にメタデータの変更が行われた場合は、新しいメタデータを使用する前にこのメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fb98-110">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="3fb98-111">`ApplyMetaData` では、次の種類のメタデータの追加のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3fb98-111">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="3fb98-112">`AssemblyRef`[IMetaDataAssemblyEmit::D efineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md)を呼び出すことによって作成するレコード。</span><span class="sxs-lookup"><span data-stu-id="3fb98-112">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="3fb98-113">メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3fb98-113">method.</span></span>  
  
- <span data-ttu-id="3fb98-114">`TypeRef`[IMetaDataEmit::D efinetyperefbyname](../metadata/imetadataemit-definetyperefbyname-method.md)メソッドを呼び出すことによって作成するレコード。</span><span class="sxs-lookup"><span data-stu-id="3fb98-114">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="3fb98-115">`TypeSpec` レコード。 [IMetaDataEmit:: GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) メソッドを呼び出すことによって作成します。</span><span class="sxs-lookup"><span data-stu-id="3fb98-115">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="3fb98-116">`MemberRef`[IMetaDataEmit::D efinememberref](../metadata/imetadataemit-definememberref-method.md)メソッドを呼び出すことによって作成するレコード。</span><span class="sxs-lookup"><span data-stu-id="3fb98-116">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="3fb98-117">`MemberSpec`[IMetaDataEmit2::D efinemethodspec](../metadata/imetadataemit2-definemethodspec-method.md)メソッドを呼び出すことによって作成するレコード。</span><span class="sxs-lookup"><span data-stu-id="3fb98-117">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="3fb98-118">`UserString` レコード。 [IMetaDataEmit::D efineUserString](../metadata/imetadataemit-defineuserstring-method.md) メソッドを呼び出すことによって作成します。</span><span class="sxs-lookup"><span data-stu-id="3fb98-118">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="3fb98-119">.NET Core 3.0 以降では、 `ApplyMetaData` 次の型もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3fb98-119">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="3fb98-120">`TypeDef`[IMetaDataEmit::D efineTypeDef](../metadata/imetadataemit-definetypedef-method.md)メソッドを呼び出すことによって作成するレコード。</span><span class="sxs-lookup"><span data-stu-id="3fb98-120">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="3fb98-121">`MethodDef`[IMetaDataEmit::D efinemethod](../metadata/imetadataemit-definemethod-method.md)メソッドを呼び出すことによって作成するレコード。</span><span class="sxs-lookup"><span data-stu-id="3fb98-121">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="3fb98-122">ただし、既存の型に仮想メソッドを追加することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3fb98-122">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="3fb98-123">仮想メソッドは、 [Moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md) コールバックの前に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fb98-123">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="3fb98-124">要件</span><span class="sxs-lookup"><span data-stu-id="3fb98-124">Requirements</span></span>  

 <span data-ttu-id="3fb98-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fb98-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fb98-126">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3fb98-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3fb98-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fb98-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fb98-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb98-128">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb98-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fb98-129">See also</span></span>

- [<span data-ttu-id="3fb98-130">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fb98-130">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
