---
description: '詳細情報: ASM_CACHE_FLAGS 列挙型'
title: ASM_CACHE_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
ms.openlocfilehash: 866f61d2960074495ed036e3a8e89ebceec74e87
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761435"
---
# <a name="asm_cache_flags-enumeration"></a><span data-ttu-id="da1ed-103">ASM_CACHE_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="da1ed-103">ASM_CACHE_FLAGS Enumeration</span></span>

<span data-ttu-id="da1ed-104">グローバルアセンブリキャッシュ内の [Iassemblycacheitem](iassemblycacheitem-interface.md) によって表されるアセンブリのソースを示します。</span><span class="sxs-lookup"><span data-stu-id="da1ed-104">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da1ed-105">構文</span><span class="sxs-lookup"><span data-stu-id="da1ed-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="da1ed-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="da1ed-106">Members</span></span>  
  
|<span data-ttu-id="da1ed-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="da1ed-107">Member</span></span>|<span data-ttu-id="da1ed-108">説明</span><span class="sxs-lookup"><span data-stu-id="da1ed-108">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="da1ed-109">Ngen.exe を使用して、プリコンパイル済みアセンブリのキャッシュを列挙します。</span><span class="sxs-lookup"><span data-stu-id="da1ed-109">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="da1ed-110">グローバルアセンブリキャッシュを列挙します。</span><span class="sxs-lookup"><span data-stu-id="da1ed-110">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="da1ed-111">要求時にダウンロードされた、またはシャドウコピーされたアセンブリを列挙します。</span><span class="sxs-lookup"><span data-stu-id="da1ed-111">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="da1ed-112">[Getcachepath](getcachepath-function.md)関数が、共通言語ランタイム (CLR) バージョン2.0 のグローバルアセンブリキャッシュへのパスを返す必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="da1ed-112">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="da1ed-113">[Getcachepath](getcachepath-function.md)への呼び出しのコンテキストでのみ意味があります。</span><span class="sxs-lookup"><span data-stu-id="da1ed-113">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="da1ed-114">[Getcachepath](getcachepath-function.md)関数が CLR version 4 のグローバルアセンブリキャッシュへのパスを返す必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="da1ed-114">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="da1ed-115">[Getcachepath](getcachepath-function.md)への呼び出しのコンテキストでのみ意味があります。</span><span class="sxs-lookup"><span data-stu-id="da1ed-115">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da1ed-116">要件</span><span class="sxs-lookup"><span data-stu-id="da1ed-116">Requirements</span></span>  

 <span data-ttu-id="da1ed-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da1ed-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da1ed-118">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="da1ed-118">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="da1ed-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="da1ed-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da1ed-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da1ed-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da1ed-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="da1ed-121">See also</span></span>

- [<span data-ttu-id="da1ed-122">GetCachePath 関数</span><span class="sxs-lookup"><span data-stu-id="da1ed-122">GetCachePath Function</span></span>](getcachepath-function.md)
- [<span data-ttu-id="da1ed-123">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da1ed-123">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
- [<span data-ttu-id="da1ed-124">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="da1ed-124">Fusion Enumerations</span></span>](fusion-enumerations.md)
