---
description: '詳細について: IMetaDataEmit:: SetFieldProps メソッド'
title: IMetaDataEmit::SetFieldProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: ee9964077e556a1d0666a836ca0c3bab92540252
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658010"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="1d526-103">IMetaDataEmit::SetFieldProps メソッド</span><span class="sxs-lookup"><span data-stu-id="1d526-103">IMetaDataEmit::SetFieldProps Method</span></span>

<span data-ttu-id="1d526-104">指定したフィールドトークンによって参照されるフィールドの既定値を設定または更新します。</span><span class="sxs-lookup"><span data-stu-id="1d526-104">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d526-105">構文</span><span class="sxs-lookup"><span data-stu-id="1d526-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d526-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1d526-106">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="1d526-107">からターゲットフィールドのトークン。</span><span class="sxs-lookup"><span data-stu-id="1d526-107">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="1d526-108">からフィールド属性。</span><span class="sxs-lookup"><span data-stu-id="1d526-108">[in] Field attributes.</span></span> <span data-ttu-id="1d526-109">これは、値のビットマスクです `CorFieldAttr` 。</span><span class="sxs-lookup"><span data-stu-id="1d526-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="1d526-110">から`ELEMENT_TYPE_` *\** 定数値の。</span><span class="sxs-lookup"><span data-stu-id="1d526-110">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="1d526-111">これは `CorElementType` 値です。</span><span class="sxs-lookup"><span data-stu-id="1d526-111">This is a `CorElementType` value.</span></span> <span data-ttu-id="1d526-112">定数が定義されていない場合は、この値をに設定 `ELEMENT_TYPE_END` します。</span><span class="sxs-lookup"><span data-stu-id="1d526-112">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="1d526-113">からフィールドの定数値。</span><span class="sxs-lookup"><span data-stu-id="1d526-113">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="1d526-114">からのサイズ (Unicode 文字) `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="1d526-114">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d526-115">要件</span><span class="sxs-lookup"><span data-stu-id="1d526-115">Requirements</span></span>  

 <span data-ttu-id="1d526-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d526-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d526-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1d526-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d526-118">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d526-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d526-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d526-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d526-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d526-120">See also</span></span>

- [<span data-ttu-id="1d526-121">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d526-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1d526-122">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d526-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
