---
description: 詳細については、「EClrFailure 列挙型」を参照してください。
title: EClrFailure 列挙型
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
ms.openlocfilehash: 9f3a2270651e5b05d2d31ed90511b8eb05dd4d44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785589"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="ff3e2-103">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="ff3e2-103">EClrFailure Enumeration</span></span>

<span data-ttu-id="ff3e2-104">ホストがポリシーアクションを設定できるエラーのセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-104">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff3e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="ff3e2-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="ff3e2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ff3e2-106">Members</span></span>  
  
|<span data-ttu-id="ff3e2-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="ff3e2-107">Member</span></span>|<span data-ttu-id="ff3e2-108">説明</span><span class="sxs-lookup"><span data-stu-id="ff3e2-108">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="ff3e2-109">クリティカルでないコード領域に、リソース (スレッド、メモリブロック、ロックなど) を割り当てようとしたときにエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="ff3e2-110">コードの重要な領域に、リソース (スレッド、メモリブロック、ロックなど) を割り当てようとしたときにエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-110">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="ff3e2-111">共通言語ランタイム (CLR) は、プロセスでマネージコードを実行できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-111">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="ff3e2-112">その後では、任意のホスト関数を呼び出すと、HOST_E_CLRNOTAVAILABLE の HRESULT 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-112">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="ff3e2-113">スレッドは、オブジェクトから戻るときにロックを解放できませんでした <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-113">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="ff3e2-114">ホストは、このエラーを設定してスレッドを中止することはできません。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-114">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="ff3e2-115">スタックオーバーフローが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-115">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="ff3e2-116">保護されたメモリの読み取りまたは書き込みが試行されました。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-116">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="ff3e2-117">.NET Framework 4 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-117">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="ff3e2-118">コードコントラクトエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-118">A code contract failure occurred.</span></span> <span data-ttu-id="ff3e2-119">「 [コードコントラクト](../../debug-trace-profile/code-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-119">See [Code Contracts](../../debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff3e2-120">解説</span><span class="sxs-lookup"><span data-stu-id="ff3e2-120">Remarks</span></span>  

 <span data-ttu-id="ff3e2-121">エラー条件のポリシーアクションを指定するためにホストで使用できる[Epolicyaction](epolicyaction-enumeration.md)値の一覧については、 [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-121">See the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="ff3e2-122">クリティカルな、またはクリティカルでないコード領域の詳細については、「 [EClrOperation](eclroperation-enumeration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-122">For more information about critical and non-critical regions of code, see [EClrOperation](eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff3e2-123">要件</span><span class="sxs-lookup"><span data-stu-id="ff3e2-123">Requirements</span></span>  

 <span data-ttu-id="ff3e2-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff3e2-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff3e2-125">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ff3e2-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff3e2-126">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff3e2-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff3e2-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff3e2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff3e2-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff3e2-128">See also</span></span>

- [<span data-ttu-id="ff3e2-129">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff3e2-129">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="ff3e2-130">SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="ff3e2-130">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="ff3e2-131">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff3e2-131">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="ff3e2-132">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="ff3e2-132">Hosting Enumerations</span></span>](hosting-enumerations.md)
