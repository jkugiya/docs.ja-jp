---
description: '詳細については、次を参照してください: CorUnmanagedCallingConvention 列挙型'
title: CorUnmanagedCallingConvention 列挙型
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
ms.openlocfilehash: a4b5c70b7dcb4750d641540662941ed3cc08c94b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707294"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="b07db-103">CorUnmanagedCallingConvention 列挙型</span><span class="sxs-lookup"><span data-stu-id="b07db-103">CorUnmanagedCallingConvention Enumeration</span></span>

<span data-ttu-id="b07db-104">アンマネージコードの呼び出し規約を指定します。</span><span class="sxs-lookup"><span data-stu-id="b07db-104">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b07db-105">構文</span><span class="sxs-lookup"><span data-stu-id="b07db-105">Syntax</span></span>  
  
```cpp  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="b07db-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b07db-106">Members</span></span>  
  
|<span data-ttu-id="b07db-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b07db-107">Member</span></span>|<span data-ttu-id="b07db-108">説明</span><span class="sxs-lookup"><span data-stu-id="b07db-108">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="b07db-109">C 言語の呼び出し規約。</span><span class="sxs-lookup"><span data-stu-id="b07db-109">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="b07db-110">標準の呼び出し規約。</span><span class="sxs-lookup"><span data-stu-id="b07db-110">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="b07db-111">"This" 呼び出し規約。</span><span class="sxs-lookup"><span data-stu-id="b07db-111">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="b07db-112">"高速" 呼び出し規約。</span><span class="sxs-lookup"><span data-stu-id="b07db-112">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="b07db-113">使用しません。</span><span class="sxs-lookup"><span data-stu-id="b07db-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="b07db-114">使用しません。</span><span class="sxs-lookup"><span data-stu-id="b07db-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="b07db-115">使用しません。</span><span class="sxs-lookup"><span data-stu-id="b07db-115">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="b07db-116">使用しません。</span><span class="sxs-lookup"><span data-stu-id="b07db-116">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b07db-117">解説</span><span class="sxs-lookup"><span data-stu-id="b07db-117">Remarks</span></span>  

 <span data-ttu-id="b07db-118">CLR では、.NET Framework バージョン1.0 での "高速" 呼び出し規約はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b07db-118">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b07db-119">要件</span><span class="sxs-lookup"><span data-stu-id="b07db-119">Requirements</span></span>  

 <span data-ttu-id="b07db-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b07db-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b07db-121">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b07db-121">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b07db-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b07db-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b07db-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="b07db-123">See also</span></span>

- [<span data-ttu-id="b07db-124">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="b07db-124">Metadata Enumerations</span></span>](metadata-enumerations.md)
