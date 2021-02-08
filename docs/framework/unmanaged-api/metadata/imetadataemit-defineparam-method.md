---
description: '詳細について: IMetaDataEmit::D efineParam メソッド'
title: IMetaDataEmit::DefineParam メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 300de3183b329773a8e6813d6b92c6d049d63195
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784094"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="ba8fc-103">IMetaDataEmit::DefineParam メソッド</span><span class="sxs-lookup"><span data-stu-id="ba8fc-103">IMetaDataEmit::DefineParam Method</span></span>

<span data-ttu-id="ba8fc-104">指定したトークンによって参照されるメソッドに対して、指定したシグネチャを持つパラメーター定義を作成し、そのパラメーター定義のトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-104">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba8fc-105">構文</span><span class="sxs-lookup"><span data-stu-id="ba8fc-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba8fc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ba8fc-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="ba8fc-107">からパラメーターが定義されているメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-107">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="ba8fc-108">からパラメーターのシーケンス番号。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-108">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="ba8fc-109">からUnicode でのパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-109">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="ba8fc-110">からパラメーターのフラグ。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-110">[in] Flags for the parameter.</span></span> <span data-ttu-id="ba8fc-111">これは、値のビットマスクです `CorParamAttr` 。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-111">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="ba8fc-112">[入力] `ELEMENT_TYPE_` *\** 定数値の。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-112">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ba8fc-113">からパラメーターの定数値。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-113">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="ba8fc-114">からのサイズ (Unicode 文字) `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-114">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="ba8fc-115">入出力 `mdParamDef` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-115">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba8fc-116">解説</span><span class="sxs-lookup"><span data-stu-id="ba8fc-116">Remarks</span></span>  

 <span data-ttu-id="ba8fc-117">パラメーターの場合、のシーケンス値は `ulParamSeq` 1 から始まります。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-117">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="ba8fc-118">戻り値のシーケンス番号は0です。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-118">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba8fc-119">要件</span><span class="sxs-lookup"><span data-stu-id="ba8fc-119">Requirements</span></span>  

 <span data-ttu-id="ba8fc-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba8fc-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="ba8fc-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba8fc-122">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="ba8fc-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba8fc-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba8fc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba8fc-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba8fc-124">See also</span></span>

- [<span data-ttu-id="ba8fc-125">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ba8fc-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ba8fc-126">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ba8fc-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
