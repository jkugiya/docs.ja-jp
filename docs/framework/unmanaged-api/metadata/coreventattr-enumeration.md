---
description: 詳細については、「CorEventAttr 列挙型」を参照してください。
title: CorEventAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
ms.openlocfilehash: 70f05eacf2cc7c7975b9b52d402cceb60bbea426
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784510"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="70937-103">CorEventAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="70937-103">CorEventAttr Enumeration</span></span>

<span data-ttu-id="70937-104">イベントのメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="70937-104">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70937-105">構文</span><span class="sxs-lookup"><span data-stu-id="70937-105">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="70937-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="70937-106">Members</span></span>  
  
|<span data-ttu-id="70937-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="70937-107">Member</span></span>|<span data-ttu-id="70937-108">説明</span><span class="sxs-lookup"><span data-stu-id="70937-108">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="70937-109">イベントが特別であり、その名前がどのように記述するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="70937-109">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="70937-110">共通言語ランタイムによる内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="70937-110">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="70937-111">共通言語ランタイムがイベント名のエンコーディングを確認する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="70937-111">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70937-112">要件</span><span class="sxs-lookup"><span data-stu-id="70937-112">Requirements</span></span>  

 <span data-ttu-id="70937-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70937-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70937-114">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="70937-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="70937-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70937-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70937-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="70937-116">See also</span></span>

- [<span data-ttu-id="70937-117">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="70937-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
