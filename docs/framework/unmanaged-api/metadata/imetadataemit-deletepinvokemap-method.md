---
description: '詳細について: IMetaDataEmit::D eletePinvokeMap メソッド'
title: IMetaDataEmit::DeletePinvokeMap メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
ms.openlocfilehash: 977fd600600cdfba0fd9fd5d383648ffbf63229f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783977"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="082d5-103">IMetaDataEmit::DeletePinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="082d5-103">IMetaDataEmit::DeletePinvokeMap Method</span></span>

<span data-ttu-id="082d5-104">指定したトークンによって参照されるオブジェクトの PInvoke マッピングメタデータを破棄します。</span><span class="sxs-lookup"><span data-stu-id="082d5-104">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="082d5-105">構文</span><span class="sxs-lookup"><span data-stu-id="082d5-105">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="082d5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="082d5-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="082d5-107">から `mdFieldDef` `mdMethodDef` PInvoke マッピングメタデータを削除する対象のオブジェクトを表すまたはトークン。</span><span class="sxs-lookup"><span data-stu-id="082d5-107">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="082d5-108">要件</span><span class="sxs-lookup"><span data-stu-id="082d5-108">Requirements</span></span>  

 <span data-ttu-id="082d5-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="082d5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="082d5-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="082d5-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="082d5-111">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="082d5-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="082d5-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="082d5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="082d5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="082d5-113">See also</span></span>

- [<span data-ttu-id="082d5-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="082d5-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="082d5-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="082d5-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
