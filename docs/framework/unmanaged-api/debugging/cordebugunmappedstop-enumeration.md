---
description: '詳細については、次を参照してください: CorDebugUnmappedStop 列挙型'
title: CorDebugUnmappedStop 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
ms.openlocfilehash: 9c4f70c5de451689f98a1c08627fd6df5128fdbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801528"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="184bf-103">CorDebugUnmappedStop 列挙型</span><span class="sxs-lookup"><span data-stu-id="184bf-103">CorDebugUnmappedStop Enumeration</span></span>

<span data-ttu-id="184bf-104">ステッパによるコード実行の停止をトリガーする可能性のあるマップ解除したコードの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="184bf-104">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="184bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="184bf-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a><span data-ttu-id="184bf-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="184bf-106">Members</span></span>  
  
|<span data-ttu-id="184bf-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="184bf-107">Member</span></span>|<span data-ttu-id="184bf-108">説明</span><span class="sxs-lookup"><span data-stu-id="184bf-108">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="184bf-109">どの種類のマップされていないコードでも停止しないでください。</span><span class="sxs-lookup"><span data-stu-id="184bf-109">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="184bf-110">プロローグコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="184bf-110">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="184bf-111">エピローグコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="184bf-111">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="184bf-112">マッピング情報のないコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="184bf-112">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="184bf-113">プロローグ、エピローグ、非マッピング情報、またはアンマネージカテゴリに適合しない、マップされていないコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="184bf-113">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="184bf-114">アンマネージコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="184bf-114">Stop in unmanaged code.</span></span> <span data-ttu-id="184bf-115">この値は、相互運用機能デバッグでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="184bf-115">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="184bf-116">すべての種類のマップされていないコードで停止します。</span><span class="sxs-lookup"><span data-stu-id="184bf-116">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="184bf-117">解説</span><span class="sxs-lookup"><span data-stu-id="184bf-117">Remarks</span></span>  

 <span data-ttu-id="184bf-118">[ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md)メソッドを使用して、ステッパが停止するマップされていないコードを指定するフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="184bf-118">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="184bf-119">要件</span><span class="sxs-lookup"><span data-stu-id="184bf-119">Requirements</span></span>  

 <span data-ttu-id="184bf-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="184bf-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="184bf-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="184bf-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="184bf-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="184bf-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="184bf-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="184bf-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="184bf-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="184bf-124">See also</span></span>

- [<span data-ttu-id="184bf-125">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="184bf-125">Debugging Enumerations</span></span>](debugging-enumerations.md)
