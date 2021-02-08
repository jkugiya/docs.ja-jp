---
description: '詳細について: IHostFilter:: MarkToken メソッド'
title: IHostFilter::MarkToken メソッド
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
ms.openlocfilehash: c8f5ecdef56b77e1b0031a93d6d8f7de79de4c3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784185"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="0ebf4-103">IHostFilter::MarkToken メソッド</span><span class="sxs-lookup"><span data-stu-id="0ebf4-103">IHostFilter::MarkToken Method</span></span>

<span data-ttu-id="0ebf4-104">指定されたメタデータトークンが処理されることを示します。</span><span class="sxs-lookup"><span data-stu-id="0ebf4-104">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ebf4-105">構文</span><span class="sxs-lookup"><span data-stu-id="0ebf4-105">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ebf4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0ebf4-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="0ebf4-107">から処理するメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="0ebf4-107">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ebf4-108">解説</span><span class="sxs-lookup"><span data-stu-id="0ebf4-108">Remarks</span></span>  

 <span data-ttu-id="0ebf4-109">通常、トークンがメタデータスコープ内にある場合は、トークンを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ebf4-109">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="0ebf4-110">メソッドは、 `MarkToken` [IMetaDataEmit:: SetHandler](imetadataemit-sethandler-method.md) メソッドを使用してメタデータエンジンに渡されます。</span><span class="sxs-lookup"><span data-stu-id="0ebf4-110">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ebf4-111">要件</span><span class="sxs-lookup"><span data-stu-id="0ebf4-111">Requirements</span></span>  

 <span data-ttu-id="0ebf4-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ebf4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebf4-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0ebf4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ebf4-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ebf4-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ebf4-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebf4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebf4-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ebf4-116">See also</span></span>

- [<span data-ttu-id="0ebf4-117">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ebf4-117">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="0ebf4-118">IHostFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ebf4-118">IHostFilter Interface</span></span>](ihostfilter-interface.md)
