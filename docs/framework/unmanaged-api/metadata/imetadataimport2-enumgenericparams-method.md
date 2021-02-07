---
description: '詳細情報: IMetaDataImport2:: EnumGenericParams メソッド'
title: IMetaDataImport2::EnumGenericParams メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 9d4e9d163da07ec4a3af1aa628b8b6ec4b2338fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720944"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="be59a-103">IMetaDataImport2::EnumGenericParams メソッド</span><span class="sxs-lookup"><span data-stu-id="be59a-103">IMetaDataImport2::EnumGenericParams Method</span></span>

<span data-ttu-id="be59a-104">指定した TypeDef または MethodDef トークンに関連付けられているジェネリックパラメータートークンの配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="be59a-104">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be59a-105">構文</span><span class="sxs-lookup"><span data-stu-id="be59a-105">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be59a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be59a-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="be59a-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="be59a-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="be59a-108">からジェネリックパラメーターを列挙する TypeDef または MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="be59a-108">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="be59a-109">入出力列挙するジェネリックパラメーターの配列。</span><span class="sxs-lookup"><span data-stu-id="be59a-109">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="be59a-110">からに格納するトークンの要求された最大数 `rGenericParams` 。</span><span class="sxs-lookup"><span data-stu-id="be59a-110">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="be59a-111">入出力に格納された、返されたトークンの数 `rGenericParams` 。</span><span class="sxs-lookup"><span data-stu-id="be59a-111">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be59a-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="be59a-112">Return Value</span></span>  
  
|<span data-ttu-id="be59a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be59a-113">HRESULT</span></span>|<span data-ttu-id="be59a-114">説明</span><span class="sxs-lookup"><span data-stu-id="be59a-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="be59a-115">`EnumGenericParams` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="be59a-115">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="be59a-116">`phEnum` にメンバー要素がありません。</span><span class="sxs-lookup"><span data-stu-id="be59a-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="be59a-117">この場合、 `pcGenericParams` は 0 (ゼロ) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="be59a-117">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be59a-118">要件</span><span class="sxs-lookup"><span data-stu-id="be59a-118">Requirements</span></span>  

 <span data-ttu-id="be59a-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be59a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be59a-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="be59a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be59a-121">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="be59a-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be59a-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be59a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be59a-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="be59a-123">See also</span></span>

- [<span data-ttu-id="be59a-124">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be59a-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="be59a-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be59a-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
