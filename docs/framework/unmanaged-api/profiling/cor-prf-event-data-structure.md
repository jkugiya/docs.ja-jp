---
description: '詳細情報: COR_PRF_EVENT_DATA 列挙型'
title: COR_PRF_EVENT_DATA 列挙型
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENT_DATA
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 477f36476deb9c0d74e263703e36b134c91b5327
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805567"
---
# <a name="cor_prf_event_data-enumeration"></a><span data-ttu-id="3e53d-103">COR_PRF_EVENT_DATA 列挙型</span><span class="sxs-lookup"><span data-stu-id="3e53d-103">COR_PRF_EVENT_DATA Enumeration</span></span>

<span data-ttu-id="3e53d-104">書き込まれる EventPipe イベントのイベント データを記述します。</span><span class="sxs-lookup"><span data-stu-id="3e53d-104">Describes the event data for an EventPipe event being written.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="3e53d-105">構文</span><span class="sxs-lookup"><span data-stu-id="3e53d-105">Syntax</span></span>  
  
```cpp  
typedef struct
{
    UINT64 ptr;
    UINT32 size;
    UINT32 reserved;
} COR_PRF_EVENT_DATA;
```  
  
## <a name="members"></a><span data-ttu-id="3e53d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3e53d-106">Members</span></span>  
  
|<span data-ttu-id="3e53d-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="3e53d-107">Member</span></span>|<span data-ttu-id="3e53d-108">説明</span><span class="sxs-lookup"><span data-stu-id="3e53d-108">Description</span></span>|  
|------------|-----------------|  
|`ptr`|<span data-ttu-id="3e53d-109">データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3e53d-109">A pointer to the data.</span></span>|  
|`size`|<span data-ttu-id="3e53d-110">`ptr` によって指し示されるデータのサイズ。</span><span class="sxs-lookup"><span data-stu-id="3e53d-110">The size of the data pointed to by `ptr`.</span></span>|  
|`reserved`|<span data-ttu-id="3e53d-111">予約された実装固有のフィールド。</span><span class="sxs-lookup"><span data-stu-id="3e53d-111">An reserved implementation specific field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e53d-112">解説</span><span class="sxs-lookup"><span data-stu-id="3e53d-112">Remarks</span></span>  

 <span data-ttu-id="3e53d-113">`COR_PRF_EVENT_DATA` 構造体は、書き込まれるイベントのデータ ペイロードを提供するために [ICorProfilerInfo12::EventPipeWriteEvent](icorprofilerinfo12-eventpipewriteevent-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="3e53d-113">The `COR_PRF_EVENT_DATA` structure is used by the [ICorProfilerInfo12::EventPipeWriteEvent](icorprofilerinfo12-eventpipewriteevent-method.md) method to providate the data payload for the event being written.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="3e53d-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="3e53d-114">Requirements</span></span>  

<span data-ttu-id="3e53d-115">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e53d-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="3e53d-116">**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e53d-116">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3e53d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e53d-117">See also</span></span>

- [<span data-ttu-id="3e53d-118">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="3e53d-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="3e53d-119">ICorProfilerInfo12::EventPipeWriteEvent</span><span class="sxs-lookup"><span data-stu-id="3e53d-119">ICorProfilerInfo12::EventPipeWriteEvent</span></span>](icorprofilerinfo12-eventpipewriteevent-method.md)
