---
description: '詳細情報: COR_PRF_CODE_INFO 構造'
title: COR_PRF_CODE_INFO 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
ms.openlocfilehash: 11eae032424a039cac1136c08409b5b4712e6db1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649248"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="dfb97-103">COR_PRF_CODE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="dfb97-103">COR_PRF_CODE_INFO Structure</span></span>

<span data-ttu-id="dfb97-104">メモリに格納されている 1 個の連続ブロックからなるネイティブ コードを表します。</span><span class="sxs-lookup"><span data-stu-id="dfb97-104">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfb97-105">構文</span><span class="sxs-lookup"><span data-stu-id="dfb97-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="dfb97-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="dfb97-106">Members</span></span>  
  
|<span data-ttu-id="dfb97-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="dfb97-107">Member</span></span>|<span data-ttu-id="dfb97-108">説明</span><span class="sxs-lookup"><span data-stu-id="dfb97-108">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="dfb97-109">連続したコードブロックの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="dfb97-109">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="dfb97-110">ブロックのサイズ。</span><span class="sxs-lookup"><span data-stu-id="dfb97-110">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfb97-111">要件</span><span class="sxs-lookup"><span data-stu-id="dfb97-111">Requirements</span></span>  

 <span data-ttu-id="dfb97-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfb97-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfb97-113">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="dfb97-113">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="dfb97-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfb97-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfb97-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfb97-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb97-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfb97-116">See also</span></span>

- [<span data-ttu-id="dfb97-117">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="dfb97-117">Profiling Structures</span></span>](profiling-structures.md)
