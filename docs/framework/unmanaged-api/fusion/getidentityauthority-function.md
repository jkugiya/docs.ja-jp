---
description: '詳細情報: GetIdentityAuthority 関数'
title: GetIdentityAuthority 関数
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
ms.openlocfilehash: 5126aa9b319af41f7ecd30845a9f74ba69016588
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760997"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="ccddc-103">GetIdentityAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="ccddc-103">GetIdentityAuthority Function</span></span>

<span data-ttu-id="ccddc-104">コードオブジェクトのキーを管理する [Iidentity authority](iidentityauthority-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="ccddc-104">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccddc-105">構文</span><span class="sxs-lookup"><span data-stu-id="ccddc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccddc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ccddc-106">Parameters</span></span>  

 `ppIIdentityAuthority`  
 <span data-ttu-id="ccddc-107">入出力返された `IIdentityAuthority` ポインター。</span><span class="sxs-lookup"><span data-stu-id="ccddc-107">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccddc-108">要件</span><span class="sxs-lookup"><span data-stu-id="ccddc-108">Requirements</span></span>  

 <span data-ttu-id="ccddc-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccddc-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccddc-110">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="ccddc-110">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="ccddc-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccddc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccddc-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccddc-112">See also</span></span>

- [<span data-ttu-id="ccddc-113">IIdentityAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ccddc-113">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="ccddc-114">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="ccddc-114">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
