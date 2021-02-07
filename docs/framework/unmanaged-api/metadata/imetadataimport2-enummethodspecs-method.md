---
description: '詳細情報: IMetaDataImport2:: EnumMethodSpecs メソッド'
title: IMetaDataImport2::EnumMethodSpecs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 19fff1d78599d968bb1fd0ab27b0f71e41fae20b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677523"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="d7043-103">IMetaDataImport2::EnumMethodSpecs メソッド</span><span class="sxs-lookup"><span data-stu-id="d7043-103">IMetaDataImport2::EnumMethodSpecs Method</span></span>

<span data-ttu-id="d7043-104">指定した MethodDef または MemberRef トークンに関連付けられている MethodSpec トークンの配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d7043-104">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7043-105">構文</span><span class="sxs-lookup"><span data-stu-id="d7043-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d7043-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d7043-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="d7043-107">[入力、出力]の列挙子へのポインター `rMethodSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="d7043-107">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="d7043-108">からMethodSpec トークンを列挙するメソッドを表す MemberRef または MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="d7043-108">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="d7043-109">の値 `tk` が 0 (ゼロ) の場合、スコープ内のすべての MethodSpec トークンが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="d7043-109">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="d7043-110">入出力列挙する MethodSpec トークンの配列。</span><span class="sxs-lookup"><span data-stu-id="d7043-110">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d7043-111">からに格納するトークンの要求された最大数 `rMethodSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="d7043-111">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="d7043-112">入出力に格納された、返されたトークンの数 `rMethodSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="d7043-112">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7043-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="d7043-113">Return Value</span></span>  
  
|<span data-ttu-id="d7043-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7043-114">HRESULT</span></span>|<span data-ttu-id="d7043-115">説明</span><span class="sxs-lookup"><span data-stu-id="d7043-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d7043-116">`EnumMethodSpecs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d7043-116">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d7043-117">`phEnum` にメンバー要素がありません。</span><span class="sxs-lookup"><span data-stu-id="d7043-117">`phEnum` has no member elements.</span></span> <span data-ttu-id="d7043-118">この場合、 `pcMethodSpecs` は 0 (ゼロ) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d7043-118">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7043-119">要件</span><span class="sxs-lookup"><span data-stu-id="d7043-119">Requirements</span></span>  

 <span data-ttu-id="d7043-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7043-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7043-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="d7043-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d7043-122">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="d7043-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d7043-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7043-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7043-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7043-124">See also</span></span>

- [<span data-ttu-id="d7043-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7043-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="d7043-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7043-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
