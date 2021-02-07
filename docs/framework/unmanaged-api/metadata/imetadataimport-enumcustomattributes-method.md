---
description: '詳細について: IMetaDataImport:: EnumCustomAttributes メソッド'
title: IMetaDataImport::EnumCustomAttributes メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 1c55ea4b72483e5dc30425172b95be7f77e8a62a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677588"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="fbf5e-103">IMetaDataImport::EnumCustomAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="fbf5e-103">IMetaDataImport::EnumCustomAttributes Method</span></span>

<span data-ttu-id="fbf5e-104">指定した型またはメンバーに関連付けられているカスタム属性定義トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-104">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf5e-105">構文</span><span class="sxs-lookup"><span data-stu-id="fbf5e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbf5e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fbf5e-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="fbf5e-107">[入力、出力]返された列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-107">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="fbf5e-108">から列挙体のスコープのトークン、またはすべてのカスタム属性の0。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-108">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="fbf5e-109">から列挙する属性の型のコンストラクター、またはすべての型のコンストラクターのトークン `null` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-109">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="fbf5e-110">入出力カスタム属性トークンの配列。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-110">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fbf5e-111">[in] `rCustomAttributes` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-111">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="fbf5e-112">[out、省略可能]で返されるトークン値の実際の数 `rCustomAttributes` 。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-112">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbf5e-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="fbf5e-113">Return Value</span></span>  
  
|<span data-ttu-id="fbf5e-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbf5e-114">HRESULT</span></span>|<span data-ttu-id="fbf5e-115">説明</span><span class="sxs-lookup"><span data-stu-id="fbf5e-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fbf5e-116">`EnumCustomAttributes` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-116">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fbf5e-117">列挙するカスタム属性はありません。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-117">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="fbf5e-118">この場合、 `pcCustomAttributes` は0になります。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-118">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbf5e-119">要件</span><span class="sxs-lookup"><span data-stu-id="fbf5e-119">Requirements</span></span>  

 <span data-ttu-id="fbf5e-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbf5e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbf5e-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="fbf5e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fbf5e-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="fbf5e-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fbf5e-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbf5e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf5e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbf5e-124">See also</span></span>

- [<span data-ttu-id="fbf5e-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fbf5e-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="fbf5e-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fbf5e-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
