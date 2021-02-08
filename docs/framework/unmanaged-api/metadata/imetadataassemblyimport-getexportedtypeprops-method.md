---
description: '詳細について: IMetaDataAssemblyImport:: GetExportedTypeProps メソッド'
title: IMetaDataAssemblyImport::GetExportedTypeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 894fb65fb6de76a218489b2a85a2d3c20c572789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784120"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="ecdfb-103">IMetaDataAssemblyImport::GetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="ecdfb-103">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>

<span data-ttu-id="ecdfb-104">指定したメタデータシグネチャを持つ、エクスポートされた型のプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="ecdfb-104">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecdfb-105">構文</span><span class="sxs-lookup"><span data-stu-id="ecdfb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,
    [out] LPWSTR            szName,
    [in]  ULONG             cchName,
    [out] ULONG             *pchName,
    [out] mdToken           *ptkImplementation,
    [out] mdTypeDef         *ptkTypeDef,
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecdfb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ecdfb-106">Parameters</span></span>  

 `mdct`  
 <span data-ttu-id="ecdfb-107">からエクスポートされた `mdExportedType` 型を表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="ecdfb-107">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="ecdfb-108">入出力エクスポートされた型の名前。</span><span class="sxs-lookup"><span data-stu-id="ecdfb-108">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ecdfb-109">からのサイズ (ワイド文字単位) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="ecdfb-109">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="ecdfb-110">入出力実際に返されるワイド文字の数 `szName`</span><span class="sxs-lookup"><span data-stu-id="ecdfb-110">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="ecdfb-111">入出力 `mdFile` `mdAssemblyRef` エクスポートされた `mdExportedType` 型のプロパティへのアクセスを格納または許可する、、、またはメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="ecdfb-111">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="ecdfb-112">入出力 `mdTypeDef` ファイル内の型を表すトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ecdfb-112">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="ecdfb-113">入出力エクスポートされた型に適用されるメタデータを記述するフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ecdfb-113">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="ecdfb-114">Flags 値には、1つまたは複数の [Cortypeattr](cortypeattr-enumeration.md) 値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ecdfb-114">The flags value can be one or more [CorTypeAttr](cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecdfb-115">要件</span><span class="sxs-lookup"><span data-stu-id="ecdfb-115">Requirements</span></span>  

 <span data-ttu-id="ecdfb-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecdfb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecdfb-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="ecdfb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecdfb-118">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="ecdfb-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ecdfb-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecdfb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecdfb-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecdfb-120">See also</span></span>

- [<span data-ttu-id="ecdfb-121">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ecdfb-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
