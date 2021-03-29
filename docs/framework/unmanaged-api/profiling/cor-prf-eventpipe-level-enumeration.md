---
description: '詳細情報: COR_PRF_EVENTPIPE_LEVEL 列挙型'
title: COR_PRF_EVENTPIPE_LEVEL 列挙型
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_LEVEL
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: da8211da1a9bb6262b078c5e56bee1d0c1f9342e
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805819"
---
# <a name="cor_prf_eventpipe_level-enumeration"></a><span data-ttu-id="846f0-103">COR_PRF_EVENTPIPE_LEVEL 列挙型</span><span class="sxs-lookup"><span data-stu-id="846f0-103">COR_PRF_EVENTPIPE_LEVEL Enumeration</span></span>

<span data-ttu-id="846f0-104">EventPipe イベントのレベルを記述します。</span><span class="sxs-lookup"><span data-stu-id="846f0-104">Describes the level of an EventPipe event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="846f0-105">構文</span><span class="sxs-lookup"><span data-stu-id="846f0-105">Syntax</span></span>  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_LOGALWAYS = 0,
    COR_PRF_EVENTPIPE_CRITICAL = 1,
    COR_PRF_EVENTPIPE_ERROR = 2,
    COR_PRF_EVENTPIPE_WARNING = 3,
    COR_PRF_EVENTPIPE_INFORMATIONAL = 4,
    COR_PRF_EVENTPIPE_VERBOSE = 5
} COR_PRF_EVENTPIPE_LEVEL;
```  
  
## <a name="members"></a><span data-ttu-id="846f0-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="846f0-106">Members</span></span>  
  
|<span data-ttu-id="846f0-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="846f0-107">Member</span></span>|<span data-ttu-id="846f0-108">説明</span><span class="sxs-lookup"><span data-stu-id="846f0-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_LOGALWAYS`|<span data-ttu-id="846f0-109">このイベントは常にログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="846f0-109">The event is always logged.</span></span>|
|`COR_PRF_EVENTPIPE_CRITICAL`|<span data-ttu-id="846f0-110">このイベントは重大なメッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="846f0-110">The event represents a critical message.</span></span>|
|`COR_PRF_EVENTPIPE_ERROR`|<span data-ttu-id="846f0-111">このイベントはエラー メッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="846f0-111">The event represents an error message.</span></span>|
|`COR_PRF_EVENTPIPE_WARNING`|<span data-ttu-id="846f0-112">このイベントは警告メッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="846f0-112">The event represents a warning message.</span></span>|
|`COR_PRF_EVENTPIPE_INFORMATIONAL`|<span data-ttu-id="846f0-113">このイベントは情報メッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="846f0-113">The event represents an informational message.</span></span>|
|`COR_PRF_EVENTPIPE_VERBOSE`|<span data-ttu-id="846f0-114">このイベントは詳細メッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="846f0-114">The event represents a verbose message.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="846f0-115">解説</span><span class="sxs-lookup"><span data-stu-id="846f0-115">Remarks</span></span>  

 <span data-ttu-id="846f0-116">`COR_PRF_EVENTPIPE_LEVEL` 列挙型は、定義されるイベントのレベルを示すために [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="846f0-116">The `COR_PRF_EVENTPIPE_LEVEL` enumeration is used by the [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) method to indicate the level of the event being defined.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="846f0-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="846f0-117">Requirements</span></span>  

<span data-ttu-id="846f0-118">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="846f0-118">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="846f0-119">**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="846f0-119">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="846f0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="846f0-120">See also</span></span>

- [<span data-ttu-id="846f0-121">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="846f0-121">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="846f0-122">ICorProfilerInfo12::EventPipeDefineEvent</span><span class="sxs-lookup"><span data-stu-id="846f0-122">ICorProfilerInfo12::EventPipeDefineEvent</span></span>](icorprofilerinfo12-eventpipedefineevent-method.md)
