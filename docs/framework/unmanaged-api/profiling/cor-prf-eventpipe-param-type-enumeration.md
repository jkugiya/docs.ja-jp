---
description: '詳細情報: COR_PRF_EVENTPIPE_PARAM_TYPE 列挙型'
title: COR_PRF_EVENTPIPE_PARAM_TYPE 列挙型
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PARAM_TYPE
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 29aed86e4a991598d038a60ae086e77e25df24bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805780"
---
# <a name="cor_prf_eventpipe_param_type-enumeration"></a>COR_PRF_EVENTPIPE_PARAM_TYPE 列挙型

EventPipe イベントのパラメーターの型を記述します。
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_OBJECT = 1,
    COR_PRF_EVENTPIPE_BOOLEAN = 3,
    COR_PRF_EVENTPIPE_CHAR = 4,
    COR_PRF_EVENTPIPE_SBYTE = 5,
    COR_PRF_EVENTPIPE_BYTE = 6,
    COR_PRF_EVENTPIPE_INT16 = 7,
    COR_PRF_EVENTPIPE_UINT16 = 8,
    COR_PRF_EVENTPIPE_INT32 = 9,
    COR_PRF_EVENTPIPE_UINT32 = 10,
    COR_PRF_EVENTPIPE_INT64 = 11,
    COR_PRF_EVENTPIPE_UINT64 = 12,
    COR_PRF_EVENTPIPE_SINGLE = 13,
    COR_PRF_EVENTPIPE_DOUBLE = 14,
    COR_PRF_EVENTPIPE_DECIMAL = 15,
    COR_PRF_EVENTPIPE_DATETIME = 16,
    COR_PRF_EVENTPIPE_GUID = 17,
    COR_PRF_EVENTPIPE_STRING = 18,
    COR_PRF_EVENTPIPE_ARRAY = 19,
} COR_PRF_EVENTPIPE_PARAM_TYPE;
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_OBJECT`|このパラメーターの型は自己記述型のオブジェクトです。|
|`COR_PRF_EVENTPIPE_BOOLEAN`|このパラメーターの型はブール値です。|
|`COR_PRF_EVENTPIPE_CHAR`|このパラメーターの型は 16 ビット ワイド文字です。|
|`COR_PRF_EVENTPIPE_SBYTE`|このパラメーターの型は符号付き 8 ビット整数です。|
|`COR_PRF_EVENTPIPE_BYTE`|このパラメーターの型は符号なし 8 ビット整数です。|
|`COR_PRF_EVENTPIPE_INT16`|このパラメーターの型は符号付き 16 ビット整数です。|
|`COR_PRF_EVENTPIPE_UINT16`|このパラメーターの型は符号なし 16 ビット整数です。|
|`COR_PRF_EVENTPIPE_INT32`|このパラメーターの型は符号付き 32 ビット整数です。|
|`COR_PRF_EVENTPIPE_UINT32`|このパラメーターの型は符号なし 32 ビット整数です。|
|`COR_PRF_EVENTPIPE_INT64`|このパラメーターの型は符号付き 64 ビット整数です。|
|`COR_PRF_EVENTPIPE_UINT64`|このパラメーターの型は符号なし 64 ビット整数です。|
|`COR_PRF_EVENTPIPE_SINGLE`|このパラメーターの型は 32 ビット浮動小数点数です。|
|`COR_PRF_EVENTPIPE_DOUBLE`|このパラメーターの型は 64 ビット浮動小数点数です。|
|`COR_PRF_EVENTPIPE_DECIMAL`|このパラメーターの型は 128 ビット浮動小数点数です。|
|`COR_PRF_EVENTPIPE_DATETIME`|このパラメーターの型はシリアル化された DataTime 構造体です。|
|`COR_PRF_EVENTPIPE_GUID`|このパラメーターの型は GUID です。|
|`COR_PRF_EVENTPIPE_STRING`|このパラメーターの型は 16 ビットの null で終わるワイド文字列です。|
|`COR_PRF_EVENTPIPE_ARRAY`|このパラメーターの型は前のいずれかの型の配列です。|
  
## <a name="remarks"></a>解説  

 `COR_PRF_EVENTPIPE_PARAM_TYPE` 列挙型は、パラメーターの型を示すために [COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) 構造体によって使用されます。
  
## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。
**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>関連項目

- [列挙体のプロファイリング](profiling-enumerations.md)
