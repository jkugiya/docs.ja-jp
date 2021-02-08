---
description: '詳細情報: EHostBindingPolicyModifyFlags 列挙型'
title: EHostBindingPolicyModifyFlags 列挙型
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: be8a15cad49097d1ea2e206e01da2d5d5dcb165a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785485"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="115ba-103">EHostBindingPolicyModifyFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="115ba-103">EHostBindingPolicyModifyFlags Enumeration</span></span>

<span data-ttu-id="115ba-104">ソースアセンブリからターゲットアセンブリにポリシー変更を適用するときに、共通言語ランタイム (CLR) が実行するリダイレクトの種類をホストが指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="115ba-104">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="115ba-105">構文</span><span class="sxs-lookup"><span data-stu-id="115ba-105">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="115ba-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="115ba-106">Members</span></span>  
  
|<span data-ttu-id="115ba-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="115ba-107">Member</span></span>|<span data-ttu-id="115ba-108">説明</span><span class="sxs-lookup"><span data-stu-id="115ba-108">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="115ba-109">CLR がソースアセンブリのポリシー値をターゲットアセンブリのポリシー値に連結するように指定します。</span><span class="sxs-lookup"><span data-stu-id="115ba-109">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="115ba-110">CLR が既定のアクションを実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="115ba-110">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="115ba-111">CLR がターゲットアセンブリのポリシー値を最大値に設定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="115ba-111">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="115ba-112">CLR がターゲットアセンブリのポリシー値をソースアセンブリのポリシー値に置き換えることを指定します。</span><span class="sxs-lookup"><span data-stu-id="115ba-112">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="115ba-113">解説</span><span class="sxs-lookup"><span data-stu-id="115ba-113">Remarks</span></span>  

 <span data-ttu-id="115ba-114">[ICLRHostBindingPolicyManager:: ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)メソッドは、型のパラメーターを受け取り `EHostBindingPolicyModifyFlags` ます。</span><span class="sxs-lookup"><span data-stu-id="115ba-114">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="115ba-115">要件</span><span class="sxs-lookup"><span data-stu-id="115ba-115">Requirements</span></span>  

 <span data-ttu-id="115ba-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="115ba-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="115ba-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="115ba-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="115ba-118">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="115ba-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="115ba-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="115ba-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="115ba-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="115ba-120">See also</span></span>

- [<span data-ttu-id="115ba-121">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="115ba-121">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="115ba-122">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="115ba-122">Hosting Enumerations</span></span>](hosting-enumerations.md)
