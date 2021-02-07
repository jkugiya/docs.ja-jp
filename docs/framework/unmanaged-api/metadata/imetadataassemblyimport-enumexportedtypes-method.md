---
description: '詳細について: IMetaDataAssemblyImport:: EnumExportedTypes メソッド'
title: IMetaDataAssemblyImport::EnumExportedTypes メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: ecddcbd87586f5f61c57f8c04ea3bd68dc652839
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678030"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="5fee4-103">IMetaDataAssemblyImport::EnumExportedTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="5fee4-103">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>

<span data-ttu-id="5fee4-104">現在のメタデータスコープ内のアセンブリマニフェストで参照される、エクスポートされた型を列挙します。</span><span class="sxs-lookup"><span data-stu-id="5fee4-104">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fee4-105">構文</span><span class="sxs-lookup"><span data-stu-id="5fee4-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fee4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5fee4-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="5fee4-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5fee4-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5fee4-108">メソッドを初めて呼び出すときは、null 値を指定する必要があり `EnumExportedTypes` ます。</span><span class="sxs-lookup"><span data-stu-id="5fee4-108">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="5fee4-109">入出力 `mdExportedType` メタデータトークンの列挙体。</span><span class="sxs-lookup"><span data-stu-id="5fee4-109">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5fee4-110">から `mdExportedType` 配列に格納できるトークンの最大数 `rExportedTypes` 。</span><span class="sxs-lookup"><span data-stu-id="5fee4-110">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5fee4-111">入出力 `mdExportedType` 実際に配置されたトークンの数 `rExportedTypes` 。</span><span class="sxs-lookup"><span data-stu-id="5fee4-111">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fee4-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="5fee4-112">Return Value</span></span>  
  
|<span data-ttu-id="5fee4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5fee4-113">HRESULT</span></span>|<span data-ttu-id="5fee4-114">説明</span><span class="sxs-lookup"><span data-stu-id="5fee4-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5fee4-115">`EnumExportedTypes` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="5fee4-115">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5fee4-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="5fee4-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="5fee4-117">この場合、 `pcTokens` は0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5fee4-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5fee4-118">要件</span><span class="sxs-lookup"><span data-stu-id="5fee4-118">Requirements</span></span>  

 <span data-ttu-id="5fee4-119">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fee4-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fee4-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="5fee4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5fee4-121">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="5fee4-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5fee4-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fee4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fee4-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fee4-123">See also</span></span>

- [<span data-ttu-id="5fee4-124">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5fee4-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
