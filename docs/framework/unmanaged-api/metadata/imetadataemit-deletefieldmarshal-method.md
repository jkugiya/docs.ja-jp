---
description: '詳細について: IMetaDataEmit::D eleteFieldMarshal メソッド'
title: IMetaDataEmit::DeleteFieldMarshal メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
ms.openlocfilehash: 966f2ae20ad9ff4b9c1c9eec32974bc89aa76d13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783964"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="92159-103">IMetaDataEmit::DeleteFieldMarshal メソッド</span><span class="sxs-lookup"><span data-stu-id="92159-103">IMetaDataEmit::DeleteFieldMarshal Method</span></span>

<span data-ttu-id="92159-104">指定したトークンによって参照されるオブジェクトの PInvoke マーシャリングメタデータ署名を破棄します。</span><span class="sxs-lookup"><span data-stu-id="92159-104">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92159-105">構文</span><span class="sxs-lookup"><span data-stu-id="92159-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92159-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92159-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="92159-107">から `mdFieldDef` `mdParamDef` マーシャリングメタデータ署名を削除する対象のフィールドまたはパラメーターを表すまたはトークン。</span><span class="sxs-lookup"><span data-stu-id="92159-107">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92159-108">要件</span><span class="sxs-lookup"><span data-stu-id="92159-108">Requirements</span></span>  

 <span data-ttu-id="92159-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92159-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92159-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="92159-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92159-111">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="92159-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92159-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92159-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92159-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="92159-113">See also</span></span>

- [<span data-ttu-id="92159-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92159-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="92159-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92159-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
