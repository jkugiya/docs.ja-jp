---
description: '詳細について: IMetaDataImport2:: GetGenericParamConstraintProps メソッド'
title: IMetaDataImport2::GetGenericParamConstraintProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
ms.openlocfilehash: 03cc4df655f9ab7a1c04840e9d4fa782a90ce1ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688742"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="e8edd-103">IMetaDataImport2::GetGenericParamConstraintProps メソッド</span><span class="sxs-lookup"><span data-stu-id="e8edd-103">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>

<span data-ttu-id="e8edd-104">指定された制約トークンによって表されるジェネリックパラメーター制約に関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="e8edd-104">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8edd-105">構文</span><span class="sxs-lookup"><span data-stu-id="e8edd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8edd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e8edd-106">Parameters</span></span>  

 `gpc`  
 <span data-ttu-id="e8edd-107">からメタデータを返す対象のジェネリックパラメーター制約へのトークン。</span><span class="sxs-lookup"><span data-stu-id="e8edd-107">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="e8edd-108">入出力制約されているジェネリックパラメーターを表すトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e8edd-108">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="e8edd-109">入出力の制約を表す TypeDef、TypeRef、または TypeSpec トークンへのポインター `ptGenericParam` 。</span><span class="sxs-lookup"><span data-stu-id="e8edd-109">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8edd-110">要件</span><span class="sxs-lookup"><span data-stu-id="e8edd-110">Requirements</span></span>  

 <span data-ttu-id="e8edd-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8edd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8edd-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e8edd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8edd-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8edd-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8edd-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8edd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8edd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8edd-115">See also</span></span>

- [<span data-ttu-id="e8edd-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8edd-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="e8edd-117">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8edd-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
