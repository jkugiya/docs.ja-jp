---
description: '詳細について: IMetaDataImport:: GetModuleFromScope メソッド'
title: IMetaDataImport::GetModuleFromScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 8c1e952a45b3827717102428fbd18ceac3951baf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753368"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="faefb-103">IMetaDataImport::GetModuleFromScope メソッド</span><span class="sxs-lookup"><span data-stu-id="faefb-103">IMetaDataImport::GetModuleFromScope Method</span></span>

<span data-ttu-id="faefb-104">現在のメタデータスコープで参照されているモジュールのメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="faefb-104">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faefb-105">構文</span><span class="sxs-lookup"><span data-stu-id="faefb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faefb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="faefb-106">Parameters</span></span>  

 `pmd`  
 <span data-ttu-id="faefb-107">入出力現在のメタデータスコープで参照されているモジュールを表すトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="faefb-107">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faefb-108">要件</span><span class="sxs-lookup"><span data-stu-id="faefb-108">Requirements</span></span>  

 <span data-ttu-id="faefb-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="faefb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faefb-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="faefb-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="faefb-111">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="faefb-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="faefb-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faefb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faefb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="faefb-113">See also</span></span>

- [<span data-ttu-id="faefb-114">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="faefb-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="faefb-115">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="faefb-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
