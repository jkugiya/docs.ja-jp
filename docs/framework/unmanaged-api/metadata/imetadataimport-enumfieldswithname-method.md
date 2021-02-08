---
description: '詳細については、次を参照してください: IMetaDataImport:: Enumフィールド Withname メソッド'
title: IMetaDataImport::EnumFieldsWithName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: 88096b2b12a9571eb05d4550e6e26a348e28cfd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799370"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="248e6-103">IMetaDataImport::EnumFieldsWithName メソッド</span><span class="sxs-lookup"><span data-stu-id="248e6-103">IMetaDataImport::EnumFieldsWithName Method</span></span>

<span data-ttu-id="248e6-104">指定した名前を持つ指定した型の FieldDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="248e6-104">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="248e6-105">構文</span><span class="sxs-lookup"><span data-stu-id="248e6-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="248e6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="248e6-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="248e6-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="248e6-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="248e6-108">からフィールドを列挙する型のトークン。</span><span class="sxs-lookup"><span data-stu-id="248e6-108">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="248e6-109">から列挙型のスコープを制限するフィールド名。</span><span class="sxs-lookup"><span data-stu-id="248e6-109">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="248e6-110">入出力FieldDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="248e6-110">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="248e6-111">[in] `rFields` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="248e6-111">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="248e6-112">入出力で返された FieldDef トークンの実際の数 `rFields` 。</span><span class="sxs-lookup"><span data-stu-id="248e6-112">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="248e6-113">解説</span><span class="sxs-lookup"><span data-stu-id="248e6-113">Remarks</span></span>  

 <span data-ttu-id="248e6-114">[IMetaDataImport:: EnumFields](imetadataimport-enumfields-method.md)とは異なり、は `EnumFieldsWithName` 指定された名前のないすべてのフィールドトークンを破棄します。</span><span class="sxs-lookup"><span data-stu-id="248e6-114">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="248e6-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="248e6-115">Return Value</span></span>  
  
|<span data-ttu-id="248e6-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="248e6-116">HRESULT</span></span>|<span data-ttu-id="248e6-117">説明</span><span class="sxs-lookup"><span data-stu-id="248e6-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="248e6-118">`EnumFieldsWithName` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="248e6-118">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="248e6-119">列挙するフィールドがありません。</span><span class="sxs-lookup"><span data-stu-id="248e6-119">There are no fields to enumerate.</span></span> <span data-ttu-id="248e6-120">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="248e6-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="248e6-121">要件</span><span class="sxs-lookup"><span data-stu-id="248e6-121">Requirements</span></span>  

 <span data-ttu-id="248e6-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="248e6-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="248e6-123">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="248e6-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="248e6-124">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="248e6-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="248e6-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="248e6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248e6-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="248e6-126">See also</span></span>

- [<span data-ttu-id="248e6-127">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="248e6-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="248e6-128">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="248e6-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
