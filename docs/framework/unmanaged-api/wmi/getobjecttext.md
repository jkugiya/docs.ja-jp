---
title: GetObjectText 関数 (アンマネージド API リファレンス)
description: GetObjectText 関数では、MOF 構文でのオブジェクトのテキスト形式のレンダリングが返されます。
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6ad2b29202222d594cc7976a13929002164314a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718372"
---
# <a name="getobjecttext-function"></a>GetObjectText 関数

管理オブジェクト フォーマット (MOF) 構文でのオブジェクトのテキスト形式のレンダリングが返されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`lFlags`  
[in] 通常は 0 です。 `WBEM_FLAG_NO_FLAVORS` (または 0x1) が指定されている場合、修飾子は伝達または種類の情報なしで含まれます。

`pstrObjectText` [out] エントリの `null` へのポインター 。 戻り時は、オブジェクトの MOF 構文レンダリングを含む新しく割り当てられた `BSTR` です。  

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般エラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | メモリ不足のため、操作を完了できません。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) メソッドの呼び出しがラップされます。

返される MOF テキストには、オブジェクトに関するすべての情報ではなく、MOF コンパイラが元のオブジェクトを再作成するのに十分な情報だけが含まれています。 たとえば、伝達された修飾子や親クラスのプロパティは含まれません。

次のアルゴリズムは、メソッドのパラメーターのテキストを再構築するために使用されます。

1. パラメーターは、識別子の値の順序で並べ替えられます。
1. `[in]` および `[out]` として指定されたパラメーターは、1 つのパラメーターに結合されます。

`pstrObjectText` は、関数が呼び出されたときの `null` へのポインターである必要があります。ポインターの割り当ては解除されないため、メソッド呼び出しの前に有効な文字列を指していてはなりません。

## <a name="requirements"></a>必要条件  

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
