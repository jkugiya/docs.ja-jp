---
description: '詳細については、次を参照してください: EMemoryCriticalLevel 列挙型'
title: EMemoryCriticalLevel 列挙型
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 88965a29164de1ec7b01c2fcc8f51415127e69fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785433"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="82f06-103">EMemoryCriticalLevel 列挙型</span><span class="sxs-lookup"><span data-stu-id="82f06-103">EMemoryCriticalLevel Enumeration</span></span>

<span data-ttu-id="82f06-104">特定のメモリ割り当てが要求されたが、満たされない場合のエラーの影響を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="82f06-104">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f06-105">構文</span><span class="sxs-lookup"><span data-stu-id="82f06-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="82f06-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="82f06-106">Members</span></span>  
  
|<span data-ttu-id="82f06-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="82f06-107">Member</span></span>|<span data-ttu-id="82f06-108">説明</span><span class="sxs-lookup"><span data-stu-id="82f06-108">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="82f06-109">割り当てを要求したドメイン内のマネージコードを実行するために割り当てが不可欠であることを示します。</span><span class="sxs-lookup"><span data-stu-id="82f06-109">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="82f06-110">メモリを割り当てることができない場合、CLR はドメインが引き続き使用可能であることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="82f06-110">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="82f06-111">ホストは、割り当てを満たすことができない場合に実行するアクションを決定します。</span><span class="sxs-lookup"><span data-stu-id="82f06-111">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="82f06-112">CLR は、を自動的に中止するように指示することも、 `AppDomain` [ICLRPolicyManager](iclrpolicymanager-interface.md)でメソッドを呼び出すことによって実行を継続できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="82f06-112">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="82f06-113">は、プロセス内のマネージコードの実行に対して割り当てが不可欠であることを示します。</span><span class="sxs-lookup"><span data-stu-id="82f06-113">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="82f06-114">この値は、起動時とファイナライザーの実行時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="82f06-114">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="82f06-115">メモリを割り当てることができない場合、CLR はプロセスで動作できません。</span><span class="sxs-lookup"><span data-stu-id="82f06-115">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="82f06-116">割り当てが失敗した場合、CLR は実質的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="82f06-116">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="82f06-117">CLR への後続の呼び出しはすべて、HOST_E_CLRNOTAVAILABLE で失敗します。</span><span class="sxs-lookup"><span data-stu-id="82f06-117">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="82f06-118">割り当てを要求したタスクを実行するために割り当てが不可欠であることを示します。</span><span class="sxs-lookup"><span data-stu-id="82f06-118">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="82f06-119">メモリを割り当てることができない場合、CLR はタスクを実行できることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="82f06-119">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="82f06-120">エラーが発生した場合、CLR は <xref:System.Threading.ThreadAbortException> 物理操作システムスレッドでを発生させます。</span><span class="sxs-lookup"><span data-stu-id="82f06-120">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82f06-121">解説</span><span class="sxs-lookup"><span data-stu-id="82f06-121">Remarks</span></span>  

 <span data-ttu-id="82f06-122">[IHostMemoryManager](ihostmemorymanager-interface.md)インターフェイスと[IHostMAlloc](ihostmalloc-interface.md)インターフェイスで定義されているメモリ割り当てメソッドは、この型のパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="82f06-122">The memory allocation methods defined in the [IHostMemoryManager](ihostmemorymanager-interface.md) and [IHostMAlloc](ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="82f06-123">障害の重大度に応じて、割り当て要求を直ちに失敗させるか、または満たされるまで待機するかをホストが決定できます。</span><span class="sxs-lookup"><span data-stu-id="82f06-123">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f06-124">要件</span><span class="sxs-lookup"><span data-stu-id="82f06-124">Requirements</span></span>  

 <span data-ttu-id="82f06-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82f06-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82f06-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="82f06-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82f06-127">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82f06-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82f06-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82f06-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f06-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="82f06-129">See also</span></span>

- [<span data-ttu-id="82f06-130">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82f06-130">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="82f06-131">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="82f06-131">Hosting Enumerations</span></span>](hosting-enumerations.md)
