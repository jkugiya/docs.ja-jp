---
description: '詳細について: ICLRTaskManager:: GetCurrentTaskType メソッド'
title: ICLRTaskManager::GetCurrentTaskType メソッド
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 984cc490123d6146737d3f018fdf712c7c528635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799486"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="3065d-103">ICLRTaskManager::GetCurrentTaskType メソッド</span><span class="sxs-lookup"><span data-stu-id="3065d-103">ICLRTaskManager::GetCurrentTaskType Method</span></span>

<span data-ttu-id="3065d-104">現在実行中のタスクの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="3065d-104">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3065d-105">構文</span><span class="sxs-lookup"><span data-stu-id="3065d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3065d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3065d-106">Parameters</span></span>  

 `pTaskType`  
 <span data-ttu-id="3065d-107">入出力現在実行中のタスクの種類を示す [Etasktype](etasktype-enumeration.md) 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3065d-107">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3065d-108">要件</span><span class="sxs-lookup"><span data-stu-id="3065d-108">Requirements</span></span>  

 <span data-ttu-id="3065d-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3065d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3065d-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3065d-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3065d-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3065d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3065d-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3065d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3065d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="3065d-113">See also</span></span>

- [<span data-ttu-id="3065d-114">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3065d-114">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
