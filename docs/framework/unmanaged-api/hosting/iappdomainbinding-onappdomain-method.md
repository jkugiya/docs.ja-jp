---
description: '詳細情報: IAppDomainBinding:: OnAppDomain メソッド'
title: IAppDomainBinding::OnAppDomain メソッド
ms.date: 03/30/2017
api_name:
- IAppDomainBinding.OnAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type:
- apiref
ms.openlocfilehash: de7f37152261a6fe829026607cf135f3ea0b4a84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760603"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="afd81-103">IAppDomainBinding::OnAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="afd81-103">IAppDomainBinding::OnAppDomain Method</span></span>

<span data-ttu-id="afd81-104">アプリケーションドメインが作成されたことをホストに通知するために、共通言語ランタイム (CLR) によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="afd81-104">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afd81-105">構文</span><span class="sxs-lookup"><span data-stu-id="afd81-105">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afd81-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="afd81-106">Parameters</span></span>  

 `pAppdomain`  
 <span data-ttu-id="afd81-107">から新しいアプリケーションドメインを表す [IUnknown](/cpp/atl/iunknown) インターフェイスオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="afd81-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afd81-108">要件</span><span class="sxs-lookup"><span data-stu-id="afd81-108">Requirements</span></span>  

 <span data-ttu-id="afd81-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afd81-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afd81-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="afd81-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="afd81-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="afd81-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afd81-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afd81-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd81-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="afd81-113">See also</span></span>

- [<span data-ttu-id="afd81-114">IAppDomainBinding インターフェイス</span><span class="sxs-lookup"><span data-stu-id="afd81-114">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)
