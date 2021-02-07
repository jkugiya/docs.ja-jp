---
description: '詳細については、「IManagedObject:: GetObjectIdentity メソッド」を参照してください。'
title: IManagedObject::GetObjectIdentity メソッド
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
ms.openlocfilehash: 8929819bbf490680b5f3f1f47b9f3b8e830d57ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671166"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="a94a8-103">IManagedObject::GetObjectIdentity メソッド</span><span class="sxs-lookup"><span data-stu-id="a94a8-103">IManagedObject::GetObjectIdentity Method</span></span>

<span data-ttu-id="a94a8-104">このマネージオブジェクトの id を取得します。</span><span class="sxs-lookup"><span data-stu-id="a94a8-104">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a94a8-105">構文</span><span class="sxs-lookup"><span data-stu-id="a94a8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a94a8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a94a8-106">Parameters</span></span>  

 `pBSTRGUID`  
 <span data-ttu-id="a94a8-107">入出力オブジェクトが存在するプロセスの GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a94a8-107">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="a94a8-108">入出力オブジェクトのアプリケーションドメインの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a94a8-108">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="a94a8-109">入出力COM クラシック v テーブル内のオブジェクトのインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a94a8-109">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a94a8-110">解説</span><span class="sxs-lookup"><span data-stu-id="a94a8-110">Remarks</span></span>  

 <span data-ttu-id="a94a8-111">マネージオブジェクトの id には、プロセス GUID、アプリケーションドメイン ID、および COM クラシック v テーブルのオブジェクトのインデックスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a94a8-111">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a94a8-112">要件</span><span class="sxs-lookup"><span data-stu-id="a94a8-112">Requirements</span></span>  

 <span data-ttu-id="a94a8-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a94a8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a94a8-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a94a8-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a94a8-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a94a8-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a94a8-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a94a8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a94a8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a94a8-117">See also</span></span>

- [<span data-ttu-id="a94a8-118">IManagedObject インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a94a8-118">IManagedObject Interface</span></span>](imanagedobject-interface.md)
