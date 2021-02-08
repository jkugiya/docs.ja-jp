---
description: '詳細について: IMetaDataEmit:: SetParamProps メソッド'
title: IMetaDataEmit::SetParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 35e839b05b3671c6c09f315ac636971c386e766e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772024"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="7d012-103">IMetaDataEmit::SetParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="7d012-103">IMetaDataEmit::SetParamProps Method</span></span>

<span data-ttu-id="7d012-104">[IMetaDataEmit::D efineParam](imetadataemit-defineparam-method.md)の前の呼び出しで定義されたメソッドパラメーターの機能を設定または変更します。</span><span class="sxs-lookup"><span data-stu-id="7d012-104">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d012-105">構文</span><span class="sxs-lookup"><span data-stu-id="7d012-105">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d012-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d012-106">Parameters</span></span>  

 `pd`  
 <span data-ttu-id="7d012-107">から対象のパラメーターのトークン。</span><span class="sxs-lookup"><span data-stu-id="7d012-107">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="7d012-108">からUnicode でのパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="7d012-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="7d012-109">からパラメーターのフラグ。</span><span class="sxs-lookup"><span data-stu-id="7d012-109">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="7d012-110">から定数値の ELEMENT_TYPE_ \*。</span><span class="sxs-lookup"><span data-stu-id="7d012-110">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="7d012-111">からパラメーターの定数値。</span><span class="sxs-lookup"><span data-stu-id="7d012-111">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="7d012-112">からの (Unicode) 文字のサイズ `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="7d012-112">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d012-113">要件</span><span class="sxs-lookup"><span data-stu-id="7d012-113">Requirements</span></span>  

 <span data-ttu-id="7d012-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d012-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d012-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="7d012-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d012-116">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="7d012-116">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d012-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d012-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d012-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d012-118">See also</span></span>

- [<span data-ttu-id="7d012-119">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d012-119">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7d012-120">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d012-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
