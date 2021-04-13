---
title: GetNames 関数 (アンマネージド API リファレンス)
description: GetNames 関数では、オブジェクトのプロパティの名前が取得されます。
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd889158e61b86f42d88bcf86eda7d816277e6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687659"
---
# <a name="getnames-function"></a>GetNames 関数

オブジェクトのプロパティの名前の一部またはすべてが取得されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`wszQualifierName`  
[in] フィルターの一部として動作する修飾子名を指定する有効な `LPCWSTR` へのポインター。 詳細については、「[解説](#remarks)」を参照してください。 このパラメーターは、`null` に設定できます。

`lFlags`  
[in] ビット フィールドの組み合わせ。 詳細については、「[解説](#remarks)」を参照してください。

`pQualifierValue` [in] フィルター値に初期化される有効な `VARIANT` 構造体へのポインター。 このパラメーターは、`null` に設定できます。

`pstrNames`  
[out] プロパティ名を格納している `SAFEARRAY` 構造体。 入力時には、このパラメーターは常に `null` へのポインターである必要があります。 詳細については、「[解説](#remarks)」セクションを参照してください。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般エラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つ以上のパラメーターが無効であるか、指定したフラグとパラメーターの組み合わせが正しくありません。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | メモリ不足のため、操作を完了できません。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) メソッドの呼び出しがラップされます。

返される名前は、フラグとパラメーターの組み合わせによって制御されます。 たとえば、関数では、すべてのプロパティの名前、またはキー プロパティの名前のみを返すことができます。  プライマリ フィルターは `lFlags` パラメーターで指定され、その他のパラメーターはそれに応じて異なります。

`lFlags` 内のフラグ値はビット フィールドです

`lEnumFlags` 引数として渡すことができるフラグは、*WbemCli.h* ヘッダー ファイル内で定義されているか、コード内で定数として定義することができるビット フィールドです。  各グループのフラグを他のグループの任意のフラグと組み合わせることができます。 ただし、同じグループのフラグは相互に排他的です。

| グループ 1 フラグ |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | すべてのプロパティ名を返します。 `strQualifierName` と `pQualifierVal` は使用されません。 |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | `strQualifierName` パラメーターで指定された名前の修飾子を持つプロパティのみを返します。 このフラグを使用する場合は、`strQualifierName` を指定する必要があります。 |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  `strQualifierName` パラメーターで指定された名前の修飾子を持たないプロパティのみを返します。 このフラグを使用する場合は、`strQualifierName` を指定する必要があります。 |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | `wszQualifierName` パラメーターで指定された名前の修飾子を持ち、`pQualifierVal` 構造体で指定されたものと同じ値も持つプロパティのみを返します。 このフラグを使用する場合は、`wszQualifierName` と `pQualifierValue` の両方を指定する必要があります。 |

| グループ 2 フラグ |[値]  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | キーを定義するプロパティの名前だけを返します。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | オブジェクト参照であるプロパティ名だけを返します。 |

| グループ 3 フラグ |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 最派生クラスに属しているプロパティ名だけを返します。 親クラスからのプロパティは除外します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 親クラスに属しているプロパティ名だけを返します。 |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | システム プロパティの名前だけを返します。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | システム以外のプロパティの名前だけを返します。 |

この関数では、`WBEM_S_NO_ERROR` を返す場合には常に新しい `SAFEARRAY` が割り当てられ、`pstrNames` は常にそれを指すように設定されます。 指定したフィルターに一致するプロパティがない場合、返される配列には 0 個の要素を含めることができます。 関数によって `WBM_S_NO_ERROR` 以外の値が返される場合、新しい `SAFEARRAY` 構造体は返されません。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
