---
description: '詳細について: IMetaDataEmit:: SetCustomAttributeValue メソッド'
title: IMetaDataEmit::SetCustomAttributeValue メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
ms.openlocfilehash: 1eede765f27b371deb670242086d59b3d4320530
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706579"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="2b6bd-103">IMetaDataEmit::SetCustomAttributeValue メソッド</span><span class="sxs-lookup"><span data-stu-id="2b6bd-103">IMetaDataEmit::SetCustomAttributeValue Method</span></span>

<span data-ttu-id="2b6bd-104">[IMetaDataEmit::D efinecustomattribute](imetadataemit-definecustomattribute-method.md)の前の呼び出しで定義されたカスタム属性の値を設定または更新します。</span><span class="sxs-lookup"><span data-stu-id="2b6bd-104">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b6bd-105">構文</span><span class="sxs-lookup"><span data-stu-id="2b6bd-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b6bd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b6bd-106">Parameters</span></span>  

 `pcv`  
 <span data-ttu-id="2b6bd-107">から対象のカスタム属性のトークン。</span><span class="sxs-lookup"><span data-stu-id="2b6bd-107">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="2b6bd-108">からカスタム属性を格納している配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2b6bd-108">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="2b6bd-109">からカスタム属性のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2b6bd-109">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b6bd-110">要件</span><span class="sxs-lookup"><span data-stu-id="2b6bd-110">Requirements</span></span>  

 <span data-ttu-id="2b6bd-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b6bd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b6bd-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="2b6bd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b6bd-113">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="2b6bd-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b6bd-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b6bd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6bd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b6bd-115">See also</span></span>

- [<span data-ttu-id="2b6bd-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b6bd-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2b6bd-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b6bd-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
