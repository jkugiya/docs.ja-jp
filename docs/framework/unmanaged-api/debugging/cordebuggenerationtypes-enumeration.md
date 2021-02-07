---
description: '詳細については、次を参照してください: CorDebugGenerationTypes 列挙型'
title: CorDebugGenerationTypes 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugGenerationTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGenerationTypes
helpviewer_keywords:
- CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type:
- apiref
ms.openlocfilehash: f86b2bc9bf947c6b285c50678f46494005bb5537
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662131"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="2f526-103">CorDebugGenerationTypes 列挙型</span><span class="sxs-lookup"><span data-stu-id="2f526-103">CorDebugGenerationTypes Enumeration</span></span>

<span data-ttu-id="2f526-104">マネージド ヒープ上のメモリ領域の生成を指定します。</span><span class="sxs-lookup"><span data-stu-id="2f526-104">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f526-105">構文</span><span class="sxs-lookup"><span data-stu-id="2f526-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="2f526-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f526-106">Members</span></span>  
  
|<span data-ttu-id="2f526-107">メンバー名</span><span class="sxs-lookup"><span data-stu-id="2f526-107">Member name</span></span>|<span data-ttu-id="2f526-108">説明</span><span class="sxs-lookup"><span data-stu-id="2f526-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="2f526-109">ジェネレーション 0。</span><span class="sxs-lookup"><span data-stu-id="2f526-109">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="2f526-110">第 1 世代。</span><span class="sxs-lookup"><span data-stu-id="2f526-110">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="2f526-111">ジェネレーション 2。</span><span class="sxs-lookup"><span data-stu-id="2f526-111">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="2f526-112">大きなオブジェクトヒープ。</span><span class="sxs-lookup"><span data-stu-id="2f526-112">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f526-113">解説</span><span class="sxs-lookup"><span data-stu-id="2f526-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f526-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="2f526-114">Requirements</span></span>  

 <span data-ttu-id="2f526-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f526-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f526-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f526-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f526-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f526-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f526-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f526-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f526-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f526-119">See also</span></span>

- [<span data-ttu-id="2f526-120">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="2f526-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
