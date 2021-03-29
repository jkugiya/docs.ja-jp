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
# <a name="cor_prf_eventpipe_provider_config-enumeration"></a>COR_PRF_EVENTPIPE_PROVIDER_CONFIG 列挙型

EventPipe プロバイダーを構成するために必要なフィールドを記述します。
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct
{
    const WCHAR* providerName;
    UINT64       keywords;
    UINT32       loggingLevel;
    const WCHAR* filterData;
} COR_PRF_EVENTPIPE_PROVIDER_CONFIG;
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`providerName`|有効にするプロバイダーの名前。|  
|`keywords`|プロバイダーで有効にするキーワード。|  
|`loggingLevel`|プロバイダーで有効にするレベル。|  
|`filterData`|プロバイダーを有効にするときに使用する filterdata が含まれているワイド文字列。|  
  
## <a name="remarks"></a>解説  

 `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` 構造体は、セッションに追加されるプロバイダーの構成を示すために [ICorProfilerInfo12::EventPipeAddProviderToSession](icorprofilerinfo12-eventpipeaddprovidertosession-method.md) メソッドによって使用されます。
  
## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。
**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>関連項目

- [列挙体のプロファイリング](profiling-enumerations.md)
- [ICorProfilerInfo12::EventPipeAddProviderToSession](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
