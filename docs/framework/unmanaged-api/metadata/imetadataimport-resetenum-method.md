---
description: '詳細について: IMetaDataImport:: ResetEnum メソッド'
title: IMetaDataImport::ResetEnum メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
ms.openlocfilehash: 7b1572be2e2b905e6db5cf6e422643dbb76ca9be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670581"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="ff574-103">IMetaDataImport::ResetEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="ff574-103">IMetaDataImport::ResetEnum Method</span></span>

<span data-ttu-id="ff574-104">指定した列挙子を指定した位置にリセットします。</span><span class="sxs-lookup"><span data-stu-id="ff574-104">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff574-105">構文</span><span class="sxs-lookup"><span data-stu-id="ff574-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff574-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff574-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="ff574-107">からリセットする列挙子。</span><span class="sxs-lookup"><span data-stu-id="ff574-107">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="ff574-108">から列挙子を配置する新しい位置。</span><span class="sxs-lookup"><span data-stu-id="ff574-108">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff574-109">要件</span><span class="sxs-lookup"><span data-stu-id="ff574-109">Requirements</span></span>  

 <span data-ttu-id="ff574-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff574-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff574-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="ff574-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff574-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ff574-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff574-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff574-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff574-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff574-114">See also</span></span>

- [<span data-ttu-id="ff574-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff574-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ff574-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff574-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
