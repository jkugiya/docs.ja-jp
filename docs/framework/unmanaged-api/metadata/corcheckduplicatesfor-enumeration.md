---
description: '詳細については、次を参照してください: CorCheckDuplicatesFor 列挙型'
title: CorCheckDuplicatesFor 列挙型
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 5649fc6bc66dd282b64fb5064e302a9f77420cd6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678433"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="9e2fc-103">CorCheckDuplicatesFor 列挙型</span><span class="sxs-lookup"><span data-stu-id="9e2fc-103">CorCheckDuplicatesFor Enumeration</span></span>

<span data-ttu-id="9e2fc-104">重複をチェックするメタデータトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-104">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e2fc-105">構文</span><span class="sxs-lookup"><span data-stu-id="9e2fc-105">Syntax</span></span>  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="9e2fc-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9e2fc-106">Members</span></span>  
  
|<span data-ttu-id="9e2fc-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="9e2fc-107">Member</span></span>|<span data-ttu-id="9e2fc-108">説明</span><span class="sxs-lookup"><span data-stu-id="9e2fc-108">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="9e2fc-109">すべてのメタデータトークンの重複を確認します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-109">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="9e2fc-110">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-110">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="9e2fc-111">メタデータトークンの重複をチェックしないでください。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-111">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="9e2fc-112">トークンの重複を確認 `mdTypeDef` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-112">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="9e2fc-113">トークンの重複を確認 `mdInterfaceImpl` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-113">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="9e2fc-114">トークンの重複を確認 `mdMethodDef` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-114">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="9e2fc-115">トークンの重複を確認 `mdTypeRef` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-115">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="9e2fc-116">トークンの重複を確認 `mdMemberRef` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-116">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="9e2fc-117">トークンの重複を確認 `mdCustomAttribute` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-117">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="9e2fc-118">トークンの重複を確認 `mdParamDef` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-118">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="9e2fc-119">トークンの重複を確認 `mdPermission` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-119">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="9e2fc-120">トークンの重複を確認 `mdProperty` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-120">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="9e2fc-121">トークンの重複を確認 `mdEvent` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-121">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="9e2fc-122">トークンの重複を確認 `mdFieldDef` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-122">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="9e2fc-123">トークンの重複を確認 `mdSignature` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-123">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="9e2fc-124">トークンの重複を確認 `mdModuleRef` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-124">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="9e2fc-125">トークンの重複を確認 `mdTypeSpec` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-125">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="9e2fc-126">トークンの重複を確認 `mdImplMap` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-126">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="9e2fc-127">トークンの重複を確認 `mdAssemblyRef` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-127">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="9e2fc-128">トークンの重複を確認 `mdFile` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-128">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="9e2fc-129">トークンの重複を確認 `mdExportedType` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-129">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="9e2fc-130">トークンの重複を確認 `mdManifestResource` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-130">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="9e2fc-131">トークンの重複を確認 `mdGenericParam` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-131">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="9e2fc-132">トークンの重複を確認 `mdMethodSpec` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-132">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="9e2fc-133">トークンの重複を確認 `mdGenericParamConstraint` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-133">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="9e2fc-134">トークンの重複を確認 `mdAssembly` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-134">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="9e2fc-135">、、、、およびの各トークンの重複を確認 `mdMemberRef` `mdTypeRef` `mdSignature` `mdTypeSpec` `mdMethodSpec` します。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-135">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e2fc-136">要件</span><span class="sxs-lookup"><span data-stu-id="9e2fc-136">Requirements</span></span>  

 <span data-ttu-id="9e2fc-137">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e2fc-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e2fc-138">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="9e2fc-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9e2fc-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e2fc-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e2fc-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e2fc-140">See also</span></span>

- [<span data-ttu-id="9e2fc-141">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="9e2fc-141">Metadata Enumerations</span></span>](metadata-enumerations.md)
