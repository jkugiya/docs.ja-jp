---
description: '詳細については、次を参照してください: EClrUnhandledException 列挙型'
title: EClrUnhandledException 列挙型
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 088d448a92c4d9030208537b9c788477c85f9d37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785550"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="b44d2-103">EClrUnhandledException 列挙型</span><span class="sxs-lookup"><span data-stu-id="b44d2-103">EClrUnhandledException Enumeration</span></span>

<span data-ttu-id="b44d2-104">ユーザーコードで処理されない例外を管理するために使用できるオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b44d2-104">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b44d2-105">構文</span><span class="sxs-lookup"><span data-stu-id="b44d2-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="b44d2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b44d2-106">Members</span></span>  
  
|<span data-ttu-id="b44d2-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b44d2-107">Member</span></span>|<span data-ttu-id="b44d2-108">説明</span><span class="sxs-lookup"><span data-stu-id="b44d2-108">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="b44d2-109">既定の動作を実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b44d2-109">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="b44d2-110">プロセスが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="b44d2-110">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="b44d2-111">共通言語ランタイム (CLR) が未処理の例外を無視し、ホストがそれ以上のアクションを決定できるように指定します。</span><span class="sxs-lookup"><span data-stu-id="b44d2-111">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b44d2-112">解説</span><span class="sxs-lookup"><span data-stu-id="b44d2-112">Remarks</span></span>  

 <span data-ttu-id="b44d2-113">CLR が以前のバージョンと同じように動作するように指定するには、メンバーを使用し `eHostDeterminedPolicy` ます。</span><span class="sxs-lookup"><span data-stu-id="b44d2-113">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b44d2-114">要件</span><span class="sxs-lookup"><span data-stu-id="b44d2-114">Requirements</span></span>  

 <span data-ttu-id="b44d2-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b44d2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b44d2-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b44d2-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b44d2-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b44d2-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b44d2-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b44d2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b44d2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b44d2-119">See also</span></span>

- [<span data-ttu-id="b44d2-120">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="b44d2-120">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="b44d2-121">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="b44d2-121">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="b44d2-122">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b44d2-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="b44d2-123">SetUnhandledExceptionPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="b44d2-123">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="b44d2-124">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b44d2-124">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="b44d2-125">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="b44d2-125">Hosting Enumerations</span></span>](hosting-enumerations.md)
