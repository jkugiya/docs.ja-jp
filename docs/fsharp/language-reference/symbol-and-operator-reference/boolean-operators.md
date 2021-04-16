---
title: ブール演算子
description: F# プログラミング言語で使用できるブール演算子について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: ad4bdd1121389f7e280647dbe0c4d0098ffb17df
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641899"
---
# <a name="boolean-operators"></a>ブール演算子

このトピックでは、F# 言語のブール演算子のサポートについて説明します。

## <a name="summary-of-boolean-operators"></a>ブール演算子の概要

次の表では、F# 言語で使用できるブール演算子がまとめられています。 これらの演算子でサポートされている型は、`bool` 型のみです。

|演算子|説明|
|--------|-----------|
|`not`|ブール値の否定|
|<code>&#124;&#124;</code>|ブール値の OR|
|`&&`|ブール値の AND|

ブール値の AND および OR 演算子では、 *"短絡評価"* が実行されます。つまり、式の全体の結果を確認する必要がある場合にのみ、演算子の右側で式が評価されます。 `&&` 演算子の 2 番目の式は、最初の式が `true` に評価される場合にのみ評価され、`||` 演算子の 2 番目の式は、最初の式が `false` に評価される場合にのみ評価されます。

## <a name="see-also"></a>関連項目

- [ビット処理演算子 &、^、&#124;](bitwise-operators.md)
- [算術演算子](arithmetic-operators.md)
- [シンボルと演算子のリファレンス](index.md)
