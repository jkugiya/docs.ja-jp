---
description: '詳細情報: IMetaDataAssemblyImport:: EnumManifestResources メソッド'
title: IMetaDataAssemblyImport::EnumManifestResources メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: ff819ebb575626af6049558656637e7fabcbc322
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677980"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="4408f-103">IMetaDataAssemblyImport::EnumManifestResources メソッド</span><span class="sxs-lookup"><span data-stu-id="4408f-103">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>

<span data-ttu-id="4408f-104">現在のアセンブリマニフェストで参照されているリソースの列挙子へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4408f-104">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4408f-105">構文</span><span class="sxs-lookup"><span data-stu-id="4408f-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="4408f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4408f-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="4408f-107">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4408f-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4408f-108">メソッドを初めて呼び出すときは、null 値を指定する必要があり `EnumManifestResources` ます。</span><span class="sxs-lookup"><span data-stu-id="4408f-108">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="4408f-109">入出力メタデータトークンを格納するために使用される配列 `mdManifestResource` 。</span><span class="sxs-lookup"><span data-stu-id="4408f-109">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4408f-110">から `mdManifestResource` に格納できるトークンの最大数 `rManifestResources` 。</span><span class="sxs-lookup"><span data-stu-id="4408f-110">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4408f-111">入出力 `mdManifestResource` 実際に配置されたトークンの数 `rManifestResources` 。</span><span class="sxs-lookup"><span data-stu-id="4408f-111">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4408f-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="4408f-112">Return Value</span></span>  
  
|<span data-ttu-id="4408f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4408f-113">HRESULT</span></span>|<span data-ttu-id="4408f-114">説明</span><span class="sxs-lookup"><span data-stu-id="4408f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4408f-115">`EnumManifestResources` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="4408f-115">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4408f-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="4408f-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="4408f-117">この場合、 `pcTokens` は0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4408f-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4408f-118">要件</span><span class="sxs-lookup"><span data-stu-id="4408f-118">Requirements</span></span>  

 <span data-ttu-id="4408f-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4408f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4408f-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4408f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4408f-121">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="4408f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4408f-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4408f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4408f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="4408f-123">See also</span></span>

- [<span data-ttu-id="4408f-124">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4408f-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
