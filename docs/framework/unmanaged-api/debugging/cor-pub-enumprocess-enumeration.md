---
description: '詳細情報: COR_PUB_ENUMPROCESS 列挙型'
title: COR_PUB_ENUMPROCESS 列挙型
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
ms.openlocfilehash: 66bbd08aabb9d2c93e385ed098bae54754a85b85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801788"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="3e230-103">COR_PUB_ENUMPROCESS 列挙型</span><span class="sxs-lookup"><span data-stu-id="3e230-103">COR_PUB_ENUMPROCESS Enumeration</span></span>

<span data-ttu-id="3e230-104">列挙するプロセスの型を識別します。</span><span class="sxs-lookup"><span data-stu-id="3e230-104">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e230-105">構文</span><span class="sxs-lookup"><span data-stu-id="3e230-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="3e230-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3e230-106">Members</span></span>  
  
|<span data-ttu-id="3e230-107">メンバー名</span><span class="sxs-lookup"><span data-stu-id="3e230-107">Member name</span></span>|<span data-ttu-id="3e230-108">説明</span><span class="sxs-lookup"><span data-stu-id="3e230-108">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="3e230-109">マネージプロセス。</span><span class="sxs-lookup"><span data-stu-id="3e230-109">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e230-110">解説</span><span class="sxs-lookup"><span data-stu-id="3e230-110">Remarks</span></span>  

 <span data-ttu-id="3e230-111">アンマネージデバッグ API の現在のバージョンは、マネージプロセスのみを列挙します。</span><span class="sxs-lookup"><span data-stu-id="3e230-111">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e230-112">要件</span><span class="sxs-lookup"><span data-stu-id="3e230-112">Requirements</span></span>  

 <span data-ttu-id="3e230-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e230-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e230-114">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="3e230-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3e230-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e230-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e230-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e230-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e230-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e230-117">See also</span></span>

- [<span data-ttu-id="3e230-118">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="3e230-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
