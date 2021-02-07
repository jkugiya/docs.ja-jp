---
description: '詳細について: IMetaDataEmit::D efineField メソッド'
title: IMetaDataEmit::DefineField メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 7636b1521de721cc183305e8a0763ff0a61f331b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753446"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="5a8c5-103">IMetaDataEmit::DefineField メソッド</span><span class="sxs-lookup"><span data-stu-id="5a8c5-103">IMetaDataEmit::DefineField Method</span></span>

<span data-ttu-id="5a8c5-104">指定したメタデータシグネチャを持つフィールドの定義を作成し、そのフィールド定義へのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-104">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8c5-105">構文</span><span class="sxs-lookup"><span data-stu-id="5a8c5-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineField (
    [in]  mdTypeDef   td,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwFieldFlags,
    [in]  PCCOR_SIGNATURE pvSigBlob,
    [in]  ULONG       cbSigBlob,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue,
    [out] mdFieldDef  *pmd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a8c5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5a8c5-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="5a8c5-107">から `mdTypeDef` 外側のクラスまたはインターフェイスのトークン。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-107">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="5a8c5-108">からUnicode でのフィールド名。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-108">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="5a8c5-109">からフィールド属性。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-109">[in] The field attributes.</span></span> <span data-ttu-id="5a8c5-110">これは、値のビットマスクです `CorFieldAttr` 。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-110">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="5a8c5-111">からBLOB としてのフィールドシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-111">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="5a8c5-112">からのバイト数 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-112">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="5a8c5-113">から`ELEMENT_TYPE_` *\** 定数値の。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-113">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="5a8c5-114">これは `CorElementType` 値です。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-114">This is a `CorElementType` value.</span></span> <span data-ttu-id="5a8c5-115">フィールドの定数値を定義していない場合は、を使用し `ELEMENT_TYPE_END` ます。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-115">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="5a8c5-116">からフィールドの定数値。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-116">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="5a8c5-117">からの (Unicode) 文字のサイズ `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-117">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="5a8c5-118">入出力 `mdFieldDef` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-118">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a8c5-119">要件</span><span class="sxs-lookup"><span data-stu-id="5a8c5-119">Requirements</span></span>  

 <span data-ttu-id="5a8c5-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a8c5-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="5a8c5-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a8c5-122">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="5a8c5-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a8c5-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a8c5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8c5-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a8c5-124">See also</span></span>

- [<span data-ttu-id="5a8c5-125">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a8c5-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5a8c5-126">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a8c5-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
