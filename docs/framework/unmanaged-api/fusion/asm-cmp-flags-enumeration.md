---
description: '詳細情報: ASM_CMP_FLAGS 列挙型'
title: ASM_CMP_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- ASM_CMP_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CMP_FLAGS
helpviewer_keywords:
- ASM_CMP_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 4d1e6700-d4be-4fbd-8796-bfb4c07abbc8
topic_type:
- apiref
ms.openlocfilehash: 6d35691e853d76dc0e363651b23a6e5ff94244a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761422"
---
# <a name="asm_cmp_flags-enumeration"></a><span data-ttu-id="7ea14-103">ASM_CMP_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="7ea14-103">ASM_CMP_FLAGS Enumeration</span></span>

<span data-ttu-id="7ea14-104">[IAssemblyName:: IsEqual](iassemblyname-isequal-method.md)メソッドによって比較される2つのアセンブリのバージョン、ビルド、カルチャ、署名などを示します。</span><span class="sxs-lookup"><span data-stu-id="7ea14-104">Indicates the version, build, culture, signature, and so on, of two assemblies to be compared by the [IAssemblyName::IsEqual](iassemblyname-isequal-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ea14-105">構文</span><span class="sxs-lookup"><span data-stu-id="7ea14-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_CMPF_NAME                   = 0x1,  
    ASM_CMPF_MAJOR_VERSION          = 0x2,  
    ASM_CMPF_MINOR_VERSION          = 0x4,  
    ASM_CMPF_BUILD_NUMBER           = 0x8,  
    ASM_CMPF_REVISION_NUMBER        = 0x10,  
  
    ASM_CMPF_VERSION                =
                 ASM_CMPF_MAJOR_VERSION |
                 ASM_CMPF_MINOR_VERSION |
                 ASM_CMPF_BUILD_NUMBER  |
                 ASM_CMPF_REVISION_NUMBER,  
  
    ASM_CMPF_PUBLIC_KEY_TOKEN       = 0x20,  
    ASM_CMPF_CULTURE                = 0x40,  
    ASM_CMPF_CUSTOM                 = 0x80,  
    ASM_CMPF_DEFAULT                = 0x100,  
    ASM_CMPF_RETARGET               = 0x200,  
    ASM_CMPF_ARCHITECTURE           = 0x400,  
    ASM_CMPF_CONFIG_MASK            = 0x800,  
    ASM_CMPF_MVID                   = 0x1000,  
    ASM_CMPF_SIGNATURE              = 0x2000,  
  
    ASM_CMPF_IL_ALL                 =
                 ASM_CMPF_NAME             |
                 ASM_CMPF_VERSION          |
                 ASM_CMPF_PUBLIC_KEY_TOKEN |
                 ASM_CMPF_CULTURE,  
  
    ASM_CMPF_IL_NO_VERSION          =
                 ASM_CMPF_NAME             |
                 ASM_CMPF_PUBLIC_KEY_TOKEN |
                 ASM_CMPF_CULTURE  
  
} ASM_CMP_FLAGS;  
```  
  
## <a name="requirements"></a><span data-ttu-id="7ea14-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="7ea14-106">Requirements</span></span>  

 <span data-ttu-id="7ea14-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ea14-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ea14-108">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="7ea14-108">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7ea14-109">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7ea14-109">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ea14-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ea14-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea14-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ea14-111">See also</span></span>

- [<span data-ttu-id="7ea14-112">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7ea14-112">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="7ea14-113">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="7ea14-113">Fusion Enumerations</span></span>](fusion-enumerations.md)
