---
description: '詳細について: IMetaDataFilter:: MarkToken メソッド'
title: IMetaDataFilter::MarkToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
ms.openlocfilehash: 97191533ae7d2bdc951521f1929a4c001c521b9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677795"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="7fc4c-103">IMetaDataFilter::MarkToken メソッド</span><span class="sxs-lookup"><span data-stu-id="7fc4c-103">IMetaDataFilter::MarkToken Method</span></span>

<span data-ttu-id="7fc4c-104">指定したメタデータトークンが処理されたことを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="7fc4c-104">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fc4c-105">構文</span><span class="sxs-lookup"><span data-stu-id="7fc4c-105">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fc4c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7fc4c-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="7fc4c-107">から処理済みとしてマークするトークン。</span><span class="sxs-lookup"><span data-stu-id="7fc4c-107">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fc4c-108">要件</span><span class="sxs-lookup"><span data-stu-id="7fc4c-108">Requirements</span></span>  

 <span data-ttu-id="7fc4c-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fc4c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fc4c-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="7fc4c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7fc4c-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="7fc4c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7fc4c-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fc4c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc4c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fc4c-113">See also</span></span>

- [<span data-ttu-id="7fc4c-114">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7fc4c-114">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
