---
description: 詳細については、「CorSetENC 列挙型」を参照してください。
title: CorSetENC 列挙型
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 5ba3e41c10b082ceb2ce7d327f7ff7f857ca98a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707398"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="d8d77-103">CorSetENC 列挙型</span><span class="sxs-lookup"><span data-stu-id="d8d77-103">CorSetENC Enumeration</span></span>

<span data-ttu-id="d8d77-104">メタデータの生成中の動作を決定する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d8d77-104">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8d77-105">構文</span><span class="sxs-lookup"><span data-stu-id="d8d77-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="d8d77-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d8d77-106">Members</span></span>  
  
|<span data-ttu-id="d8d77-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="d8d77-107">Member</span></span>|<span data-ttu-id="d8d77-108">説明</span><span class="sxs-lookup"><span data-stu-id="d8d77-108">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="d8d77-109">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="d8d77-109">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="d8d77-110">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="d8d77-110">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="d8d77-111">メタデータを更新できるのに対して、トークンを移動できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d8d77-111">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="d8d77-112">更新中にトークンを移動できることを示します。</span><span class="sxs-lookup"><span data-stu-id="d8d77-112">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="d8d77-113">更新プログラムが追加のみで構成されることを示します。</span><span class="sxs-lookup"><span data-stu-id="d8d77-113">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="d8d77-114">トークンは移動できません。</span><span class="sxs-lookup"><span data-stu-id="d8d77-114">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="d8d77-115">コンパイルが増分であることを示します。</span><span class="sxs-lookup"><span data-stu-id="d8d77-115">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="d8d77-116">は、変更されたメタデータのみを保存することを示します。</span><span class="sxs-lookup"><span data-stu-id="d8d77-116">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="d8d77-117">`MDUpdateENC`、、およびが含まれ `MDUpdateFull` `MDUpdateIncremental` ます。</span><span class="sxs-lookup"><span data-stu-id="d8d77-117">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8d77-118">要件</span><span class="sxs-lookup"><span data-stu-id="d8d77-118">Requirements</span></span>  

 <span data-ttu-id="d8d77-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8d77-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8d77-120">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d8d77-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d8d77-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8d77-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d77-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8d77-122">See also</span></span>

- [<span data-ttu-id="d8d77-123">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="d8d77-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
