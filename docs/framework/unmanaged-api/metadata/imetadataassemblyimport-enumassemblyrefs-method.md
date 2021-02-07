---
description: '詳細について: IMetaDataAssemblyImport:: EnumAssemblyRefs メソッド'
title: IMetaDataAssemblyImport::EnumAssemblyRefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: fc1d74d79edc21c6d3d13c80510440333d083801
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671062"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="748d6-103">IMetaDataAssemblyImport::EnumAssemblyRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="748d6-103">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>

<span data-ttu-id="748d6-104">`mdAssemblyRef`アセンブリマニフェストで定義されているインスタンスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="748d6-104">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="748d6-105">構文</span><span class="sxs-lookup"><span data-stu-id="748d6-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="748d6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="748d6-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="748d6-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="748d6-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="748d6-108">メソッドを初めて呼び出すときは、null 値を指定する必要があり `EnumAssemblyRefs` ます。</span><span class="sxs-lookup"><span data-stu-id="748d6-108">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="748d6-109">入出力 `mdAssemblyRef` メタデータトークンの列挙体。</span><span class="sxs-lookup"><span data-stu-id="748d6-109">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="748d6-110">から配列に格納できるトークンの最大数 `rAssemblyRefs` 。</span><span class="sxs-lookup"><span data-stu-id="748d6-110">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="748d6-111">入出力実際に配置されたトークンの数 `rAssemblyRefs` 。</span><span class="sxs-lookup"><span data-stu-id="748d6-111">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="748d6-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="748d6-112">Return Value</span></span>  
  
|<span data-ttu-id="748d6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="748d6-113">HRESULT</span></span>|<span data-ttu-id="748d6-114">説明</span><span class="sxs-lookup"><span data-stu-id="748d6-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="748d6-115">`EnumAssemblyRefs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="748d6-115">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="748d6-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="748d6-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="748d6-117">この場合、 `pcTokens` は0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="748d6-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="748d6-118">要件</span><span class="sxs-lookup"><span data-stu-id="748d6-118">Requirements</span></span>  

 <span data-ttu-id="748d6-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="748d6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="748d6-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="748d6-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="748d6-121">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="748d6-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="748d6-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="748d6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="748d6-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="748d6-123">See also</span></span>

- [<span data-ttu-id="748d6-124">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="748d6-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
