---
description: '詳細情報: GetAppIdAuthority 関数'
title: GetAppIdAuthority 関数
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
ms.openlocfilehash: a0c2a7b754c2b014b189f96fd3c27347571cc0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761058"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="78b28-103">GetAppIdAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="78b28-103">GetAppIdAuthority Function</span></span>

<span data-ttu-id="78b28-104">アプリケーション id と参照のキーを管理する [Iappidauthority](iappidauthority-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="78b28-104">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b28-105">構文</span><span class="sxs-lookup"><span data-stu-id="78b28-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="78b28-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78b28-106">Parameters</span></span>  

 `ppIAppIdAuthority`  
 <span data-ttu-id="78b28-107">入出力返された `IAppIdAuthority` ポインター。</span><span class="sxs-lookup"><span data-stu-id="78b28-107">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78b28-108">要件</span><span class="sxs-lookup"><span data-stu-id="78b28-108">Requirements</span></span>  

 <span data-ttu-id="78b28-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78b28-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78b28-110">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="78b28-110">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="78b28-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78b28-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b28-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="78b28-112">See also</span></span>

- [<span data-ttu-id="78b28-113">IAppIdAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78b28-113">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="78b28-114">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="78b28-114">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
