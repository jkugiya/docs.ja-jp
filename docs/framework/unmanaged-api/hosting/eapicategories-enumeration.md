---
description: '詳細については、次を参照してください: EApiCategories 列挙型'
title: EApiCategories 列挙型
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
ms.openlocfilehash: 58a7d4fa4d0c965bf9158ad6713185782d4ae94a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785628"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="d5cd9-103">EApiCategories 列挙型</span><span class="sxs-lookup"><span data-stu-id="d5cd9-103">EApiCategories Enumeration</span></span>

<span data-ttu-id="d5cd9-104">部分的に信頼されたコードでホストが実行をブロックできる機能のカテゴリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-104">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5cd9-105">構文</span><span class="sxs-lookup"><span data-stu-id="d5cd9-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="d5cd9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d5cd9-106">Members</span></span>  
  
|<span data-ttu-id="d5cd9-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="d5cd9-107">Member</span></span>|<span data-ttu-id="d5cd9-108">説明</span><span class="sxs-lookup"><span data-stu-id="d5cd9-108">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="d5cd9-109">他のフィールドの対象となるすべてのマネージクラスおよびメンバーが、 `EApiCategories` 部分的に信頼されたコードでの実行をブロックされるように指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-109">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="d5cd9-110">外部プロセスの作成、操作、および破棄を許可するマネージクラスおよびメンバーが、部分的に信頼されたコードでの実行をブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="d5cd9-111">外部スレッドの作成、操作、および破棄を許可するマネージクラスおよびメンバーが、部分的に信頼されたコードでの実行をブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-111">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="d5cd9-112">中止時にメモリをリークする可能性のあるマネージ型およびメンバーが、部分的に信頼されたコードで実行されないようにブロックすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-112">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="d5cd9-113">部分的に信頼されたコードでは、マネージコードのカテゴリの実行をブロックしないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-113">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="d5cd9-114">共通言語ランタイム (CLR) のセキュリティインフラストラクチャが、部分的に信頼されたコードによって使用されるのをブロックすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-114">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="d5cd9-115">ホストされるプロセスに影響を与える可能性があるマネージクラスおよびメンバーが、部分的に信頼されたコードで実行されないように指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-115">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="d5cd9-116">ホストされているプロセスのスレッドに影響を与える可能性のあるマネージクラスおよびメンバーが、部分的に信頼されたコードでの実行をブロックされるように指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-116">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="d5cd9-117">マネージクラスおよび共有状態を公開するメンバーが、部分的に信頼されたコードで実行されないようにブロックすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-117">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="d5cd9-118">ユーザーコードがロックを保持することを許可する共通言語ランタイムクラスおよびメンバーが、部分的に信頼されたコードでの実行をブロックするように指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-118">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="d5cd9-119">人間の操作を許可または必要とするマネージクラスおよびメンバーが、部分的に信頼されたコードでの実行をブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-119">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5cd9-120">解説</span><span class="sxs-lookup"><span data-stu-id="d5cd9-120">Remarks</span></span>  

 <span data-ttu-id="d5cd9-121">[ICLRHostProtectionManager:: SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md)メソッドは、型のパラメーターを受け取り `EApiCategories` ます。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-121">The [ICLRHostProtectionManager::SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="d5cd9-122">`EApiCategories`列挙体とメソッドは、 `SetProtectedCategories` マネージクラスに直接関連付けられ <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-122">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d5cd9-123">マネージクラスは、値に直接対応する値を持つ列挙体と共に使用され、 <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> `EApiCategories` によって記述されたカテゴリに対応する機能を公開するマネージ型およびメンバーをマークし `EApiCategories` ます。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-123">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5cd9-124">要件</span><span class="sxs-lookup"><span data-stu-id="d5cd9-124">Requirements</span></span>  

 <span data-ttu-id="d5cd9-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5cd9-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5cd9-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d5cd9-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5cd9-127">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5cd9-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5cd9-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5cd9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5cd9-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5cd9-129">See also</span></span>

- [<span data-ttu-id="d5cd9-130">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5cd9-130">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="d5cd9-131">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="d5cd9-131">Hosting Enumerations</span></span>](hosting-enumerations.md)
