---
description: '詳細情報: ICorProfilerInfo9::GetCodeInfo4 メソッド'
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c7897e266fbb84d44df719c127e24bd375b560bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759092"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>ICorProfilerInfo9::GetCodeInfo4 メソッド

ネイティブ コードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。

## <a name="syntax"></a>構文

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a>パラメーター

`pNativeCodeStartAddress` [in] ネイティブ関数の開始へのポインター。

`cCodeInfos` [in] `codeInfos` 配列のサイズ。

`pcCodeInfos` [out] 使用できる [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体の総数へのポインター。

`codeInfos` [out] 呼び出し元が提供したバッファー。 メソッドから制御が戻った後で、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` の構造体の配列が含まれます。

## <a name="remarks"></a>解説

`GetCodeInfo4` メソッドは、メソッドのさまざまなネイティブ バージョンのコード情報を参照できることを除いて、[GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md) に似ています。

> [!NOTE]
> `GetCodeInfo4` によって、ガベージ コレクションをトリガーできます。

エクステントは共通中間言語 (CIL) オフセットの昇順に並べ替えられます。

`GetCodeInfo4` から制御が戻ったら、`codeInfos` バッファーのサイズが十分で、すべての [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体を格納できることを確認する必要があります。 これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体のサイズによって除算された `cCodeInfos` が `pcCodeInfos` より小さい場合は、`codeInfos` バッファーの割り当てを増やし、`cCodeInfos` を新しい大きいサイズに更新した後、`GetCodeInfo4` を再度呼び出します。

別の方法として、最初に `GetCodeInfo4` を長さゼロの `codeInfos` バッファーで呼び出して、適切なバッファーのサイズを取得します。 その後 `codeInfos` バッファーのサイズを、`pcCodeInfos` で返された値と、[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体のサイズを乗算した値に設定し、`GetCodeInfo4` を再度呼び出します。

## <a name="requirements"></a>要件

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET のバージョン:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo9 インターフェイス](ICorProfilerInfo9-interface.md)
