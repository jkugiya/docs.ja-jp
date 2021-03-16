---
title: '破壊的変更:CA1831: 文字列に範囲ベースのインデクサーの代わりに AsSpan を使用します'
description: コード分析ルール CA1831 の有効化によって発生する .NET 5 での破壊的変更について学習します。
ms.date: 08/21/2020
ms.openlocfilehash: 1ed4e2bdde9c3d525f95963f316551909ac3de7c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257792"
---
# <a name="warning-ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a>警告 CA1831:文字列に範囲ベースのインデクサーの代わりに AsSpan を使用します

.NET コード アナライザー ルール [CA1831](/visualstudio/code-quality/ca1831) は .NET 5.0 以降では既定で有効になっています。 <xref:System.Range> ベースのインデクサーが文字列で使用されているが、コピーが意図されていないコードでは、ビルド警告が生成されます。

## <a name="change-description"></a>変更内容

.NET 5 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。 これらのルールのいくつかは、既定では [CA1831](/visualstudio/code-quality/ca1831) を含めて有効になっています。 このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。

ルール CA1831 は、文字列で <xref:System.Range> ベースのインデクサーが使用されているが、コピーが意図されていないインスタンスを検索します。 <xref:System.Range> ベースのインデクサーを文字列で直接使用して暗黙的なキャストを生成する場合は、文字列の要求された部分の不要なコピーが作成されます。 次に例を示します。

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

CA1831 では、代わりに文字列の "*スパン*" で <xref:System.Range> ベースのインデクサーを使用することが提案されます。 次に例を示します。

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

- コードを修正し、不要な割り当てを回避するには、<xref:System.Range> ベースのインデクサーを使用する前に <xref:System.MemoryExtensions.AsSpan(System.String)> または <xref:System.MemoryExtensions.AsMemory(System.String)> を呼び出します。 次に例を示します。

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- コードを変更しない場合は、その重要度を `suggestion` または `none` に設定して、ルールを無効にすることができます。 詳細については、「[コード分析ルールを構成する](../../../../fundamentals/code-analysis/configuration-options.md)」を参照してください。

- コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。 詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Range?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Range`

### Category

Code analysis

-->
