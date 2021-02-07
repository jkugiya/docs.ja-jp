---
description: '詳細について: ICeeGen:: GetIMapTokenIface メソッド'
title: ICeeGen::GetIMapTokenIface メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIMapTokenIface
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIMapTokenIface
helpviewer_keywords:
- GetIMapTokenIface method [.NET Framework metadata]
- ICeeGen::GetIMapTokenIface method [.NET Framework metadata]
ms.assetid: 847a5531-c37d-49cd-8844-9e54b5d86cf7
topic_type:
- apiref
ms.openlocfilehash: bfadcead611a8cc4e3e6117e0f0bb3635c042d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706956"
---
# <a name="iceegengetimaptokeniface-method"></a><span data-ttu-id="6faad-103">ICeeGen::GetIMapTokenIface メソッド</span><span class="sxs-lookup"><span data-stu-id="6faad-103">ICeeGen::GetIMapTokenIface Method</span></span>

<span data-ttu-id="6faad-104">指定したトークンによって参照されるインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6faad-104">Gets the interface referenced by the specified token.</span></span>  
  
 <span data-ttu-id="6faad-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6faad-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6faad-106">構文</span><span class="sxs-lookup"><span data-stu-id="6faad-106">Syntax</span></span>  
  
```cpp  
HRESULT GetIMapTokenIface (  
    [in, out] IUnknown   **pIMapToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6faad-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6faad-107">Parameters</span></span>  

 `pIMapToken`  
 <span data-ttu-id="6faad-108">[入力、出力]返されるインターフェイスのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="6faad-108">[in, out] The metadata token for the interface to be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6faad-109">要件</span><span class="sxs-lookup"><span data-stu-id="6faad-109">Requirements</span></span>  

 <span data-ttu-id="6faad-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6faad-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6faad-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="6faad-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6faad-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="6faad-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6faad-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6faad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6faad-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6faad-114">See also</span></span>

- [<span data-ttu-id="6faad-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6faad-115">ICeeGen Interface</span></span>](iceegen-interface.md)
