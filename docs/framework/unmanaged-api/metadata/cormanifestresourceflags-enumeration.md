---
description: 詳細については、「CorManifestResourceFlags 列挙型」を参照してください。
title: CorManifestResourceFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
ms.openlocfilehash: a863e1248bf5274e12fc16d2edea6b28dd493963
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784406"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="bb2c6-103">CorManifestResourceFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="bb2c6-103">CorManifestResourceFlags Enumeration</span></span>

<span data-ttu-id="bb2c6-104">アセンブリマニフェストでエンコードされたリソースを表示するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="bb2c6-104">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb2c6-105">構文</span><span class="sxs-lookup"><span data-stu-id="bb2c6-105">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bb2c6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="bb2c6-106">Members</span></span>  
  
|<span data-ttu-id="bb2c6-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="bb2c6-107">Member</span></span>|<span data-ttu-id="bb2c6-108">説明</span><span class="sxs-lookup"><span data-stu-id="bb2c6-108">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="bb2c6-109">予約済み。</span><span class="sxs-lookup"><span data-stu-id="bb2c6-109">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="bb2c6-110">リソースはパブリックです。</span><span class="sxs-lookup"><span data-stu-id="bb2c6-110">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="bb2c6-111">リソースはプライベートです。</span><span class="sxs-lookup"><span data-stu-id="bb2c6-111">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb2c6-112">要件</span><span class="sxs-lookup"><span data-stu-id="bb2c6-112">Requirements</span></span>  

 <span data-ttu-id="bb2c6-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb2c6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb2c6-114">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="bb2c6-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bb2c6-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb2c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb2c6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb2c6-116">See also</span></span>

- [<span data-ttu-id="bb2c6-117">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="bb2c6-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
