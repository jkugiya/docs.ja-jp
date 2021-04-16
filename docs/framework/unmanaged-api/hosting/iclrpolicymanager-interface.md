---
description: '詳細情報: ICLRPolicyManager インターフェイス'
title: ICLRPolicyManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 8823f1db8b15b327306ff3c592b46c94537f4331
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637379"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="83900-103">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83900-103">ICLRPolicyManager Interface</span></span>

<span data-ttu-id="83900-104">エラーやタイムアウトが発生した場合に実行されるポリシー アクションをホストで指定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="83900-104">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="83900-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="83900-105">Methods</span></span>  
  
|<span data-ttu-id="83900-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="83900-106">Method</span></span>|<span data-ttu-id="83900-107">説明</span><span class="sxs-lookup"><span data-stu-id="83900-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="83900-108">SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="83900-108">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="83900-109">指定した失敗の発生時に共通言語ランタイム (CLR) により実行されるポリシー アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="83900-109">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="83900-110">SetActionOnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="83900-110">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="83900-111">指定された操作がタイムアウトしたときに CLR により実行されるポリシー アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="83900-111">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="83900-112">SetDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="83900-112">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="83900-113">指定された操作が発生したときに CLR により実行されるポリシー アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="83900-113">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="83900-114">SetTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="83900-114">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="83900-115">指定された操作のタイムアウト値を設定します。</span><span class="sxs-lookup"><span data-stu-id="83900-115">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="83900-116">SetTimeoutAndAction メソッド</span><span class="sxs-lookup"><span data-stu-id="83900-116">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="83900-117">指定された操作のタイムアウト値を設定し、その操作が行われたとき、CLR で行うポリシー アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="83900-117">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="83900-118">SetUnhandledExceptionPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="83900-118">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="83900-119">未処理の例外が発生した場合の CLR の動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="83900-119">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83900-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="83900-120">Requirements</span></span>  

 <span data-ttu-id="83900-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83900-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83900-122">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83900-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83900-123">**ライブラリ:** リソースとして MSCorEE.dll に含まれている</span><span class="sxs-lookup"><span data-stu-id="83900-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83900-124">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83900-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83900-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="83900-125">See also</span></span>

- [<span data-ttu-id="83900-126">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="83900-126">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="83900-127">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="83900-127">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="83900-128">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="83900-128">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="83900-129">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83900-129">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
