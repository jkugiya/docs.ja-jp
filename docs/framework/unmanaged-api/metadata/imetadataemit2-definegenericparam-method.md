---
description: '詳細について: IMetaDataEmit2::D efineGenericParam メソッド'
title: IMetaDataEmit2::DefineGenericParam メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 813661adca162f47a864b19c9754b49072bb4c7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745778"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="604ff-103">IMetaDataEmit2::DefineGenericParam メソッド</span><span class="sxs-lookup"><span data-stu-id="604ff-103">IMetaDataEmit2::DefineGenericParam Method</span></span>

<span data-ttu-id="604ff-104">ジェネリック型パラメーターの定義を作成し、そのジェネリック型パラメーターへのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="604ff-104">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="604ff-105">構文</span><span class="sxs-lookup"><span data-stu-id="604ff-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="604ff-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="604ff-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="604ff-107">から `mdTypeDef` `mdMethodDef` ジェネリックパラメーターを定義するメソッドまたはコンストラクターを表すまたはトークン。</span><span class="sxs-lookup"><span data-stu-id="604ff-107">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="604ff-108">からジェネリックパラメーターのインデックス。</span><span class="sxs-lookup"><span data-stu-id="604ff-108">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="604ff-109">からジェネリックパラメーターの型を記述する [Corgenericparamattr](corgenericparamattr-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="604ff-109">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="604ff-110">からパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="604ff-110">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="604ff-111">からこのパラメーターは、将来の拡張のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="604ff-111">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="604ff-112">から型制約の0から終わる配列。</span><span class="sxs-lookup"><span data-stu-id="604ff-112">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="604ff-113">配列メンバーは `mdTypeDef` 、、 `mdTypeRef` 、またはメタデータトークンである必要があり `mdTypeSpec` ます。</span><span class="sxs-lookup"><span data-stu-id="604ff-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="604ff-114">入出力ジェネリックパラメーターを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="604ff-114">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="604ff-115">要件</span><span class="sxs-lookup"><span data-stu-id="604ff-115">Requirements</span></span>  

 <span data-ttu-id="604ff-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="604ff-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="604ff-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="604ff-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="604ff-118">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="604ff-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="604ff-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="604ff-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604ff-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="604ff-120">See also</span></span>

- [<span data-ttu-id="604ff-121">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="604ff-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="604ff-122">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="604ff-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
