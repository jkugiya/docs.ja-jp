---
description: '詳細情報: COR_PRF_EVENTPIPE_PARAM_DESC 列挙型'
title: COR_PRF_EVENTPIPE_PARAM_DESC 列挙型
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PARAM_DESC
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: b23897580092cc9f3f887a21e86f7111fecd9f19
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805793"
---
# <a name="cor_prf_eventpipe_param_desc-enumeration"></a><span data-ttu-id="0ceaf-103">COR_PRF_EVENTPIPE_PARAM_DESC 列挙型</span><span class="sxs-lookup"><span data-stu-id="0ceaf-103">COR_PRF_EVENTPIPE_PARAM_DESC Enumeration</span></span>

<span data-ttu-id="0ceaf-104">EventPipe イベントのパラメーター名と型を記述します。</span><span class="sxs-lookup"><span data-stu-id="0ceaf-104">Describes the parameter name and type for an EventPipe event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="0ceaf-105">構文</span><span class="sxs-lookup"><span data-stu-id="0ceaf-105">Syntax</span></span>  
  
```cpp  
typedef struct
{
    UINT32       type;
    UINT32       elementType;
    const WCHAR *name;
} COR_PRF_EVENTPIPE_PARAM_DESC;
```  
  
## <a name="members"></a><span data-ttu-id="0ceaf-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0ceaf-106">Members</span></span>  
  
|<span data-ttu-id="0ceaf-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="0ceaf-107">Member</span></span>|<span data-ttu-id="0ceaf-108">説明</span><span class="sxs-lookup"><span data-stu-id="0ceaf-108">Description</span></span>|  
|------------|-----------------|  
|`type`|<span data-ttu-id="0ceaf-109">パラメーターの型。</span><span class="sxs-lookup"><span data-stu-id="0ceaf-109">The type of the parameter.</span></span>|  
|`elementType`|<span data-ttu-id="0ceaf-110">このパラメーターが配列型である場合は要素型。</span><span class="sxs-lookup"><span data-stu-id="0ceaf-110">The element type if this parameter is an array type.</span></span>|  
|`name`|<span data-ttu-id="0ceaf-111">パラメーターの名前が含まれているワイド文字列。</span><span class="sxs-lookup"><span data-stu-id="0ceaf-111">A wide character string containing the name of the parameter.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ceaf-112">解説</span><span class="sxs-lookup"><span data-stu-id="0ceaf-112">Remarks</span></span>  

 <span data-ttu-id="0ceaf-113">`COR_PRF_EVENTPIPE_PARAM_DESC` 構造体は、定義されるイベントのパラメーターの型を定義するために [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ceaf-113">The `COR_PRF_EVENTPIPE_PARAM_DESC` structure is used by the [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) method to define the parameter types of the event being defined.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="0ceaf-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="0ceaf-114">Requirements</span></span>  

<span data-ttu-id="0ceaf-115">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ceaf-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="0ceaf-116">**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ceaf-116">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0ceaf-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ceaf-117">See also</span></span>

- [<span data-ttu-id="0ceaf-118">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="0ceaf-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="0ceaf-119">ICorProfilerInfo12::EventPipeDefineEvent</span><span class="sxs-lookup"><span data-stu-id="0ceaf-119">ICorProfilerInfo12::EventPipeDefineEvent</span></span>](icorprofilerinfo12-eventpipedefineevent-method.md)
