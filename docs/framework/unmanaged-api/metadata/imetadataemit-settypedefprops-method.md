---
description: '詳細について: IMetaDataEmit:: SetTypeDefProps メソッド'
title: IMetaDataEmit::SetTypeDefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: 1160d20e7ceb422390f8cd725a75fdb4f42318e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706501"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="03b70-103">IMetaDataEmit::SetTypeDefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="03b70-103">IMetaDataEmit::SetTypeDefProps Method</span></span>

<span data-ttu-id="03b70-104">[IMetaDataEmit::D efineTypeDef](imetadataemit-definetypedef-method.md)の前の呼び出しで定義された型の機能を設定します。</span><span class="sxs-lookup"><span data-stu-id="03b70-104">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03b70-105">構文</span><span class="sxs-lookup"><span data-stu-id="03b70-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03b70-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03b70-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="03b70-107">から `mdTypeDef` [IMetaDataEmit::D efineTypeDef](imetadataemit-definetypedef-method.md)の元の呼び出しから取得されたトークン。</span><span class="sxs-lookup"><span data-stu-id="03b70-107">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="03b70-108">[入力] `TypeDef` アトリビュート.</span><span class="sxs-lookup"><span data-stu-id="03b70-108">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="03b70-109">これは、値のビットマスクです `CorTypeAttr` 。</span><span class="sxs-lookup"><span data-stu-id="03b70-109">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="03b70-110">から `mdToken` 基本クラスの。</span><span class="sxs-lookup"><span data-stu-id="03b70-110">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="03b70-111">[IMetaDataEmit::D efineImportType](imetadataemit-defineimporttype-method.md)、またはの以前の呼び出しから取得さ `null` れます。</span><span class="sxs-lookup"><span data-stu-id="03b70-111">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="03b70-112">からこの型が実装するインターフェイスのトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="03b70-112">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="03b70-113">これらの `mdTypeRef` トークンは、 [IMetaDataEmit::D efineImportType](imetadataemit-defineimporttype-method.md)を使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="03b70-113">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="03b70-114">配列の最後の要素は、である必要があり `mdTokenNil` ます。</span><span class="sxs-lookup"><span data-stu-id="03b70-114">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03b70-115">要件</span><span class="sxs-lookup"><span data-stu-id="03b70-115">Requirements</span></span>  

 <span data-ttu-id="03b70-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03b70-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03b70-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="03b70-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03b70-118">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="03b70-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03b70-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03b70-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b70-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="03b70-120">See also</span></span>

- [<span data-ttu-id="03b70-121">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03b70-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="03b70-122">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03b70-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
