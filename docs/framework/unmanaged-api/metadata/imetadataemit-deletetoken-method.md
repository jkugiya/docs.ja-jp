---
description: '詳細について: IMetaDataEmit::D eleteToken メソッド'
title: IMetaDataEmit::DeleteToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
ms.openlocfilehash: 5c28b56b06f994057409ef8fa17179cb0b0e205b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783951"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="96e18-103">IMetaDataEmit::DeleteToken メソッド</span><span class="sxs-lookup"><span data-stu-id="96e18-103">IMetaDataEmit::DeleteToken Method</span></span>

<span data-ttu-id="96e18-104">現在のメタデータスコープから指定されたトークンを削除します。</span><span class="sxs-lookup"><span data-stu-id="96e18-104">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e18-105">構文</span><span class="sxs-lookup"><span data-stu-id="96e18-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (
    [in]  mdToken     tkObj
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96e18-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96e18-106">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="96e18-107">から削除するトークン。</span><span class="sxs-lookup"><span data-stu-id="96e18-107">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96e18-108">要件</span><span class="sxs-lookup"><span data-stu-id="96e18-108">Requirements</span></span>  

 <span data-ttu-id="96e18-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96e18-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96e18-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="96e18-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96e18-111">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="96e18-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96e18-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96e18-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e18-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="96e18-113">See also</span></span>

- [<span data-ttu-id="96e18-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96e18-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="96e18-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96e18-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
