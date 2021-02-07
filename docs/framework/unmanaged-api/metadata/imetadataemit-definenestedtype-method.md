---
description: '詳細について: IMetaDataEmit::D efineNestedType メソッド'
title: IMetaDataEmit::DefineNestedType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 1b0c5c8d1bffa425b2019a4434042c84a0069907
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753381"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="93d55-103">IMetaDataEmit::DefineNestedType メソッド</span><span class="sxs-lookup"><span data-stu-id="93d55-103">IMetaDataEmit::DefineNestedType Method</span></span>

<span data-ttu-id="93d55-104">型定義のメタデータシグネチャを作成し、 `mdTypeDef` その型のトークンを返します。また、定義された型がパラメーターによって参照される型のメンバーであることを指定し `tdEncloser` ます。</span><span class="sxs-lookup"><span data-stu-id="93d55-104">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93d55-105">構文</span><span class="sxs-lookup"><span data-stu-id="93d55-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93d55-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="93d55-106">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="93d55-107">からUnicode での型の名前。</span><span class="sxs-lookup"><span data-stu-id="93d55-107">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="93d55-108">[入力] `TypeDef` アトリビュート.</span><span class="sxs-lookup"><span data-stu-id="93d55-108">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="93d55-109">これは、値のビットマスクです `CorTypeAttr` 。</span><span class="sxs-lookup"><span data-stu-id="93d55-109">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="93d55-110">から基本クラスのトークン。</span><span class="sxs-lookup"><span data-stu-id="93d55-110">[in] The token of the base class.</span></span> <span data-ttu-id="93d55-111">これは、 `mdTypeDef` またはトークンのいずれか `mdTypeRef` です。</span><span class="sxs-lookup"><span data-stu-id="93d55-111">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="93d55-112">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="93d55-112">`rtkImplements`[]</span></span>  
 <span data-ttu-id="93d55-113">からこのクラスまたはインターフェイスが実装するインターフェイスを指定するトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="93d55-113">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="93d55-114">から外側の型のトークン。</span><span class="sxs-lookup"><span data-stu-id="93d55-114">[in] The token of the enclosing type.</span></span> <span data-ttu-id="93d55-115">配列の最後の要素は、である必要があり `mdTokenNil` ます。</span><span class="sxs-lookup"><span data-stu-id="93d55-115">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="93d55-116">入出力 `mdTypeDef` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="93d55-116">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93d55-117">要件</span><span class="sxs-lookup"><span data-stu-id="93d55-117">Requirements</span></span>  

 <span data-ttu-id="93d55-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93d55-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93d55-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="93d55-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93d55-120">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="93d55-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93d55-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93d55-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93d55-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="93d55-122">See also</span></span>

- [<span data-ttu-id="93d55-123">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93d55-123">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="93d55-124">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93d55-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
