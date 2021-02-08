---
description: '詳細情報: IMetaDataImport:: EnumFields メソッド'
title: IMetaDataImport::EnumFields メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 5cb9b3a47dc4c51b9eba24b9519e4b97846c1a6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799383"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="faeff-103">IMetaDataImport::EnumFields メソッド</span><span class="sxs-lookup"><span data-stu-id="faeff-103">IMetaDataImport::EnumFields Method</span></span>

<span data-ttu-id="faeff-104">指定した TypeDef トークンによって参照される型の FieldDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="faeff-104">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faeff-105">構文</span><span class="sxs-lookup"><span data-stu-id="faeff-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faeff-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="faeff-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="faeff-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="faeff-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="faeff-108">からフィールドを列挙するクラスの TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="faeff-108">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="faeff-109">入出力FieldDef トークンの一覧。</span><span class="sxs-lookup"><span data-stu-id="faeff-109">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="faeff-110">[in] `rFields` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="faeff-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="faeff-111">入出力で返された FieldDef トークンの実際の数 `rFields` 。</span><span class="sxs-lookup"><span data-stu-id="faeff-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faeff-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="faeff-112">Return Value</span></span>  
  
|<span data-ttu-id="faeff-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="faeff-113">HRESULT</span></span>|<span data-ttu-id="faeff-114">説明</span><span class="sxs-lookup"><span data-stu-id="faeff-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="faeff-115">`EnumFields` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="faeff-115">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="faeff-116">列挙するフィールドがありません。</span><span class="sxs-lookup"><span data-stu-id="faeff-116">There are no fields to enumerate.</span></span> <span data-ttu-id="faeff-117">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="faeff-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="faeff-118">要件</span><span class="sxs-lookup"><span data-stu-id="faeff-118">Requirements</span></span>  

 <span data-ttu-id="faeff-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="faeff-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faeff-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="faeff-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="faeff-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="faeff-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="faeff-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faeff-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faeff-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="faeff-123">See also</span></span>

- [<span data-ttu-id="faeff-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="faeff-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="faeff-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="faeff-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
