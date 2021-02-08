---
description: '詳細について: IMetaDataEmit::D eleteClassLayout メソッド'
title: IMetaDataEmit::DeleteClassLayout メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
ms.openlocfilehash: 44be89f415087a1457a83bb1167e1017d26ed5ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783990"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="e9979-103">IMetaDataEmit::DeleteClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="e9979-103">IMetaDataEmit::DeleteClassLayout Method</span></span>

<span data-ttu-id="e9979-104">指定したトークンによって表される型のクラスレイアウトメタデータシグネチャを破棄します。</span><span class="sxs-lookup"><span data-stu-id="e9979-104">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9979-105">構文</span><span class="sxs-lookup"><span data-stu-id="e9979-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9979-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9979-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="e9979-107">から `mdTypeDef` クラスレイアウトが削除される型を表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="e9979-107">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9979-108">要件</span><span class="sxs-lookup"><span data-stu-id="e9979-108">Requirements</span></span>  

 <span data-ttu-id="e9979-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9979-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9979-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e9979-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9979-111">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9979-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9979-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9979-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9979-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9979-113">See also</span></span>

- [<span data-ttu-id="e9979-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9979-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e9979-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9979-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
