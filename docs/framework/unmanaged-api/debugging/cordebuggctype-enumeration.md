---
description: '詳細については、次を参照してください: CorDebugGCType 列挙型'
title: CorDebugGCType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
ms.openlocfilehash: 4be835a9a028a882fa050991beb31d2a8dec5354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801658"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="e27aa-103">CorDebugGCType 列挙型</span><span class="sxs-lookup"><span data-stu-id="e27aa-103">CorDebugGCType Enumeration</span></span>

<span data-ttu-id="e27aa-104">ガベージ コレクターがワークステーションまたはサーバーのどちらで実行されているかを示します。</span><span class="sxs-lookup"><span data-stu-id="e27aa-104">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e27aa-105">構文</span><span class="sxs-lookup"><span data-stu-id="e27aa-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e27aa-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e27aa-106">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="e27aa-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="e27aa-107">Members</span></span>  
  
|<span data-ttu-id="e27aa-108">メンバー名</span><span class="sxs-lookup"><span data-stu-id="e27aa-108">Member name</span></span>|<span data-ttu-id="e27aa-109">説明</span><span class="sxs-lookup"><span data-stu-id="e27aa-109">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="e27aa-110">ガベージコレクターはワークステーション上で実行されています。</span><span class="sxs-lookup"><span data-stu-id="e27aa-110">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="e27aa-111">ガベージコレクターはサーバーで実行されています。</span><span class="sxs-lookup"><span data-stu-id="e27aa-111">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e27aa-112">解説</span><span class="sxs-lookup"><span data-stu-id="e27aa-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e27aa-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="e27aa-113">Requirements</span></span>  

 <span data-ttu-id="e27aa-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e27aa-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e27aa-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e27aa-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e27aa-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e27aa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e27aa-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e27aa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27aa-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e27aa-118">See also</span></span>

- [<span data-ttu-id="e27aa-119">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="e27aa-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
