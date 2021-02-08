---
description: 詳細については、「ICLRHostBindingPolicyManager インターフェイス」を参照してください。
title: ICLRHostBindingPolicyManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
ms.openlocfilehash: 07a18d622ff8d8483fe6dcb0242cb5f1ee284b14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789945"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="a943f-103">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a943f-103">ICLRHostBindingPolicyManager Interface</span></span>

<span data-ttu-id="a943f-104">ホストが現在のバインドポリシーを評価し、指定されたアセンブリのポリシー変更を伝達するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a943f-104">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a943f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a943f-105">Methods</span></span>  
  
|<span data-ttu-id="a943f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a943f-106">Method</span></span>|<span data-ttu-id="a943f-107">説明</span><span class="sxs-lookup"><span data-stu-id="a943f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a943f-108">EvaluatePolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="a943f-108">EvaluatePolicy Method</span></span>](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="a943f-109">ホストの代わりにバインドポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="a943f-109">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="a943f-110">ModifyApplicationPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="a943f-110">ModifyApplicationPolicy Method</span></span>](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="a943f-111">指定したアセンブリのバインディングポリシーを変更し、新しいバージョンのポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a943f-111">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a943f-112">要件</span><span class="sxs-lookup"><span data-stu-id="a943f-112">Requirements</span></span>  

 <span data-ttu-id="a943f-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a943f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a943f-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a943f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a943f-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a943f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a943f-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a943f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a943f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a943f-117">See also</span></span>

- [<span data-ttu-id="a943f-118">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a943f-118">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="a943f-119">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a943f-119">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="a943f-120">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a943f-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
