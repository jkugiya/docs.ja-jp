---
description: '詳細情報: EBindPolicyLevels 列挙型'
title: EBindPolicyLevels 列挙型
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
ms.openlocfilehash: 00e10cff79cdd782e8d9ab8e9b7e1e3f388fb1ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785615"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="423f6-103">EBindPolicyLevels 列挙型</span><span class="sxs-lookup"><span data-stu-id="423f6-103">EBindPolicyLevels Enumeration</span></span>

<span data-ttu-id="423f6-104">アセンブリポリシーを適用または変更するレベルを指定するフラグを提供します。</span><span class="sxs-lookup"><span data-stu-id="423f6-104">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="423f6-105">構文</span><span class="sxs-lookup"><span data-stu-id="423f6-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="423f6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="423f6-106">Members</span></span>  
  
|<span data-ttu-id="423f6-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="423f6-107">Member</span></span>|<span data-ttu-id="423f6-108">説明</span><span class="sxs-lookup"><span data-stu-id="423f6-108">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="423f6-109">ポリシーを管理者レベルで適用する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="423f6-109">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="423f6-110">ポリシーをアプリケーションレベルで適用する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="423f6-110">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="423f6-111">ポリシーをホストレベルで適用する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="423f6-111">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="423f6-112">ポリシーレベルのフラグを指定しません。</span><span class="sxs-lookup"><span data-stu-id="423f6-112">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="423f6-113">ポリシーをパブリッシャーレベルで適用する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="423f6-113">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="423f6-114">ポリシーを変数レベルで適用できることを指定します。</span><span class="sxs-lookup"><span data-stu-id="423f6-114">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="423f6-115">ポリシーで .NET Framework アセンブリの実装間の移植性をサポートする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="423f6-115">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="423f6-116">構成ファイルの要素を参照してください [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="423f6-116">See the [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="423f6-117">ポリシーを共通言語ランタイム (CLR) のポリシーに統合することを指定します。</span><span class="sxs-lookup"><span data-stu-id="423f6-117">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="423f6-118">解説</span><span class="sxs-lookup"><span data-stu-id="423f6-118">Remarks</span></span>  

 <span data-ttu-id="423f6-119">この列挙体は、アプリケーションポリシーの変更を指定するために、 [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) インターフェイスのメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="423f6-119">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="423f6-120">要件</span><span class="sxs-lookup"><span data-stu-id="423f6-120">Requirements</span></span>  

 <span data-ttu-id="423f6-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="423f6-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="423f6-122">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="423f6-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="423f6-123">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="423f6-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="423f6-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="423f6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="423f6-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="423f6-125">See also</span></span>

- [<span data-ttu-id="423f6-126">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="423f6-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="423f6-127">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="423f6-127">Hosting Enumerations</span></span>](hosting-enumerations.md)
