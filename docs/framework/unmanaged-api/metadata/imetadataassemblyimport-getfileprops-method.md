---
description: '詳細について: IMetaDataAssemblyImport:: GetFileProps メソッド'
title: IMetaDataAssemblyImport::GetFileProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: 6814fee7edf5478a1ce2cf2b81d8f16fa62cd3f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784107"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="8a7cb-103">IMetaDataAssemblyImport::GetFileProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8a7cb-103">IMetaDataAssemblyImport::GetFileProps Method</span></span>

<span data-ttu-id="8a7cb-104">指定したメタデータシグネチャを持つファイルのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-104">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a7cb-105">構文</span><span class="sxs-lookup"><span data-stu-id="8a7cb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a7cb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a7cb-106">Parameters</span></span>  

 `mdf`  
 <span data-ttu-id="8a7cb-107">から `mdFile` プロパティを取得する対象のファイルを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-107">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a7cb-108">入出力ファイルの簡易名。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-108">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8a7cb-109">からのサイズ (ワイド文字数) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-109">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8a7cb-110">入出力実際にで返されるワイド文字数 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-110">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="8a7cb-111">入出力ハッシュ値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-111">[out] A pointer to the hash value.</span></span> <span data-ttu-id="8a7cb-112">これは、ファイルの SHA-1 アルゴリズムを使用したハッシュです。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-112">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="8a7cb-113">入出力返されたハッシュ値のワイド文字の数。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-113">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="8a7cb-114">入出力ファイルに適用されるメタデータを記述するフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-114">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="8a7cb-115">Flags 値は、1つまたは複数の [Corfileflags](corfileflags-enumeration.md) 値を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-115">The flags value is a combination of one or more [CorFileFlags](corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a7cb-116">要件</span><span class="sxs-lookup"><span data-stu-id="8a7cb-116">Requirements</span></span>  

 <span data-ttu-id="8a7cb-117">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-117">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a7cb-118">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8a7cb-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a7cb-119">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a7cb-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a7cb-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a7cb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7cb-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a7cb-121">See also</span></span>

- [<span data-ttu-id="8a7cb-122">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a7cb-122">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
