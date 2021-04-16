---
description: '詳細情報: ICorConfiguration::SetGCHostControl メソッド'
title: ICorConfiguration::SetGCHostControl メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
ms.openlocfilehash: 4d3d6e5e5275adf02f9d693234a5c8e77714fd03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636651"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="6468d-103">ICorConfiguration::SetGCHostControl メソッド</span><span class="sxs-lookup"><span data-stu-id="6468d-103">ICorConfiguration::SetGCHostControl Method</span></span>

<span data-ttu-id="6468d-104">仮想メモリの制限を変更するようにホストに要求するために、ガベージ コレクターによって使用されるコールバック インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="6468d-104">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6468d-105">構文</span><span class="sxs-lookup"><span data-stu-id="6468d-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6468d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6468d-106">Parameters</span></span>  

 `pGCHostControl`  
 <span data-ttu-id="6468d-107">仮想メモリの制限を変更するように、ガベージ コレクターからホストに要求ができるようにする [IGCHostControl](igchostcontrol-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6468d-107">[in] A pointer to an [IGCHostControl](igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6468d-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="6468d-108">Requirements</span></span>  

 <span data-ttu-id="6468d-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6468d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6468d-110">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6468d-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6468d-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="6468d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6468d-112">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6468d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6468d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6468d-113">See also</span></span>

- [<span data-ttu-id="6468d-114">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6468d-114">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
