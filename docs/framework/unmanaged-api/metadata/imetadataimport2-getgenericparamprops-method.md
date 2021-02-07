---
description: '詳細について: IMetaDataImport2:: GetGenericParamProps メソッド'
title: IMetaDataImport2::GetGenericParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 06b522531282b4a30cdc8ebf001c16438e8612ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688729"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="120fb-103">IMetaDataImport2::GetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="120fb-103">IMetaDataImport2::GetGenericParamProps Method</span></span>

<span data-ttu-id="120fb-104">指定したトークンによって表されるジェネリックパラメーターに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="120fb-104">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="120fb-105">構文</span><span class="sxs-lookup"><span data-stu-id="120fb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="120fb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="120fb-106">Parameters</span></span>  

 `gp`  
 <span data-ttu-id="120fb-107">からメタデータを返す対象のジェネリックパラメーターを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="120fb-107">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="120fb-108">入出力 `Type` 親コンストラクターまたはメソッド内のパラメーターの序数位置。</span><span class="sxs-lookup"><span data-stu-id="120fb-108">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="120fb-109">入出力ジェネリックパラメーターのを記述する [Corgenericparamattr](corgenericparamattr-enumeration.md) 列挙体の値 `Type` 。</span><span class="sxs-lookup"><span data-stu-id="120fb-109">[out] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="120fb-110">入出力パラメーターの所有者を表す TypeDef または MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="120fb-110">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="120fb-111">入出力将来の拡張のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="120fb-111">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="120fb-112">入出力ジェネリックパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="120fb-112">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="120fb-113">からバッファーのサイズ `wzName` 。</span><span class="sxs-lookup"><span data-stu-id="120fb-113">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="120fb-114">入出力名前の返されたサイズ (ワイド文字単位)。</span><span class="sxs-lookup"><span data-stu-id="120fb-114">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="120fb-115">要件</span><span class="sxs-lookup"><span data-stu-id="120fb-115">Requirements</span></span>  

 <span data-ttu-id="120fb-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="120fb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="120fb-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="120fb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="120fb-118">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="120fb-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="120fb-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="120fb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120fb-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="120fb-120">See also</span></span>

- [<span data-ttu-id="120fb-121">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="120fb-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="120fb-122">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="120fb-122">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
