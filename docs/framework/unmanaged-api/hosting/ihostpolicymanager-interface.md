---
description: 詳細については、「IHostPolicyManager インターフェイス」を参照してください。
title: IHostPolicyManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: d823ee2526019188afd17df903b61a720e18207f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671933"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="5394a-103">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5394a-103">IHostPolicyManager Interface</span></span>

<span data-ttu-id="5394a-104">中止、タイムアウト、またはエラーが発生した場合に共通言語ランタイム (CLR) が実行するアクションをホストに通知するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5394a-104">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5394a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5394a-105">Methods</span></span>  
  
|<span data-ttu-id="5394a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5394a-106">Method</span></span>|<span data-ttu-id="5394a-107">説明</span><span class="sxs-lookup"><span data-stu-id="5394a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5394a-108">OnDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="5394a-108">OnDefaultAction Method</span></span>](ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="5394a-109">CLR が、スレッドの中止またはアンロードに応答して [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) の呼び出しによって指定された既定のアクションを実行しようとしていることをホストに通知し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="5394a-109">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="5394a-110">OnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="5394a-110">OnFailure Method</span></span>](ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="5394a-111">リソース割り当てまたは再利用エラーに応答して、CLR が [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) の呼び出しによって指定されたアクションを実行しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5394a-111">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="5394a-112">OnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="5394a-112">OnTimeout Method</span></span>](ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="5394a-113">タイムアウトに応答して [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) への呼び出しによって指定されたアクションを CLR が実行しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5394a-113">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5394a-114">要件</span><span class="sxs-lookup"><span data-stu-id="5394a-114">Requirements</span></span>  

 <span data-ttu-id="5394a-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5394a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5394a-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5394a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5394a-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5394a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5394a-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5394a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5394a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="5394a-119">See also</span></span>

- [<span data-ttu-id="5394a-120">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="5394a-120">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="5394a-121">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="5394a-121">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="5394a-122">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="5394a-122">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="5394a-123">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5394a-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="5394a-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5394a-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
