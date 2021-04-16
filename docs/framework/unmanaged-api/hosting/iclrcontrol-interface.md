---
description: '詳細情報: ICLRControl インターフェイス'
title: ICLRControl インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: e108506d06b746d631f4c15c37d467399de30aba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637665"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="104d9-103">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="104d9-103">ICLRControl Interface</span></span>

<span data-ttu-id="104d9-104">共通言語ランタイム (CLR) への参照をホストで取得し、その側面を構成できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="104d9-104">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="104d9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="104d9-105">Methods</span></span>  
  
|<span data-ttu-id="104d9-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="104d9-106">Method</span></span>|<span data-ttu-id="104d9-107">説明</span><span class="sxs-lookup"><span data-stu-id="104d9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="104d9-108">GetCLRManager メソッド</span><span class="sxs-lookup"><span data-stu-id="104d9-108">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="104d9-109">ホストで CLR を構成するために使用できる任意のマネージャー型のインスタンスへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="104d9-109">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="104d9-110">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="104d9-110">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="104d9-111">アプリケーション ドメイン マネージャーの型として <xref:System.AppDomainManager> から派生した型を設定します。</span><span class="sxs-lookup"><span data-stu-id="104d9-111">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="104d9-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="104d9-112">Requirements</span></span>  

 <span data-ttu-id="104d9-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="104d9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="104d9-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="104d9-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="104d9-115">**ライブラリ:** リソースとして MSCorEE.dll に含まれている</span><span class="sxs-lookup"><span data-stu-id="104d9-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="104d9-116">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="104d9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="104d9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="104d9-117">See also</span></span>

- [<span data-ttu-id="104d9-118">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="104d9-118">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="104d9-119">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="104d9-119">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="104d9-120">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="104d9-120">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="104d9-121">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="104d9-121">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="104d9-122">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="104d9-122">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="104d9-123">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="104d9-123">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="104d9-124">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="104d9-124">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="104d9-125">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="104d9-125">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="104d9-126">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="104d9-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
