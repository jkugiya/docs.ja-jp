---
description: '詳細情報: COR_PRF_EVENTPIPE_PROVIDER_CONFIG 列挙型'
title: COR_PRF_EVENTPIPE_PROVIDER_CONFIG 列挙型
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PROVIDER_CONFIG
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 2a7a5e720e9468b44e6504d24a3b9ad836e13693
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805845"
---
# <a name="cor_prf_eventpipe_provider_config-enumeration"></a><span data-ttu-id="366dc-103">COR_PRF_EVENTPIPE_PROVIDER_CONFIG 列挙型</span><span class="sxs-lookup"><span data-stu-id="366dc-103">COR_PRF_EVENTPIPE_PROVIDER_CONFIG Enumeration</span></span>

<span data-ttu-id="366dc-104">EventPipe プロバイダーを構成するために必要なフィールドを記述します。</span><span class="sxs-lookup"><span data-stu-id="366dc-104">Describes the fields necessary to configure an EventPipe provider.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="366dc-105">構文</span><span class="sxs-lookup"><span data-stu-id="366dc-105">Syntax</span></span>  
  
```cpp  
typedef struct
{
    const WCHAR* providerName;
    UINT64       keywords;
    UINT32       loggingLevel;
    const WCHAR* filterData;
} COR_PRF_EVENTPIPE_PROVIDER_CONFIG;
```  
  
## <a name="members"></a><span data-ttu-id="366dc-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="366dc-106">Members</span></span>  
  
|<span data-ttu-id="366dc-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="366dc-107">Member</span></span>|<span data-ttu-id="366dc-108">説明</span><span class="sxs-lookup"><span data-stu-id="366dc-108">Description</span></span>|  
|------------|-----------------|  
|`providerName`|<span data-ttu-id="366dc-109">有効にするプロバイダーの名前。</span><span class="sxs-lookup"><span data-stu-id="366dc-109">The name of the provider to enable.</span></span>|  
|`keywords`|<span data-ttu-id="366dc-110">プロバイダーで有効にするキーワード。</span><span class="sxs-lookup"><span data-stu-id="366dc-110">The keywords to enable on the provider.</span></span>|  
|`loggingLevel`|<span data-ttu-id="366dc-111">プロバイダーで有効にするレベル。</span><span class="sxs-lookup"><span data-stu-id="366dc-111">The level to enable on the provider.</span></span>|  
|`filterData`|<span data-ttu-id="366dc-112">プロバイダーを有効にするときに使用する filterdata が含まれているワイド文字列。</span><span class="sxs-lookup"><span data-stu-id="366dc-112">A wide character string containing the filterdata to use when enabling the provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="366dc-113">解説</span><span class="sxs-lookup"><span data-stu-id="366dc-113">Remarks</span></span>  

 <span data-ttu-id="366dc-114">`COR_PRF_EVENTPIPE_PROVIDER_CONFIG` 構造体は、セッションに追加されるプロバイダーの構成を示すために [ICorProfilerInfo12::EventPipeAddProviderToSession](icorprofilerinfo12-eventpipeaddprovidertosession-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="366dc-114">The `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` structure is used by the [ICorProfilerInfo12::EventPipeAddProviderToSession](icorprofilerinfo12-eventpipeaddprovidertosession-method.md) method to indicate the configuration for the provider being added to the session.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="366dc-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="366dc-115">Requirements</span></span>  

<span data-ttu-id="366dc-116">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="366dc-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="366dc-117">**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="366dc-117">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="366dc-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="366dc-118">See also</span></span>

- [<span data-ttu-id="366dc-119">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="366dc-119">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="366dc-120">ICorProfilerInfo12::EventPipeAddProviderToSession</span><span class="sxs-lookup"><span data-stu-id="366dc-120">ICorProfilerInfo12::EventPipeAddProviderToSession</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
