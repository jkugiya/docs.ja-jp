---
description: '詳細情報: METAHOST_CONFIG_FLAGS 列挙型'
title: METAHOST_CONFIG_FLAGS 列挙体
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
ms.openlocfilehash: 56d70f50d3b4c48b7fbf1aa3be6fc11cda904638
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679642"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="09a25-103">METAHOST_CONFIG_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="09a25-103">METAHOST_CONFIG_FLAGS Enumeration</span></span>

<span data-ttu-id="09a25-104">`pdwConfigFlags` [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md)メソッドのパラメーターで返されるフラグについて説明します。これは、 `useLegacyV2RuntimeActivationPolicy` 構成ファイルの[ \<startup> 要素](../../configure-apps/file-schema/startup/startup-element.md)内の属性の存在と設定を示します。</span><span class="sxs-lookup"><span data-stu-id="09a25-104">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09a25-105">構文</span><span class="sxs-lookup"><span data-stu-id="09a25-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="09a25-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="09a25-106">Members</span></span>  
  
|<span data-ttu-id="09a25-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="09a25-107">Member</span></span>|<span data-ttu-id="09a25-108">説明</span><span class="sxs-lookup"><span data-stu-id="09a25-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="09a25-109">`useLegacyV2RuntimeActivationPolicy`属性が[ \<startup> 要素](../../configure-apps/file-schema/startup/startup-element.md)内に存在しませんでした。</span><span class="sxs-lookup"><span data-stu-id="09a25-109">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="09a25-110">`useLegacyV2RuntimeActivationPolicy`属性が存在し、がに設定されて `true` います。</span><span class="sxs-lookup"><span data-stu-id="09a25-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="09a25-111">`useLegacyV2RuntimeActivationPolicy`属性が存在し、がに設定されて `false` います。</span><span class="sxs-lookup"><span data-stu-id="09a25-111">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="09a25-112">に関連する値を取得するには、このマスクをで返される値に適用 `pdwConfigFlags` `useLegacyV2RuntimeActivationPolicy` します。</span><span class="sxs-lookup"><span data-stu-id="09a25-112">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09a25-113">解説</span><span class="sxs-lookup"><span data-stu-id="09a25-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09a25-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="09a25-114">Requirements</span></span>  

 <span data-ttu-id="09a25-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09a25-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09a25-116">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="09a25-116">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="09a25-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="09a25-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09a25-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09a25-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a25-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="09a25-119">See also</span></span>

- [<span data-ttu-id="09a25-120">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="09a25-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="09a25-121">GetRequestedRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="09a25-121">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="09a25-122">\<startup> 要素</span><span class="sxs-lookup"><span data-stu-id="09a25-122">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
