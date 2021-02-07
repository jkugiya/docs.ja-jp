---
description: 詳細については、「IMetaDataAssemblyEmit インターフェイス」を参照してください。
title: IMetaDataAssemblyEmit インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: bcfca4eedc14f2292c40874d86c4984b4c1948f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678212"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="00574-103">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00574-103">IMetaDataAssemblyEmit Interface</span></span>

<span data-ttu-id="00574-104">共通言語ランタイムがリソースの解決および消費に使用する自己記述モデルをサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="00574-104">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00574-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-105">Methods</span></span>  
  
|<span data-ttu-id="00574-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-106">Method</span></span>|<span data-ttu-id="00574-107">説明</span><span class="sxs-lookup"><span data-stu-id="00574-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00574-108">DefineAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-108">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="00574-109">指定したアセンブリのメタデータを含むアセンブリ データ構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="00574-109">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="00574-110">DefineAssemblyRef メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-110">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="00574-111">このアセンブリが参照するアセンブリのメタデータを含む `AssemblyRef` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="00574-111">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="00574-112">DefineExportedType メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-112">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="00574-113">指定してエクスポートした型のメタデータが含まれる `ExportedType` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="00574-113">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="00574-114">DefineFile メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-114">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="00574-115">このアセンブリが参照するアセンブリのメタデータを含む `File` メタデータ構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="00574-115">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="00574-116">DefineManifestResource メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-116">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="00574-117">指定したマニフェスト リソースのメタデータを含む `ManifestResource` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="00574-117">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="00574-118">SetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-118">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="00574-119">指定された `Assembly` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="00574-119">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="00574-120">SetAssemblyRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-120">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="00574-121">指定された `AssemblyRef` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="00574-121">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="00574-122">SetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-122">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="00574-123">指定された `ExportedType` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="00574-123">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="00574-124">SetFileProps メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-124">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="00574-125">指定された `File` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="00574-125">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="00574-126">SetManifestResourceProps メソッド</span><span class="sxs-lookup"><span data-stu-id="00574-126">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="00574-127">指定された `ManifestResource` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="00574-127">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00574-128">解説</span><span class="sxs-lookup"><span data-stu-id="00574-128">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00574-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="00574-129">Requirements</span></span>  

 <span data-ttu-id="00574-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00574-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00574-131">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="00574-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00574-132">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="00574-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00574-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00574-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00574-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="00574-134">See also</span></span>

- [<span data-ttu-id="00574-135">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00574-135">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="00574-136">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00574-136">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
