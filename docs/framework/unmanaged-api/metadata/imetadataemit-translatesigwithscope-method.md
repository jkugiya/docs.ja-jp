---
description: '詳細について: IMetaDataEmit:: TranslateSigWithScope メソッド'
title: IMetaDataEmit::TranslateSigWithScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
ms.openlocfilehash: e5f4e522e993f2f391ca0c29e5fcc2cbb71775e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720932"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="cd45c-103">IMetaDataEmit::TranslateSigWithScope メソッド</span><span class="sxs-lookup"><span data-stu-id="cd45c-103">IMetaDataEmit::TranslateSigWithScope Method</span></span>

<span data-ttu-id="cd45c-104">現在のスコープにアセンブリをインポートし、マージされたスコープの新しいメタデータシグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="cd45c-104">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd45c-105">構文</span><span class="sxs-lookup"><span data-stu-id="cd45c-105">Syntax</span></span>  
  
```cpp  
HRESULT TranslateSigWithScope (
    [in]  IMetaDataAssemblyImport   *pAssemImport,
    [in]  const void                *pbHashValue,
    [in]  ULONG                     cbHashValue,
    [in]  IMetaDataImport           *import,
    [in]  PCCOR_SIGNATURE           pbSigBlob,
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,
    [in]  IMetaDataEmit             *emit,
    [out] PCOR_SIGNATURE            pvTranslatedSig,
    [in]  ULONG                     cbTranslatedSigMax,
    [out] ULONG                     *pcbTranslatedSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd45c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd45c-106">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="cd45c-107">からインポートアセンブリのインターフェイス (シグネチャが定義されている場合)。</span><span class="sxs-lookup"><span data-stu-id="cd45c-107">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="cd45c-108">からアセンブリのハッシュ blob。</span><span class="sxs-lookup"><span data-stu-id="cd45c-108">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="cd45c-109">からのバイト数 `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="cd45c-109">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="cd45c-110">からインポートメタデータスコープのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="cd45c-110">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="cd45c-111">からインポートされる署名。</span><span class="sxs-lookup"><span data-stu-id="cd45c-111">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="cd45c-112">からのサイズ (バイト単位) `pbSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="cd45c-112">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="cd45c-113">からエクスポートアセンブリのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="cd45c-113">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="cd45c-114">からエクスポートメタデータスコープのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="cd45c-114">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="cd45c-115">入出力変換された署名 blob を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="cd45c-115">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="cd45c-116">からの容量 (バイト単位) `pvTranslatedSig` 。</span><span class="sxs-lookup"><span data-stu-id="cd45c-116">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="cd45c-117">入出力変換されたシグネチャの実際のバイト数。</span><span class="sxs-lookup"><span data-stu-id="cd45c-117">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd45c-118">要件</span><span class="sxs-lookup"><span data-stu-id="cd45c-118">Requirements</span></span>  

 <span data-ttu-id="cd45c-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd45c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd45c-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="cd45c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd45c-121">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd45c-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd45c-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd45c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd45c-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd45c-123">See also</span></span>

- [<span data-ttu-id="cd45c-124">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd45c-124">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="cd45c-125">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd45c-125">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="cd45c-126">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd45c-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="cd45c-127">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd45c-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="cd45c-128">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd45c-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
