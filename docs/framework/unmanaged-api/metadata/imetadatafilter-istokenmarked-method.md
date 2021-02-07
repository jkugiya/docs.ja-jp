---
description: '詳細については、次を参照してください: IMetaDataFilter:: IsTokenMarked されたメソッド'
title: IMetaDataFilter::IsTokenMarked メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
ms.openlocfilehash: dddb0aa9040a2f5ef3ec972bb37a9e8778ddffe8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677786"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="77bf5-103">IMetaDataFilter::IsTokenMarked メソッド</span><span class="sxs-lookup"><span data-stu-id="77bf5-103">IMetaDataFilter::IsTokenMarked Method</span></span>

<span data-ttu-id="77bf5-104">指定したメタデータトークンが処理済みとしてマークされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="77bf5-104">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77bf5-105">構文</span><span class="sxs-lookup"><span data-stu-id="77bf5-105">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77bf5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="77bf5-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="77bf5-107">から処理マークを調べるトークン。</span><span class="sxs-lookup"><span data-stu-id="77bf5-107">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="77bf5-108">入出力が `true` 処理された場合は値。それ以外の場合は `tk` `false` 。</span><span class="sxs-lookup"><span data-stu-id="77bf5-108">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77bf5-109">要件</span><span class="sxs-lookup"><span data-stu-id="77bf5-109">Requirements</span></span>  

 <span data-ttu-id="77bf5-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77bf5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77bf5-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="77bf5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77bf5-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="77bf5-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="77bf5-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77bf5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77bf5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="77bf5-114">See also</span></span>

- [<span data-ttu-id="77bf5-115">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77bf5-115">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
