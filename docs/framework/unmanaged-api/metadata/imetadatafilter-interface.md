---
description: 詳細については、「IMetaDataFilter インターフェイス」を参照してください。
title: IMetaDataFilter インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: c994574207ccb26a5cb317e1673145a41f0d837d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677926"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="7a888-103">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a888-103">IMetaDataFilter Interface</span></span>

<span data-ttu-id="7a888-104">メタデータ トークンにマークを付け、フィルター処理をして、既に実行されたアクションが繰り返し行われないようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7a888-104">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a888-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7a888-105">Methods</span></span>  
  
|<span data-ttu-id="7a888-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7a888-106">Method</span></span>|<span data-ttu-id="7a888-107">説明</span><span class="sxs-lookup"><span data-stu-id="7a888-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a888-108">IsTokenMarked メソッド</span><span class="sxs-lookup"><span data-stu-id="7a888-108">IsTokenMarked Method</span></span>](imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="7a888-109">指定したメタデータトークンが処理されたかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="7a888-109">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="7a888-110">MarkToken メソッド</span><span class="sxs-lookup"><span data-stu-id="7a888-110">MarkToken Method</span></span>](imetadatafilter-marktoken-method.md)|<span data-ttu-id="7a888-111">指定したメタデータトークンが処理されたことを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="7a888-111">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="7a888-112">UnmarkAll メソッド</span><span class="sxs-lookup"><span data-stu-id="7a888-112">UnmarkAll Method</span></span>](imetadatafilter-unmarkall-method.md)|<span data-ttu-id="7a888-113">現在のメタデータスコープ内のすべてのトークンから処理マークを削除します。</span><span class="sxs-lookup"><span data-stu-id="7a888-113">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a888-114">要件</span><span class="sxs-lookup"><span data-stu-id="7a888-114">Requirements</span></span>  

 <span data-ttu-id="7a888-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a888-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a888-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="7a888-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a888-117">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a888-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a888-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a888-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a888-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a888-119">See also</span></span>

- [<span data-ttu-id="7a888-120">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a888-120">Metadata Interfaces</span></span>](metadata-interfaces.md)
