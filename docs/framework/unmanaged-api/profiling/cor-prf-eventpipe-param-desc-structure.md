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
# <a name="cor_prf_eventpipe_param_desc-enumeration"></a>COR_PRF_EVENTPIPE_PARAM_DESC 列挙型

EventPipe イベントのパラメーター名と型を記述します。
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct
{
    UINT32       type;
    UINT32       elementType;
    const WCHAR *name;
} COR_PRF_EVENTPIPE_PARAM_DESC;
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`type`|パラメーターの型。|  
|`elementType`|このパラメーターが配列型である場合は要素型。|  
|`name`|パラメーターの名前が含まれているワイド文字列。|  
  
## <a name="remarks"></a>解説  

 `COR_PRF_EVENTPIPE_PARAM_DESC` 構造体は、定義されるイベントのパラメーターの型を定義するために [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md) メソッドによって使用されます。
  
## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。
**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>関連項目

- [列挙体のプロファイリング](profiling-enumerations.md)
- [ICorProfilerInfo12::EventPipeDefineEvent](icorprofilerinfo12-eventpipedefineevent-method.md)
