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
# <a name="cor_prf_eventpipe_level-enumeration"></a>COR_PRF_EVENTPIPE_LEVEL 列挙型

EventPipe イベントのレベルを記述します。
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_LOGALWAYS`|このイベントは常にログに記録されます。|
|`COR_PRF_EVENTPIPE_CRITICAL`|このイベントは重大なメッセージを表します。|
|`COR_PRF_EVENTPIPE_ERROR`|このイベントはエラー メッセージを表します。|
|`COR_PRF_EVENTPIPE_WARNING`|このイベントは警告メッセージを表します。|
|`COR_PRF_EVENTPIPE_INFORMATIONAL`|このイベントは情報メッセージを表します。|
|`COR_PRF_EVENTPIPE_VERBOSE`|このイベントは詳細メッセージを表します。|
  
## <a name="remarks"></a>解説  

 `COR_PRF_EVENTPIPE_LEVEL` 列挙型は、定義されるイベントのレベルを示すために [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) メソッドによって使用されます。
  
## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。
**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>関連項目

- [列挙体のプロファイリング](profiling-enumerations.md)
- [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md)
