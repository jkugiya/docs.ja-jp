---
description: '詳細情報: COR_PRF_MISC 列挙型'
title: COR_PRF_MISC 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: 037ea040dfdf9f5be48369ab4d8e94b12aea51ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687598"
---
# <a name="cor_prf_misc-enumeration"></a><span data-ttu-id="5ec49-103">COR_PRF_MISC 列挙型</span><span class="sxs-lookup"><span data-stu-id="5ec49-103">COR_PRF_MISC Enumeration</span></span>

<span data-ttu-id="5ec49-104">特殊な識別子を指定する定数値を含めます。</span><span class="sxs-lookup"><span data-stu-id="5ec49-104">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ec49-105">構文</span><span class="sxs-lookup"><span data-stu-id="5ec49-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="5ec49-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="5ec49-106">Members</span></span>  
  
|<span data-ttu-id="5ec49-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="5ec49-107">Member</span></span>|<span data-ttu-id="5ec49-108">説明</span><span class="sxs-lookup"><span data-stu-id="5ec49-108">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="5ec49-109">アセンブリにまだアタッチされていないモジュールに対して [ICorProfilerInfo:: GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) によって使用される既定の識別子。</span><span class="sxs-lookup"><span data-stu-id="5ec49-109">The default identifier used by [ICorProfilerInfo::GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="5ec49-110">クラスに属していないグローバル定数の既定のクラス識別子。</span><span class="sxs-lookup"><span data-stu-id="5ec49-110">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="5ec49-111">モジュールに属さないグローバルオブジェクトの既定のモジュール識別子。</span><span class="sxs-lookup"><span data-stu-id="5ec49-111">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ec49-112">要件</span><span class="sxs-lookup"><span data-stu-id="5ec49-112">Requirements</span></span>  

 <span data-ttu-id="5ec49-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ec49-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ec49-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ec49-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ec49-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ec49-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ec49-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ec49-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec49-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ec49-117">See also</span></span>

- [<span data-ttu-id="5ec49-118">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="5ec49-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
