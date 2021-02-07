---
description: '詳細については、次を参照してください: CorDebugJITCompilerFlagsDeprecated 列挙型'
title: CorDebugJITCompilerFlagsDeprecated 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlagsDeprecated
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords:
- CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type:
- apiref
ms.openlocfilehash: ac607766c484a63a757d726826c81d16edd48aae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661910"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="c002b-103">CorDebugJITCompilerFlagsDeprecated 列挙型</span><span class="sxs-lookup"><span data-stu-id="c002b-103">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>

<span data-ttu-id="c002b-104">この列挙型は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="c002b-104">This enumeration is obsolete.</span></span> <span data-ttu-id="c002b-105">代わりに、 `CORDEBUG_JIT_DEFAULT` [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列挙体のメンバーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="c002b-105">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c002b-106">構文</span><span class="sxs-lookup"><span data-stu-id="c002b-106">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="c002b-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="c002b-107">Members</span></span>  
  
|<span data-ttu-id="c002b-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="c002b-108">Member</span></span>|<span data-ttu-id="c002b-109">説明</span><span class="sxs-lookup"><span data-stu-id="c002b-109">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="c002b-110">代わりに `CORDEBUG_JIT_DEFAULT` を使用してください</span><span class="sxs-lookup"><span data-stu-id="c002b-110">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c002b-111">要件</span><span class="sxs-lookup"><span data-stu-id="c002b-111">Requirements</span></span>  

 <span data-ttu-id="c002b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c002b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c002b-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c002b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c002b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c002b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c002b-115">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="c002b-115">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c002b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c002b-116">See also</span></span>

- [<span data-ttu-id="c002b-117">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="c002b-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
