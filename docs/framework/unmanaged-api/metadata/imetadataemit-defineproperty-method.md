---
description: '詳細について: IMetaDataEmit::D efineProperty メソッド'
title: IMetaDataEmit::DefineProperty メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: c0c0b6009f8674a5edebf1c982e277f4ca5b185b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784032"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="ee946-103">IMetaDataEmit::DefineProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="ee946-103">IMetaDataEmit::DefineProperty Method</span></span>

<span data-ttu-id="ee946-104">指定したアクセサーとメソッドアクセサーを使用して、指定した型のプロパティ定義を作成 `get` `set` し、そのプロパティ定義へのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="ee946-104">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee946-105">構文</span><span class="sxs-lookup"><span data-stu-id="ee946-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee946-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ee946-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="ee946-107">からプロパティが定義されているクラスまたはインターフェイスのトークン。</span><span class="sxs-lookup"><span data-stu-id="ee946-107">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="ee946-108">からプロパティの名前。</span><span class="sxs-lookup"><span data-stu-id="ee946-108">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="ee946-109">からプロパティフラグ。</span><span class="sxs-lookup"><span data-stu-id="ee946-109">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="ee946-110">からプロパティシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="ee946-110">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="ee946-111">からのバイト数 `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="ee946-111">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="ee946-112">からプロパティの既定値の型。</span><span class="sxs-lookup"><span data-stu-id="ee946-112">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ee946-113">からプロパティの既定値。</span><span class="sxs-lookup"><span data-stu-id="ee946-113">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="ee946-114">から内の (Unicode) 文字の数 `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="ee946-114">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="ee946-115">からプロパティ値を設定するメソッド。</span><span class="sxs-lookup"><span data-stu-id="ee946-115">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="ee946-116">からプロパティ値を取得するメソッド。</span><span class="sxs-lookup"><span data-stu-id="ee946-116">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="ee946-117">からプロパティに関連付けられている他のメソッドの配列。</span><span class="sxs-lookup"><span data-stu-id="ee946-117">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="ee946-118">を使用して配列を終了 `mdTokenNil` します。</span><span class="sxs-lookup"><span data-stu-id="ee946-118">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="ee946-119">入出力 `mdProperty` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="ee946-119">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee946-120">要件</span><span class="sxs-lookup"><span data-stu-id="ee946-120">Requirements</span></span>  

 <span data-ttu-id="ee946-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee946-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee946-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="ee946-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee946-123">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee946-123">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee946-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee946-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee946-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee946-125">See also</span></span>

- [<span data-ttu-id="ee946-126">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee946-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ee946-127">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee946-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
