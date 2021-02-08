---
description: '詳細について: IMetaDataAssemblyImport:: FindManifestResourceByName メソッド'
title: IMetaDataAssemblyImport::FindManifestResourceByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
ms.openlocfilehash: 1d1312277675a1f2bf213221ab8d9d2a584733a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784172"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="857bf-103">IMetaDataAssemblyImport::FindManifestResourceByName メソッド</span><span class="sxs-lookup"><span data-stu-id="857bf-103">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>

<span data-ttu-id="857bf-104">指定した名前のマニフェストリソースへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="857bf-104">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="857bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="857bf-105">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="857bf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="857bf-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="857bf-107">からリソースの名前。</span><span class="sxs-lookup"><span data-stu-id="857bf-107">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="857bf-108">入出力メタデータトークンを格納するために使用される配列 `mdManifestResource` 。それぞれがマニフェストリソースを表します。</span><span class="sxs-lookup"><span data-stu-id="857bf-108">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="857bf-109">解説</span><span class="sxs-lookup"><span data-stu-id="857bf-109">Remarks</span></span>  

 <span data-ttu-id="857bf-110">メソッドは、 `FindManifestResourceByName` 参照を解決するために共通言語ランタイムによって採用されている標準の規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="857bf-110">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="857bf-111">要件</span><span class="sxs-lookup"><span data-stu-id="857bf-111">Requirements</span></span>  

 <span data-ttu-id="857bf-112">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="857bf-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="857bf-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="857bf-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="857bf-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="857bf-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="857bf-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="857bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="857bf-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="857bf-116">See also</span></span>

- [<span data-ttu-id="857bf-117">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="857bf-117">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="857bf-118">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="857bf-118">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
