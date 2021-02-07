---
description: '詳細について: IMetaDataAssemblyImport:: GetManifestResourceProps メソッド'
title: IMetaDataAssemblyImport::GetManifestResourceProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: d8f390f8eede5153df282cc30479ceff22fb552d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728287"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="8a698-103">IMetaDataAssemblyImport::GetManifestResourceProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8a698-103">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>

<span data-ttu-id="8a698-104">指定されたメタデータシグネチャを持つマニフェストリソースのプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a698-104">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a698-105">構文</span><span class="sxs-lookup"><span data-stu-id="8a698-105">Syntax</span></span>  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a698-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a698-106">Parameters</span></span>  

 `mdmr`  
 <span data-ttu-id="8a698-107">から `mdManifestResource` プロパティを取得する対象のリソースを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="8a698-107">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a698-108">入出力リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="8a698-108">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8a698-109">からのサイズ (ワイド文字数) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="8a698-109">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8a698-110">入出力実際にで返されるワイド文字数へのポインター `szName` 。</span><span class="sxs-lookup"><span data-stu-id="8a698-110">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="8a698-111">入出力リソースを格納し `mdFile` `mdAssemblyRef` ているファイルまたはアセンブリを表すトークンまたはトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8a698-111">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="8a698-112">入出力ファイル内のリソースの先頭へのオフセットを指定する値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8a698-112">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="8a698-113">入出力リソースに適用されるメタデータを記述するフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8a698-113">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="8a698-114">Flags 値は、1つ以上の [Cormanifestresourceflags](cormanifestresourceflags-enumeration.md) 値を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="8a698-114">The flags value is a combination of one or more [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a698-115">要件</span><span class="sxs-lookup"><span data-stu-id="8a698-115">Requirements</span></span>  

 <span data-ttu-id="8a698-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a698-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a698-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8a698-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a698-118">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a698-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a698-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a698-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a698-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a698-120">See also</span></span>

- [<span data-ttu-id="8a698-121">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a698-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
