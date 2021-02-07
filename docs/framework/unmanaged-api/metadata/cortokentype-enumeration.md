---
description: 詳細については、「CorTokenType 列挙型」を参照してください。
title: CorTokenType 列挙型
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
ms.openlocfilehash: 954bddccd8fe20be46080f8843bcf754e0cf1bbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678407"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="e7a8e-103">CorTokenType 列挙型</span><span class="sxs-lookup"><span data-stu-id="e7a8e-103">CorTokenType Enumeration</span></span>

<span data-ttu-id="e7a8e-104">メタデータトークンの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-104">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a8e-105">構文</span><span class="sxs-lookup"><span data-stu-id="e7a8e-105">Syntax</span></span>  
  
```cpp  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a><span data-ttu-id="e7a8e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e7a8e-106">Members</span></span>  
  
|<span data-ttu-id="e7a8e-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="e7a8e-107">Member</span></span>|<span data-ttu-id="e7a8e-108">説明</span><span class="sxs-lookup"><span data-stu-id="e7a8e-108">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="e7a8e-109">`mdModule`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-109">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="e7a8e-110">`mdTypeRef`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-110">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="e7a8e-111">`mdTypeDef`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-111">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="e7a8e-112">`mdFieldDef`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-112">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="e7a8e-113">`mdMethodDef`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-113">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="e7a8e-114">`mdParamDef`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-114">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="e7a8e-115">`mdInterfaceImpl`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-115">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="e7a8e-116">`mdMemberRef`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-116">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="e7a8e-117">`mdCustomAttribute`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-117">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="e7a8e-118">`mdPermission`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-118">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="e7a8e-119">`mdSignature`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-119">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="e7a8e-120">`mdEvent`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-120">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="e7a8e-121">`mdProperty`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-121">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="e7a8e-122">`mdModuleRef`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-122">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="e7a8e-123">`mdTypeSpec`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-123">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="e7a8e-124">`mdAssembly`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-124">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="e7a8e-125">`mdAssemblyRef`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-125">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="e7a8e-126">`mdFile`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-126">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="e7a8e-127">`mdExportedType`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-127">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="e7a8e-128">`mdManifestResource`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-128">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="e7a8e-129">`mdGenericParam`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-129">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="e7a8e-130">`mdMethodSpec`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-130">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="e7a8e-131">`mdGenericParamConstraint`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-131">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="e7a8e-132">`mdString`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-132">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="e7a8e-133">`mdName`トークン。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-133">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="e7a8e-134">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-134">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7a8e-135">解説</span><span class="sxs-lookup"><span data-stu-id="e7a8e-135">Remarks</span></span>  

 <span data-ttu-id="e7a8e-136">各値は、対応するメタデータトークンの上位バイトの値に相当します。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-136">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7a8e-137">要件</span><span class="sxs-lookup"><span data-stu-id="e7a8e-137">Requirements</span></span>  

 <span data-ttu-id="e7a8e-138">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7a8e-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7a8e-139">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e7a8e-139">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e7a8e-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7a8e-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a8e-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7a8e-141">See also</span></span>

- [<span data-ttu-id="e7a8e-142">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="e7a8e-142">Metadata Enumerations</span></span>](metadata-enumerations.md)
