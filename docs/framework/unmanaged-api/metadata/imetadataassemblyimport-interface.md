---
description: 詳細については、「IMetaDataAssemblyImport インターフェイス」を参照してください。
title: IMetaDataAssemblyImport インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: bb9c5163e4f5b68700e5a3836fa55edbbebac01c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753641"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="196a5-103">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="196a5-103">IMetaDataAssemblyImport Interface</span></span>

<span data-ttu-id="196a5-104">アセンブリ マニフェストの内容にアクセスして確認するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="196a5-104">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="196a5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-105">Methods</span></span>  
  
|<span data-ttu-id="196a5-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-106">Method</span></span>|<span data-ttu-id="196a5-107">説明</span><span class="sxs-lookup"><span data-stu-id="196a5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="196a5-108">CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-108">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="196a5-109">指定した列挙子へのハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="196a5-109">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="196a5-110">EnumAssemblyRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-110">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="196a5-111">`mdAssemblyRef`現在のメタデータスコープ内のアセンブリによって参照されるアセンブリのトークンを格納している列挙子へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-111">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="196a5-112">EnumExportedTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-112">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="196a5-113">`mdExportedType`現在のメタデータスコープ内のアセンブリによって参照される COM 型のトークンを格納している列挙子へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-113">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="196a5-114">EnumFiles メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-114">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="196a5-115">`mdFile`現在のメタデータスコープ内のアセンブリによって参照されるファイルのトークンを格納している列挙子へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-115">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="196a5-116">EnumManifestResources メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-116">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="196a5-117">`mdManifestResource`現在のメタデータスコープ内のアセンブリによって参照されているリソースのトークンを格納している列挙子へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-117">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="196a5-118">FindAssembliesByName メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-118">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="196a5-119">`mdAssemblyRef`指定した名前のアセンブリのトークンの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-119">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="196a5-120">FindExportedTypeByName メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-120">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="196a5-121">指定し `mdExportedType` た名前の COM 型のトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-121">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="196a5-122">FindManifestResourceByName メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-122">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="196a5-123">指定し `mdManifestResource` た名前のリソースのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-123">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="196a5-124">GetAssemblyFromScope メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-124">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="196a5-125">現在のメタデータスコープ内のアセンブリのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-125">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="196a5-126">GetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-126">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="196a5-127">指定したアセンブリのプロパティ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-127">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="196a5-128">GetAssemblyRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-128">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="196a5-129">指定したトークンのプロパティ設定を取得し `mdAssemblyRef` ます。</span><span class="sxs-lookup"><span data-stu-id="196a5-129">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="196a5-130">GetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-130">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="196a5-131">指定した COM 型のプロパティ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-131">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="196a5-132">GetFileProps メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-132">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="196a5-133">指定されたファイルのプロパティ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-133">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="196a5-134">GetManifestResourceProps メソッド</span><span class="sxs-lookup"><span data-stu-id="196a5-134">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="196a5-135">指定されたマニフェストリソースのプロパティ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="196a5-135">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="196a5-136">要件</span><span class="sxs-lookup"><span data-stu-id="196a5-136">Requirements</span></span>  

 <span data-ttu-id="196a5-137">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="196a5-137">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="196a5-138">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="196a5-138">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="196a5-139">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="196a5-139">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="196a5-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="196a5-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="196a5-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="196a5-141">See also</span></span>

- [<span data-ttu-id="196a5-142">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="196a5-142">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="196a5-143">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="196a5-143">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
