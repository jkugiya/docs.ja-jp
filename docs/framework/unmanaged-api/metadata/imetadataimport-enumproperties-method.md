---
description: '詳細情報: IMetaDataImport:: EnumProperties メソッド'
title: IMetaDataImport::EnumProperties メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
ms.openlocfilehash: 7503dd14668e8ea4ccf8939e67b91a41db187105
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799357"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="8730d-103">IMetaDataImport::EnumProperties メソッド</span><span class="sxs-lookup"><span data-stu-id="8730d-103">IMetaDataImport::EnumProperties Method</span></span>

<span data-ttu-id="8730d-104">指定した TypeDef トークンによって参照される型のプロパティを表す PropertyDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="8730d-104">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8730d-105">構文</span><span class="sxs-lookup"><span data-stu-id="8730d-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8730d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8730d-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="8730d-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8730d-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8730d-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8730d-108">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="8730d-109">から列挙するプロパティを持つ型を表す TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="8730d-109">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="8730d-110">入出力PropertyDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="8730d-110">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8730d-111">[in] `rProperties` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="8730d-111">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="8730d-112">入出力で返された PropertyDef トークンの数 `rProperties` 。</span><span class="sxs-lookup"><span data-stu-id="8730d-112">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8730d-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="8730d-113">Return Value</span></span>  
  
|<span data-ttu-id="8730d-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8730d-114">HRESULT</span></span>|<span data-ttu-id="8730d-115">説明</span><span class="sxs-lookup"><span data-stu-id="8730d-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8730d-116">`EnumProperties` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="8730d-116">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8730d-117">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="8730d-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="8730d-118">この場合、 `pcProperties` は0になります。</span><span class="sxs-lookup"><span data-stu-id="8730d-118">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8730d-119">要件</span><span class="sxs-lookup"><span data-stu-id="8730d-119">Requirements</span></span>  

 <span data-ttu-id="8730d-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8730d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8730d-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8730d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8730d-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8730d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8730d-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8730d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8730d-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="8730d-124">See also</span></span>

- [<span data-ttu-id="8730d-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8730d-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8730d-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8730d-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
