---
description: '詳細について: IMetaDataImport2:: EnumGenericParamConstraints メソッド'
title: IMetaDataImport2::EnumGenericParamConstraints メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
ms.openlocfilehash: d7ee44059796a943411750b66f5b45034f871a0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677549"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="a5627-103">IMetaDataImport2::EnumGenericParamConstraints メソッド</span><span class="sxs-lookup"><span data-stu-id="a5627-103">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>

<span data-ttu-id="a5627-104">指定したトークンによって表されるジェネリックパラメーターに関連付けられているジェネリックパラメーター制約の配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5627-104">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5627-105">構文</span><span class="sxs-lookup"><span data-stu-id="a5627-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5627-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5627-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="a5627-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a5627-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="a5627-108">から  制約を列挙するジェネリックパラメーターを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="a5627-108">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="a5627-109">入出力列挙するジェネリックパラメーター制約の配列。</span><span class="sxs-lookup"><span data-stu-id="a5627-109">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a5627-110">から  に格納するトークンの要求された最大数 `rGenericParamConstraints` 。</span><span class="sxs-lookup"><span data-stu-id="a5627-110">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="a5627-111">入出力に格納されているトークンの数へのポインター `rGenericParamConstraints` 。</span><span class="sxs-lookup"><span data-stu-id="a5627-111">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5627-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="a5627-112">Return Value</span></span>  
  
|<span data-ttu-id="a5627-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5627-113">HRESULT</span></span>|<span data-ttu-id="a5627-114">説明</span><span class="sxs-lookup"><span data-stu-id="a5627-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a5627-115">`EnumGenericParameterConstraints` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="a5627-115">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a5627-116">`phEnum` にメンバー要素がありません。</span><span class="sxs-lookup"><span data-stu-id="a5627-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="a5627-117">この場合、 `pcGenericParameterConstraints` は 0 (ゼロ) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a5627-117">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5627-118">要件</span><span class="sxs-lookup"><span data-stu-id="a5627-118">Requirements</span></span>  

 <span data-ttu-id="a5627-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5627-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5627-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="a5627-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5627-121">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5627-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5627-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5627-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5627-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5627-123">See also</span></span>

- [<span data-ttu-id="a5627-124">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5627-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="a5627-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5627-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
