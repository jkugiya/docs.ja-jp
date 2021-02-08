---
description: '詳細については、次を参照してください: EClrOperation 列挙型'
title: EClrOperation 列挙型
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
ms.openlocfilehash: 9f75762a400955b5f36fb2a337f283e36a32658c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785563"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="99c24-103">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="99c24-103">EClrOperation Enumeration</span></span>

<span data-ttu-id="99c24-104">ホストがポリシーアクションを適用できる操作のセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="99c24-104">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c24-105">構文</span><span class="sxs-lookup"><span data-stu-id="99c24-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="99c24-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="99c24-106">Members</span></span>  
  
|<span data-ttu-id="99c24-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="99c24-107">Member</span></span>|<span data-ttu-id="99c24-108">説明</span><span class="sxs-lookup"><span data-stu-id="99c24-108">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="99c24-109">ホストは、 <xref:System.AppDomain> が正常でない状態でアンロードされた場合に実行されるポリシーアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="99c24-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="99c24-110">ホストは、がアンロードされたときに実行されるポリシーアクションを指定でき <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="99c24-110">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="99c24-111">ホストは、ファイナライザーの実行時に実行されるポリシーアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="99c24-111">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="99c24-112">ホストは、プロセスが終了したときに実行するポリシーアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="99c24-112">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="99c24-113">ホストは、スレッドが中止されたときに実行されるポリシーアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="99c24-113">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="99c24-114">ホストは、コードの重要な領域でルースレッドの中止が発生したときに実行されるポリシーアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="99c24-114">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="99c24-115">ホストは、非クリティカルなコード領域で、ルードスレッドの中止が発生したときに実行するポリシーアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="99c24-115">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99c24-116">解説</span><span class="sxs-lookup"><span data-stu-id="99c24-116">Remarks</span></span>  

 <span data-ttu-id="99c24-117">共通言語ランタイム (CLR) の信頼性インフラストラクチャでは、コードの重要な領域で発生する中止とリソース割り当ての失敗と、コードの重要ではない領域で発生するエラーを区別します。</span><span class="sxs-lookup"><span data-stu-id="99c24-117">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="99c24-118">この区別は、コード内でエラーが発生した場所に応じて、ホストがさまざまなポリシーを設定できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="99c24-118">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="99c24-119">*コードの重要な領域* は、タスクの中止、またはリソースの要求を完了できないことが CLR によって保証されない場合、現在のタスクにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="99c24-119">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="99c24-120">たとえば、タスクがロックを保持していて、メモリ割り当て要求の発生時に失敗したことを示す HRESULT を受け取った場合、には、 <xref:System.AppDomain> <xref:System.AppDomain> 同じロックを待機している他のタスクが含まれている可能性があるため、そのタスクを中止しての安定性を保証するだけでは不十分です。</span><span class="sxs-lookup"><span data-stu-id="99c24-120">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="99c24-121">現在のタスクを破棄すると、その他のタスクが応答を停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="99c24-121">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="99c24-122">このような場合、ホストは、潜在的に不安定になるリスクではなく、全体をアンロードする機能を必要とし <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="99c24-122">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="99c24-123">一方、クリティカルでは *ないコード領域* とは、CLR が、エラーが発生したタスクのみに影響を与えることを CLR が保証できる領域です。</span><span class="sxs-lookup"><span data-stu-id="99c24-123">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="99c24-124">また、この CLR では、グレースフルとグレースフルの (ルード) 中止が区別されます。</span><span class="sxs-lookup"><span data-stu-id="99c24-124">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="99c24-125">一般に、通常または正常な中止では、タスクを中止する前に例外処理ルーチンとファイナライザーを実行するすべての作業を行います。ただし、ルードアボートではこのような保証は行われません。</span><span class="sxs-lookup"><span data-stu-id="99c24-125">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99c24-126">要件</span><span class="sxs-lookup"><span data-stu-id="99c24-126">Requirements</span></span>  

 <span data-ttu-id="99c24-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99c24-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99c24-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="99c24-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99c24-129">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99c24-129">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99c24-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99c24-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c24-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="99c24-131">See also</span></span>

- [<span data-ttu-id="99c24-132">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="99c24-132">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="99c24-133">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="99c24-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="99c24-134">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99c24-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="99c24-135">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99c24-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="99c24-136">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="99c24-136">Hosting Enumerations</span></span>](hosting-enumerations.md)
