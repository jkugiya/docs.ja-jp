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
# <a name="cor_prf_event_data-enumeration"></a>COR_PRF_EVENT_DATA 列挙型

書き込まれる EventPipe イベントのイベント データを記述します。
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct
{
    UINT64 ptr;
    UINT32 size;
    UINT32 reserved;
} COR_PRF_EVENT_DATA;
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ptr`|データへのポインター。|  
|`size`|`ptr` によって指し示されるデータのサイズ。|  
|`reserved`|予約された実装固有のフィールド。|  
  
## <a name="remarks"></a>解説  

 `COR_PRF_EVENT_DATA` 構造体は、書き込まれるイベントのデータ ペイロードを提供するために [ICorProfilerInfo12::EventPipeWriteEvent](icorprofilerinfo12-eventpipewriteevent-method.md) メソッドによって使用されます。
  
## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。
**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>関連項目

- [列挙体のプロファイリング](profiling-enumerations.md)
- [ICorProfilerInfo12::EventPipeWriteEvent](icorprofilerinfo12-eventpipewriteevent-method.md)
