---
title: 保守容易性の規則 (コード分析)
description: コード分析の保守容易性の規則について説明します。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: fc2ef2b42eeba241b7af66b579a60365ad2b88c7
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591194"
---
# <a name="maintainability-rules"></a>保守容易性の規則

保守容易性の規則は、ライブラリとアプリケーションの保守をサポートします。

## <a name="in-this-section"></a>このセクションの内容

| ルール | 説明 |
|-----------|-----------------------------------|
| [CA1501:継承を使用しすぎないでください](ca1501.md) | 型が、その継承階層内の 5 つ以上深いレベルにあります。 深いレベルで入れ子にされた型の確認、理解、および保守は困難です。 |
| [CA1502:メソッドの実装を複雑にしすぎないでください](ca1502.md) | この規則は、線形独立のメソッド経路数を示す尺度で、条件分岐の数と複雑さによって決まります。 |
| [CA1505:メンテナンスできないコードを使用しないでください](ca1505.md) | 型またはメソッドの保守容易性指数が低い値です。 保守容易性指数の低い型またはメソッドは、保守が困難な可能性があるため、デザインの変更を検討することをお勧めします。 |
| [CA1506:クラス結合度を大きくしすぎないでください](ca1506.md) | この規則は、型またはメソッドに含まれる一意の型参照の数をカウントすることによって、クラス結合度を計測します。 |
| [CA1507:文字列の代わりに nameof を使用します](ca1507.md) | `nameof` 式を使用できる場合に、文字列リテラルが引数として使用されています。 |
| [CA1508:使用されない条件付きコードを回避する](ca1508.md) | 実行時に常に `true` または `false` と評価される条件付きコードがメソッドにあります。 このため、条件の `false` 分岐で実行されないコードになります。 |
| [CA1509: コード メトリック構成ファイルのエントリが無効です](ca1509.md) | [CA1501](ca1501.md)、[CA1502](ca1502.md)、[CA1505](ca1505.md)、[CA1506](ca1506.md) などのコード メトリック規則で、無効なエントリを含んだ `CodeMetricsConfig.txt` という名前の構成ファイルが指定されました。 |

## <a name="see-also"></a>関連項目

- [マネージド コードの複雑さと保守性の測定](/visualstudio/code-quality/code-metrics-values)
