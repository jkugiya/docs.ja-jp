---
description: '詳細について: IMetaDataAssemblyImport:: GetAssemblyProps メソッド'
title: IMetaDataAssemblyImport::GetAssemblyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: 9cd3674dcd640bce27ae5d399d0f7de0c2eeca48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784146"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="becb7-103">IMetaDataAssemblyImport::GetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="becb7-103">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>

<span data-ttu-id="becb7-104">指定したメタデータシグネチャを持つアセンブリのプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="becb7-104">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="becb7-105">構文</span><span class="sxs-lookup"><span data-stu-id="becb7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="becb7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="becb7-106">Parameters</span></span>  

 `mda`  
 <span data-ttu-id="becb7-107">[入力]。</span><span class="sxs-lookup"><span data-stu-id="becb7-107">[in].</span></span> <span data-ttu-id="becb7-108">`mdAssembly`プロパティを取得する対象のアセンブリを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="becb7-108">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="becb7-109">入出力公開キーまたはメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="becb7-109">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="becb7-110">入出力返される公開キーのバイト数。</span><span class="sxs-lookup"><span data-stu-id="becb7-110">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="becb7-111">入出力アセンブリ内のファイルのハッシュに使用されるアルゴリズムへのポインター。</span><span class="sxs-lookup"><span data-stu-id="becb7-111">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="becb7-112">入出力アセンブリの簡易名。</span><span class="sxs-lookup"><span data-stu-id="becb7-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="becb7-113">からのサイズ (ワイド文字数) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="becb7-113">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="becb7-114">入出力実際にで返されるワイド文字数 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="becb7-114">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="becb7-115">入出力アセンブリメタデータを格納している ASSEMBLYMETADATA 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="becb7-115">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="becb7-116">入出力アセンブリに適用されるメタデータを記述するフラグ。</span><span class="sxs-lookup"><span data-stu-id="becb7-116">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="becb7-117">この値は、1つまたは複数の [Corassemblyflags](corassemblyflags-enumeration.md) 値を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="becb7-117">This value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="becb7-118">要件</span><span class="sxs-lookup"><span data-stu-id="becb7-118">Requirements</span></span>  

 <span data-ttu-id="becb7-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="becb7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="becb7-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="becb7-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="becb7-121">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="becb7-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="becb7-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="becb7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="becb7-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="becb7-123">See also</span></span>

- [<span data-ttu-id="becb7-124">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="becb7-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
