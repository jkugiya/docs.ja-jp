---
title: グローバリゼーション規則 (コード分析)
description: コード分析規則のグローバリゼーション規則について
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- rules, globalization
- globalization rules
- globalization [Visual Studio], rules
- managed code analysis rules, globalization rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 83ecc52c5e20e074c6c1aed68204a574494f42d5
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591595"
---
# <a name="globalization-rules"></a>グローバリゼーション規則

グローバリゼーション規則は、国際対応ライブラリおよびアプリケーションをサポートします。

## <a name="in-this-section"></a>このセクションの内容

|ルール|説明|
|----------|-----------------|
|[CA1303:ローカライズされるパラメーターとしてリテラルを渡さない](ca1303.md)|外部から参照できるメソッドで、.NET コンストラクターまたはメソッドへのパラメーターとして、リテラル文字列を渡しています。その文字列はローカライズ可能です。|
|[CA1304:CultureInfo を指定します](ca1304.md)|System.Globalization.CultureInfo パラメーターを受け入れるオーバーロードを持つメンバーを呼び出しているメソッドまたはコンストラクターが、CultureInfo パラメーターを使用するオーバーロードを呼び出していません。 CultureInfo オブジェクトまたは System.IFormatProvider オブジェクトが指定されない場合、オーバーロードされたメンバーから提示された既定値は、すべてのロケールに効果が及ばない可能性があります。|
|[CA1305:IFormatProvider を指定します](ca1305.md)|System.IFormatProvider パラメーターを受け入れるオーバーロードを持つメンバーを 1 つ以上呼び出しているメソッドまたはコンストラクターが、IFormatProvider パラメーターを使用するオーバーロードを呼び出していません。 System.Globalization.CultureInfo オブジェクトまたは IFormatProvider オブジェクトが指定されない場合、オーバーロードされたメンバーから提示された既定値は、すべてのロケールに効果が及ばない可能性があります。|
|[CA1307:意味を明確にするための StringComparison の指定](ca1307.md)|文字列比較演算で、StringComparison パラメーターを設定しないメソッド オーバーロードが使用されています。|
|[CA1308:文字列を大文字に標準化します](ca1308.md)|文字列は大文字に正規化する必要があります。 小文字への変換時に 1 つの小さい文字グループをラウンド トリップさせることができません。|
|[CA1309:順序を示す StringComparison を使用します](ca1309.md)|非言語的な文字列比較演算で、StringComparison パラメーターが Ordinal または OrdinalIgnoreCase に設定されていません。 パラメーターを StringComparison.Ordinal または StringComparison.OrdinalIgnoreCase に明示的に設定することによって、多くの場合、コードの速度、正確さ、および信頼性が向上します。|
|[CA1310:正確な StringComparison の指定](ca1310.md)|文字列比較演算で、StringComparison パラメーターが設定されておらず、カルチャ固有の文字列比較が既定で使用されるメソッド オーバーロードを使用しています。|
|[CA2101: P/Invoke 文字列引数に対してマーシャリングを指定します](ca2101.md)|プラットフォーム呼び出しメンバーが、部分信頼の呼び出し元を許可し、文字列パラメーターを持ち、さらにその文字列を明示的にマーシャリングしていません。 これはセキュリティ上の脆弱性となる可能性があります。|
