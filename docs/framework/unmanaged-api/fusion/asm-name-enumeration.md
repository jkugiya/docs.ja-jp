---
description: '詳細情報: ASM_NAME 列挙型'
title: ASM_NAME 列挙型
ms.date: 03/30/2017
api_name:
- ASM_NAME
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_NAME
helpviewer_keywords:
- ASM_NAME enumeration [.NET Framework fusion]
ms.assetid: c8b65b19-d777-428f-bc0c-0d84c78a37bc
topic_type:
- apiref
ms.openlocfilehash: d4fc18b24e3de31e4c6679bb30a013f61346f4dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761319"
---
# <a name="asm_name-enumeration"></a><span data-ttu-id="bdff4-103">ASM_NAME 列挙型</span><span class="sxs-lookup"><span data-stu-id="bdff4-103">ASM_NAME Enumeration</span></span>

<span data-ttu-id="bdff4-104">[IAssemblyName](iassemblyname-interface.md)メソッドによって取得または設定されるプロパティを持つアセンブリのバージョン、ビルド、カルチャ、署名などを示します。</span><span class="sxs-lookup"><span data-stu-id="bdff4-104">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](iassemblyname-interface.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdff4-105">構文</span><span class="sxs-lookup"><span data-stu-id="bdff4-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_NAME_PUBLIC_KEY = 0,  
    ASM_NAME_PUBLIC_KEY_TOKEN,  
    ASM_NAME_HASH_VALUE,  
    ASM_NAME_NAME,  
    ASM_NAME_MAJOR_VERSION,  
    ASM_NAME_MINOR_VERSION,  
    ASM_NAME_BUILD_NUMBER,  
    ASM_NAME_REVISION_NUMBER,  
    ASM_NAME_CULTURE,  
    ASM_NAME_PROCESSOR_ID_ARRAY,  
    ASM_NAME_OSINFO_ARRAY,  
    ASM_NAME_HASH_ALGID,  
    ASM_NAME_ALIAS,  
    ASM_NAME_CODEBASE_URL,  
    ASM_NAME_CODEBASE_LASTMOD,  
    ASM_NAME_NULL_PUBLIC_KEY,  
    ASM_NAME_NULL_PUBLIC_KEY_TOKEN,  
    ASM_NAME_CUSTOM,  
    ASM_NAME_NULL_CUSTOM,
    ASM_NAME_MVID,  
    ASM_NAME_FILE_MAJOR_VERSION,  
    ASM_NAME_FILE_MINOR_VERSION,  
    ASM_NAME_FILE_BUILD_NUMBER,  
    ASM_NAME_FILE_REVISION_NUMBER,  
    ASM_NAME_RETARGET,  
    ASM_NAME_SIGNATURE_BLOB,  
    ASM_NAME_CONFIG_MASK,  
    ASM_NAME_ARCHITECTURE,  
    ASM_NAME_MAX_PARAMS  
  
} ASM_NAME;  
```  
  
## <a name="requirements"></a><span data-ttu-id="bdff4-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="bdff4-106">Requirements</span></span>  

 <span data-ttu-id="bdff4-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdff4-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdff4-108">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="bdff4-108">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bdff4-109">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bdff4-109">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bdff4-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdff4-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdff4-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdff4-111">See also</span></span>

- [<span data-ttu-id="bdff4-112">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bdff4-112">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="bdff4-113">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="bdff4-113">Fusion Enumerations</span></span>](fusion-enumerations.md)
