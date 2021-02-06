---
description: 詳細については、「ICLRPolicyManager インターフェイス」を参照してください。
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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637379"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="e144c-103">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e144c-103">ICLRPolicyManager Interface</span></span>

<span data-ttu-id="e144c-104">エラーやタイムアウトが発生した場合に実行されるポリシーアクションをホストが指定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e144c-104">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e144c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e144c-105">Methods</span></span>  
  
|<span data-ttu-id="e144c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e144c-106">Method</span></span>|<span data-ttu-id="e144c-107">説明</span><span class="sxs-lookup"><span data-stu-id="e144c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e144c-108">SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="e144c-108">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="e144c-109">指定したエラーが発生したときに共通言語ランタイム (CLR) が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e144c-109">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="e144c-110">SetActionOnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="e144c-110">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="e144c-111">指定された操作がタイムアウトしたときに CLR が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e144c-111">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="e144c-112">SetDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="e144c-112">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="e144c-113">指定された操作が発生したときに CLR が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e144c-113">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="e144c-114">SetTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="e144c-114">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="e144c-115">指定された操作のタイムアウト値を設定します。</span><span class="sxs-lookup"><span data-stu-id="e144c-115">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="e144c-116">SetTimeoutAndAction メソッド</span><span class="sxs-lookup"><span data-stu-id="e144c-116">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="e144c-117">指定された操作のタイムアウト値を設定し、操作が発生したときに CLR が実行する必要があるポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e144c-117">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="e144c-118">SetUnhandledExceptionPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="e144c-118">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="e144c-119">未処理の例外が発生した場合の CLR の動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="e144c-119">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e144c-120">要件</span><span class="sxs-lookup"><span data-stu-id="e144c-120">Requirements</span></span>  

 <span data-ttu-id="e144c-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e144c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e144c-122">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e144c-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e144c-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e144c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e144c-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e144c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e144c-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e144c-125">See also</span></span>

- [<span data-ttu-id="e144c-126">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="e144c-126">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="e144c-127">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="e144c-127">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="e144c-128">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="e144c-128">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="e144c-129">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e144c-129">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
