---
description: 詳細については、「CorNotificationForTokenMovement 列挙型」を参照してください。
title: CorNotificationForTokenMovement 列挙型
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
ms.openlocfilehash: 1975598b756499c9c0b017bf7eba9a134af5185f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784315"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="58667-103">CorNotificationForTokenMovement 列挙型</span><span class="sxs-lookup"><span data-stu-id="58667-103">CorNotificationForTokenMovement Enumeration</span></span>

<span data-ttu-id="58667-104">トークンの再マップが発生したときにメタデータ API クライアントに送信される通知を指定します。</span><span class="sxs-lookup"><span data-stu-id="58667-104">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58667-105">構文</span><span class="sxs-lookup"><span data-stu-id="58667-105">Syntax</span></span>  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a><span data-ttu-id="58667-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="58667-106">Members</span></span>  
  
|<span data-ttu-id="58667-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="58667-107">Member</span></span>|<span data-ttu-id="58667-108">説明</span><span class="sxs-lookup"><span data-stu-id="58667-108">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="58667-109">、、 `mdTypeRef` `mdMethodDef` `mdMemberRef` 、またはトークンが移動したときに通知 `mdFieldDef` します。</span><span class="sxs-lookup"><span data-stu-id="58667-109">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="58667-110">任意のトークンが移動したときに通知します。</span><span class="sxs-lookup"><span data-stu-id="58667-110">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="58667-111">トークンの移動時に通知しません。</span><span class="sxs-lookup"><span data-stu-id="58667-111">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="58667-112">トークンが移動したときに通知 `mdMethodDef` します。</span><span class="sxs-lookup"><span data-stu-id="58667-112">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="58667-113">トークンが移動したときに通知 `mdMemberRef` します。</span><span class="sxs-lookup"><span data-stu-id="58667-113">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="58667-114">トークンが移動したときに通知 `mdFieldDef` します。</span><span class="sxs-lookup"><span data-stu-id="58667-114">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="58667-115">トークンが移動したときに通知 `mdTypeRef` します。</span><span class="sxs-lookup"><span data-stu-id="58667-115">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="58667-116">トークンが移動したときに通知 `mdTypeDef` します。</span><span class="sxs-lookup"><span data-stu-id="58667-116">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="58667-117">トークンが移動したときに通知 `mdParamDef` します。</span><span class="sxs-lookup"><span data-stu-id="58667-117">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="58667-118">トークンが移動したときに通知 `mdInterfaceImpl` します。</span><span class="sxs-lookup"><span data-stu-id="58667-118">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="58667-119">トークンが移動したときに通知 `mdProperty` します。</span><span class="sxs-lookup"><span data-stu-id="58667-119">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="58667-120">トークンが移動したときに通知 `mdEvent` します。</span><span class="sxs-lookup"><span data-stu-id="58667-120">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="58667-121">トークンが移動したときに通知 `mdSignature` します。</span><span class="sxs-lookup"><span data-stu-id="58667-121">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="58667-122">トークンが移動したときに通知 `mdTypeSpec` します。</span><span class="sxs-lookup"><span data-stu-id="58667-122">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="58667-123">トークンが移動したときに通知 `mdCustomAttribute` します。</span><span class="sxs-lookup"><span data-stu-id="58667-123">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="58667-124">トークンが移動したときに通知 `mdSecurityValue` します。</span><span class="sxs-lookup"><span data-stu-id="58667-124">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="58667-125">トークンが移動したときに通知 `mdPermission` します。</span><span class="sxs-lookup"><span data-stu-id="58667-125">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="58667-126">トークンが移動したときに通知 `mdModuleRef` します。</span><span class="sxs-lookup"><span data-stu-id="58667-126">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="58667-127">トークンが移動したときに通知 `mdNameSpace` します。</span><span class="sxs-lookup"><span data-stu-id="58667-127">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="58667-128">トークンが移動したときに通知 `mdAssemblyRef` します。</span><span class="sxs-lookup"><span data-stu-id="58667-128">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="58667-129">トークンが移動したときに通知 `mdFile` します。</span><span class="sxs-lookup"><span data-stu-id="58667-129">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="58667-130">トークンが移動したときに通知 `mdExportedType` します。</span><span class="sxs-lookup"><span data-stu-id="58667-130">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="58667-131">トークンが移動したときに通知 `mdManifestResource` します。</span><span class="sxs-lookup"><span data-stu-id="58667-131">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58667-132">解説</span><span class="sxs-lookup"><span data-stu-id="58667-132">Remarks</span></span>  

 <span data-ttu-id="58667-133">メタデータのマージ中に、トークンが再マップ (移動) される場合があります。</span><span class="sxs-lookup"><span data-stu-id="58667-133">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58667-134">要件</span><span class="sxs-lookup"><span data-stu-id="58667-134">Requirements</span></span>  

 <span data-ttu-id="58667-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58667-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58667-136">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="58667-136">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="58667-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58667-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58667-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="58667-138">See also</span></span>

- [<span data-ttu-id="58667-139">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="58667-139">Metadata Enumerations</span></span>](metadata-enumerations.md)
