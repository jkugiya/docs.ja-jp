---
description: '詳細について: IMetaDataImport:: EnumTypeRefs メソッド'
title: IMetaDataImport::EnumTypeRefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: 1155357e82c08660a852225f0b1a54629cbee0ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670620"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="9b3bd-103">IMetaDataImport::EnumTypeRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="9b3bd-103">IMetaDataImport::EnumTypeRefs Method</span></span>

<span data-ttu-id="9b3bd-104">現在のメタデータ スコープに定義されている TypeRef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-104">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b3bd-105">構文</span><span class="sxs-lookup"><span data-stu-id="9b3bd-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b3bd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b3bd-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="9b3bd-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="9b3bd-108">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-108">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="9b3bd-109">入出力TypeRef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-109">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9b3bd-110">[in] `rTypeRefs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-110">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="9b3bd-111">入出力で返された TypeRef トークンの数へのポインター `rTypeRefs` 。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-111">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b3bd-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="9b3bd-112">Return Value</span></span>  
  
|<span data-ttu-id="9b3bd-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b3bd-113">HRESULT</span></span>|<span data-ttu-id="9b3bd-114">説明</span><span class="sxs-lookup"><span data-stu-id="9b3bd-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9b3bd-115">`EnumTypeRefs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-115">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9b3bd-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="9b3bd-117">この場合、 `pcTypeRefs` は0になります。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-117">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b3bd-118">解説</span><span class="sxs-lookup"><span data-stu-id="9b3bd-118">Remarks</span></span>  

 <span data-ttu-id="9b3bd-119">TypeRef トークンは、型への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-119">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b3bd-120">要件</span><span class="sxs-lookup"><span data-stu-id="9b3bd-120">Requirements</span></span>  

 <span data-ttu-id="9b3bd-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b3bd-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b3bd-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9b3bd-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b3bd-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9b3bd-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b3bd-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b3bd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3bd-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b3bd-125">See also</span></span>

- [<span data-ttu-id="9b3bd-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b3bd-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9b3bd-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b3bd-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
