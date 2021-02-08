---
description: '詳細については、次を参照してください: CorDebugJITCompilerFlags 列挙型'
title: CorDebugJITCompilerFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
ms.openlocfilehash: 7e5337293aa4fe446deb12653acd22864eb7679a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801606"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="446b0-103">CorDebugJITCompilerFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="446b0-103">CorDebugJITCompilerFlags Enumeration</span></span>

<span data-ttu-id="446b0-104">マネージド Just-In-Time (JIT) コンパイラの動作に影響を与える値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="446b0-104">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="446b0-105">構文</span><span class="sxs-lookup"><span data-stu-id="446b0-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="446b0-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="446b0-106">Members</span></span>  
  
|<span data-ttu-id="446b0-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="446b0-107">Member</span></span>|<span data-ttu-id="446b0-108">説明</span><span class="sxs-lookup"><span data-stu-id="446b0-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="446b0-109">コンパイラがコンパイルデータを追跡し、最適化を許可することを指定します。</span><span class="sxs-lookup"><span data-stu-id="446b0-109">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="446b0-110">コンパイラがコンパイルデータを追跡する必要があるが、最適化を無効にすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="446b0-110">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="446b0-111">コンパイラがコンパイルデータを追跡し、最適化を無効にして、エディットコンティニュテクノロジを有効にする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="446b0-111">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="446b0-112">要件</span><span class="sxs-lookup"><span data-stu-id="446b0-112">Requirements</span></span>  

 <span data-ttu-id="446b0-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="446b0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="446b0-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="446b0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="446b0-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="446b0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="446b0-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="446b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446b0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="446b0-117">See also</span></span>

- [<span data-ttu-id="446b0-118">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="446b0-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
