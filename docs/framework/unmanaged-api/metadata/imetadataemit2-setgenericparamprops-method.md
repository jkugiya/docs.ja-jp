---
description: '詳細について: IMetaDataEmit2:: SetGenericParamProps メソッド'
title: IMetaDataEmit2::SetGenericParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: 9c6946bbd301450203bc6fb2b1202352119dc792
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771653"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="e07a2-103">IMetaDataEmit2::SetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="e07a2-103">IMetaDataEmit2::SetGenericParamProps Method</span></span>

<span data-ttu-id="e07a2-104">指定したトークンによって参照されるジェネリックパラメーター定義のプロパティ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="e07a2-104">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07a2-105">構文</span><span class="sxs-lookup"><span data-stu-id="e07a2-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e07a2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e07a2-106">Parameters</span></span>  

 `gp`  
 <span data-ttu-id="e07a2-107">から値を設定するジェネリックパラメーター定義のトークン。</span><span class="sxs-lookup"><span data-stu-id="e07a2-107">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e07a2-108">からジェネリックパラメーターの型を記述する [Corgenericparamattr](corgenericparamattr-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="e07a2-108">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="e07a2-109">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="e07a2-109">[in] Optional.</span></span> <span data-ttu-id="e07a2-110">値を設定するパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="e07a2-110">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="e07a2-111">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="e07a2-111">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="e07a2-112">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="e07a2-112">[in] Optional.</span></span> <span data-ttu-id="e07a2-113">型制約の0から終わる配列。</span><span class="sxs-lookup"><span data-stu-id="e07a2-113">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="e07a2-114">配列メンバーは `mdTypeDef` 、、 `mdTypeRef` 、またはメタデータトークンである必要があり `mdTypeSpec` ます。</span><span class="sxs-lookup"><span data-stu-id="e07a2-114">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07a2-115">要件</span><span class="sxs-lookup"><span data-stu-id="e07a2-115">Requirements</span></span>  

 <span data-ttu-id="e07a2-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e07a2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e07a2-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e07a2-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e07a2-118">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e07a2-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e07a2-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e07a2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07a2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e07a2-120">See also</span></span>

- [<span data-ttu-id="e07a2-121">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e07a2-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="e07a2-122">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e07a2-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
