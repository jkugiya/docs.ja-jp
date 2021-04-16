---
title: 不要なコード規則
description: コード分析の不要なコード規則について
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96593857"
---
# <a name="unnecessary-code-rules"></a>不要なコード規則

不要なコード規則は、不要でリファクタリングまたは削除することができるコード ベースのさまざまな部分を特定します。 不要なコードが存在する場合は、次の問題の 1 つ以上が存在することを示しています。

- 読みやすさ: 読みやすさを不必要に低下させるコード。 たとえば、[IDE0001](ide0001.md) は不要な型名の修飾にフラグを設定します。
- 保守容易性: リファクタリング後に使用されなくなり、不必要に管理されるコード。 たとえば、[IDE0051](ide0051.md) は、使用されていないプライベート フィールド、プロパティ、イベント、およびメソッドにフラグを設定します。
- パフォーマンス: 副作用がなく、不要なパフォーマンスのオーバーヘッドが発生する不要な計算。 たとえば、[IDE0059](ide0059.md) は、値を計算する式に副作用がない未使用の値の割り当てにフラグを設定します。
- 機能: コードの冗長なレンダリングが必要となるコードの機能の問題。 たとえば、[IDE0060](ide0060.md) は、メソッドで誤って入力パラメーターを無視した場合に、未使用のパラメーターにフラグを設定します。

このセクションの規則では、次の不要なコード規則について考慮します。

- [名前を簡略化する (IDE0001)](ide0001.md)
- [メンバー アクセスを簡略化する (IDE0002)](ide0002.md)
- [不要なキャストを削除する (IDE0004)](ide0004.md)
- [不要なインポートを削除する (IDE0005)](ide0005.md)
- [到達できないコードを削除する (IDE0035)](ide0035.md)
- [使用されていない非公開メンバーを削除する (IDE0051)](ide0051.md)
- [読み取られていない非公開メンバーを削除する (IDE0052)](ide0052.md)
- [使用されていない式の値を削除する (IDE0058)](ide0058.md)
- [不要な値の代入を削除する (IDE0059)](ide0059.md)
- [使用されていないパラメーターを削除する (IDE0060)](ide0060.md)
- [不要な抑制を削除する (IDE0079)](ide0079.md)
- [不要な抑制演算子を削除する (IDE0080)](ide0080.md) - C# のみ。
- ['ByVal' を削除する (IDE0081)](ide0081.md) - Visual Basic のみ。
- [不要な等値演算子を削除する (IDE0100)](ide0100.md)
- [不要な破棄を削除する (IDE0110)](ide0110.md) - C# のみ。

これらの規則の一部には、規則の動作を構成するためのオプションがあります。

- [csharp_style_unused_value_expression_statement_preference (IDE0058)](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [visual_basic_style_unused_value_expression_statement_preference (IDE0058)](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [csharp_style_unused_value_assignment_preference (IDE0059)](ide0059.md#csharp_style_unused_value_assignment_preference)
- [visual_basic_style_unused_value_assignment_preference (IDE0059)](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [dotnet_code_quality_unused_parameters (IDE0060)](ide0060.md#dotnet_code_quality_unused_parameters)
- [dotnet_remove_unnecessary_suppression_exclusions (IDE0079)](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a>関連項目

- [コード スタイルの言語規則](language-rules.md)
- [コード スタイルの規則のリファレンス](index.md)
