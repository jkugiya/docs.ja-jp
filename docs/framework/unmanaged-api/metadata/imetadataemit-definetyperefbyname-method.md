---
description: '詳細について: IMetaDataEmit::D efineTypeRefByName メソッド'
title: IMetaDataEmit::DefineTypeRefByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: 836516e06105bb8ebc7c9bacf7b7d3837bf89eec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784016"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="aaaf3-103">IMetaDataEmit::DefineTypeRefByName メソッド</span><span class="sxs-lookup"><span data-stu-id="aaaf3-103">IMetaDataEmit::DefineTypeRefByName Method</span></span>

<span data-ttu-id="aaaf3-104">現在のスコープ外にある、指定されたスコープで定義されている型のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-104">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaaf3-105">構文</span><span class="sxs-lookup"><span data-stu-id="aaaf3-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaaf3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aaaf3-106">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="aaaf3-107">から解決スコープを指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-107">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="aaaf3-108">有効なトークンの種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-108">The following token types are valid:</span></span>  
  
- <span data-ttu-id="aaaf3-109">`mdModuleRef`型が、呼び出し元が定義されている同じアセンブリ内で定義されている場合は。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-109">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="aaaf3-110">`mdAssemblyRef`型が、呼び出し元が定義されているアセンブリ以外のアセンブリで定義されている場合は。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-110">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="aaaf3-111">`mdTypeRef`型が入れ子にされた型の場合は。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-111">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="aaaf3-112">`mdModule`型が、呼び出し元が定義されている同じモジュールで定義されている場合は。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-112">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="aaaf3-113">型がグローバルに定義されている場合は Null。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-113">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="aaaf3-114">からUnicode での対象の型の名前。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-114">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="aaaf3-115">入出力 `mdTypeRef` 型に割り当てられているトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-115">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaaf3-116">要件</span><span class="sxs-lookup"><span data-stu-id="aaaf3-116">Requirements</span></span>  

 <span data-ttu-id="aaaf3-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaaf3-118">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="aaaf3-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aaaf3-119">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="aaaf3-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aaaf3-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaaf3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaaf3-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="aaaf3-121">See also</span></span>

- [<span data-ttu-id="aaaf3-122">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aaaf3-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="aaaf3-123">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aaaf3-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
