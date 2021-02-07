---
description: 詳細については、「GetCachePath 関数」を参照してください。
title: GetCachePath 関数
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
ms.openlocfilehash: 4f5045d4110ca9aae33ef54eb85a2146f855e6c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761042"
---
# <a name="getcachepath-function"></a><span data-ttu-id="ccf1a-103">GetCachePath 関数</span><span class="sxs-lookup"><span data-stu-id="ccf1a-103">GetCachePath Function</span></span>

<span data-ttu-id="ccf1a-104">指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ccf1a-104">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf1a-105">構文</span><span class="sxs-lookup"><span data-stu-id="ccf1a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccf1a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ccf1a-106">Parameters</span></span>  

 `dwCacheFlags`  
 <span data-ttu-id="ccf1a-107">からキャッシュされたアセンブリのソースを示す [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) 値。</span><span class="sxs-lookup"><span data-stu-id="ccf1a-107">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="ccf1a-108">入出力パスへの返されたポインター。</span><span class="sxs-lookup"><span data-stu-id="ccf1a-108">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="ccf1a-109">[入力、出力]要求された最大長 `pwzCachePath` 。戻り値は、の実際の長さ `pwzCachePath` 。</span><span class="sxs-lookup"><span data-stu-id="ccf1a-109">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccf1a-110">要件</span><span class="sxs-lookup"><span data-stu-id="ccf1a-110">Requirements</span></span>  

 <span data-ttu-id="ccf1a-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccf1a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccf1a-112">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ccf1a-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ccf1a-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccf1a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf1a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccf1a-114">See also</span></span>

- [<span data-ttu-id="ccf1a-115">ASM_CACHE_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="ccf1a-115">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="ccf1a-116">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="ccf1a-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
