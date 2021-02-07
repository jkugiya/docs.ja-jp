---
description: '詳細について: IMetaDataEmit::D efineCustomAttribute メソッド'
title: IMetaDataEmit::DefineCustomAttribute メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: 5d802f590525b8b398ac270b1b7f59d122b45b73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753485"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="86044-103">IMetaDataEmit::DefineCustomAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="86044-103">IMetaDataEmit::DefineCustomAttribute Method</span></span>

<span data-ttu-id="86044-104">指定したメタデータシグネチャを使用して、指定したオブジェクトにアタッチするカスタム属性の定義を作成し、そのカスタム属性定義へのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="86044-104">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86044-105">構文</span><span class="sxs-lookup"><span data-stu-id="86044-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86044-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="86044-106">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="86044-107">から所有者項目のトークン。</span><span class="sxs-lookup"><span data-stu-id="86044-107">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="86044-108">からカスタム属性を識別するトークン。</span><span class="sxs-lookup"><span data-stu-id="86044-108">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="86044-109">からカスタム属性へのポインター。</span><span class="sxs-lookup"><span data-stu-id="86044-109">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="86044-110">からのバイト数 `pCustomAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="86044-110">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="86044-111">入出力 `mdCustomAttribute` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="86044-111">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86044-112">要件</span><span class="sxs-lookup"><span data-stu-id="86044-112">Requirements</span></span>  

 <span data-ttu-id="86044-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86044-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86044-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="86044-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86044-115">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="86044-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86044-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86044-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86044-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="86044-117">See also</span></span>

- [<span data-ttu-id="86044-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86044-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="86044-119">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86044-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
