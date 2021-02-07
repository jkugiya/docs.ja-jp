---
description: '詳細について: IMetaDataEmit:: GetTokenFromTypeSpec メソッド'
title: IMetaDataEmit::GetTokenFromTypeSpec メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 09f7133af9b9d912b03cdc1c93744ee260c69169
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728237"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="1679d-103">IMetaDataEmit::GetTokenFromTypeSpec メソッド</span><span class="sxs-lookup"><span data-stu-id="1679d-103">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>

<span data-ttu-id="1679d-104">指定したメタデータシグネチャを持つ型のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="1679d-104">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1679d-105">構文</span><span class="sxs-lookup"><span data-stu-id="1679d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1679d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1679d-106">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="1679d-107">から定義されている署名。</span><span class="sxs-lookup"><span data-stu-id="1679d-107">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="1679d-108">からのバイト数 `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="1679d-108">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="1679d-109">入出力 `mdTypeSpec` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="1679d-109">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1679d-110">要件</span><span class="sxs-lookup"><span data-stu-id="1679d-110">Requirements</span></span>  

 <span data-ttu-id="1679d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1679d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1679d-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1679d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1679d-113">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="1679d-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1679d-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1679d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1679d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1679d-115">See also</span></span>

- [<span data-ttu-id="1679d-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1679d-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1679d-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1679d-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
