---
description: '詳細について: IHostTaskManager:: GetStackGuarantee メソッド'
title: IHostTaskManager::GetStackGuarantee メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
ms.openlocfilehash: 6c8bd9839ea0c1fdb72fbbd296061d1a2b6edfe1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753797"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="19950-103">IHostTaskManager::GetStackGuarantee メソッド</span><span class="sxs-lookup"><span data-stu-id="19950-103">IHostTaskManager::GetStackGuarantee Method</span></span>

<span data-ttu-id="19950-104">スタック操作が完了した後、プロセスが終了する前に使用可能であることが保証されているスタック領域の量を取得します。</span><span class="sxs-lookup"><span data-stu-id="19950-104">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19950-105">構文</span><span class="sxs-lookup"><span data-stu-id="19950-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19950-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="19950-106">Parameters</span></span>  

 `pGuarantee`  
 <span data-ttu-id="19950-107">入出力使用可能なバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="19950-107">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19950-108">要件</span><span class="sxs-lookup"><span data-stu-id="19950-108">Requirements</span></span>  

 <span data-ttu-id="19950-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19950-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19950-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="19950-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19950-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="19950-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19950-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19950-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19950-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="19950-113">See also</span></span>

- [<span data-ttu-id="19950-114">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19950-114">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
