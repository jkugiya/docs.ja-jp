---
title: '破壊的変更:CA2013: 値の型と共に ReferenceEquals を使用しないでください'
description: コード分析ルール CA2013 の有効化によって発生する .NET 5 での破壊的変更について学習します。
ms.date: 09/03/2020
ms.openlocfilehash: fc68d9a3af0d629dc39aba0091d32b1982d6f2c5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257766"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a>警告 CA2013:値の型と共に ReferenceEquals を使用しないでください

.NET コード アナライザー ルール [CA2013](/visualstudio/code-quality/ca2013) は、.NET 5.0 以降では既定で有効になっています。 <xref:System.Object.ReferenceEquals(System.Object,System.Object)> を使用して 1 つまたは複数の値の型の等価性を比較するコードについては、ビルド警告が生成されます。

## <a name="change-description"></a>変更内容

.NET 5 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。 これらのルールのいくつかは、[CA2013](/visualstudio/code-quality/ca2013) を含め、既定で有効になっています。 このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。

<xref:System.Object.ReferenceEquals(System.Object,System.Object)> を使用して 1 または複数の値の型の等価性を比較するインスタンスが、ルール CA2013 によって検出されます。 このように値の型の等価性を比較すると、値がボックス化されてから比較が行われるため、結果が不正確になる可能性があります。 比較した値が、同じ値の型のインスタンスを表す場合でも、<xref:System.Object.ReferenceEquals(System.Object,System.Object)> からは `false` が返されます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

- 適切な等値演算子 (`==` など) を使用するようにコードを変更します。 この警告を抑制しないでください。

- コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。 詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

### Category

Code analysis

-->
