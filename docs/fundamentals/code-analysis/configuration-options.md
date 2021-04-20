---
title: コード分析ルールの構成
description: アナライザー構成ファイルでコード分析ルールを構成する方法について説明します。
ms.date: 09/24/2020
no-loc:
- EditorConfig
ms.openlocfilehash: b9f934d13a510fa9e349d1cefc8131f22e9cd549
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740970"
---
# <a name="configuration-options-for-code-analysis"></a>コード分析の構成オプション

コード分析ルールには、さまざまな構成オプションが用意されています。 これらのオプションは、`<option key> = <option value>` という構文を使用して、[アナライザー構成ファイル](configuration-files.md)内のキーと値のペアとして指定されます。

最も一般的に構成されるオプションは、[ルールの重大度](#severity-level)です。 [コード品質ルール](quality-rules/index.md)や[コード スタイル ルール](style-rules/index.md)などのすべてのアナライザー ルールについて、重大度レベルを構成できます。 たとえば、あるルールを警告として有効にするには、次のキーと値のペアを EditorConfig ファイルに追加します。

`dotnet_diagnostic.<rule ID>.severity = warning`

追加のオプションを構成して、ルールの動作をカスタマイズすることもできます。

- コード品質ルールには、ルールを適用する必要があるメソッド名など、動作を構成するための[追加オプション](code-quality-rule-options.md)が用意されています。
- コード スタイル ルールには、[カスタム コード スタイル オプション](code-style-rule-options.md)が用意されています。
- サード パーティのアナライザー ルールでは、カスタムのキー名と値の形式を使用して、独自の構成オプションを定義できます。

[アナライザー構成ファイル](configuration-files.md)で特定のルールの重大度を構成する構文は、次のとおりです。

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a>[全般] オプション

これらのオプションは、コード分析全体に適用されます。 これらを 1 つのルールやルール セットのみに対して適用することはできません。

### <a name="exclude-generated-code"></a>生成されたコードを除外する

`generated_code = true | false` エントリを[構成ファイル](configuration-files.md)に追加することで、追加のファイルやフォルダーを生成されたコードとして扱うように構成することができます。 .NET コード アナライザーの警告は、デザイナーで生成されたファイルなどの、ユーザーが編集して違反を修正することのできない生成されたコード ファイルに対しては役立ちません。 ほとんどの場合、コード アナライザーは生成されたコード ファイルをスキップし、これらのファイルに関する違反を報告しません。

既定では、特定のファイル拡張子または自動生成されたファイル ヘッダーを持つファイルは、生成されたコード ファイルとして扱われます。 たとえば、`.designer.cs` または `.generated.cs` で終わるファイル名は、生成されたコードと見なされます。 この構成オプションを使用することにより、追加の名前付けパターンを指定できます。

たとえば、名前が `.MyGenerated.cs` で終わるすべてのファイルを生成されたコードとして扱うには、次のエントリを追加します。

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a>ルール固有のオプション

ルール固有のオプションは、1 つのルール、ルール セット、またはすべてのルールに適用できます。 ルール固有のオプションには、次のものがあります。

- [ルールの重大度レベル](#severity-level)
- ["*コード品質*" ルールに固有のオプション](code-quality-rule-options.md)

### <a name="severity-level"></a>重大度レベル

次の表に、[コード品質](quality-rules/index.md)ルールや[コード スタイル](style-rules/index.md)ルールなどのすべてのアナライザー ルールに対して構成できる、さまざまなルールの重大度を示します。

| 重大度の構成値 | ビルド時の動作 |
|-|-|
| `error` | 違反はビルドの "*エラー*" として表示され、ビルドは失敗します。|
| `warning` | 違反はビルドの "*警告*" として表示されますが、ビルドは失敗しません (警告をエラーとして扱うようにオプションで設定している場合を除く)。 |
| `suggestion` | 違反はビルドの "*メッセージ*" として表示され、Visual Studio IDE に修正候補として表示されます。 |
| `silent` | 違反はユーザーに表示されません。 |
| `none` | 規則は完全に抑制されます。 |
| `default` | ルールの既定の重大度が使用されます。 各 .NET リリースの既定の重大度は、[roslyn-analyzers リポジトリ](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)に一覧で示されています。 その表で、Disabled は `none` に、Hidden は `silent` に、Info は `suggestion` に相当します。 |

> [!TIP]
> Visual Studio でルールの重大度がどのように表示されるかについては、[重大度レベル](/visualstudio/ide/editorconfig-language-conventions#severity-levels)に関するページを参照してください。

#### <a name="scope"></a>Scope

1 つのルールに対してルールの重大度を設定するには、次の構文を使用します。

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

[ルールのカテゴリ](categories.md)に対して既定のルールの重大度を設定するには、次の構文を使用します。 各ルールのカテゴリは、個々のルールのリファレンス ページ (例: [CA1000](quality-rules/ca1000.md)) で説明されています。

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

すべてのアナライザー ルールに対して既定のルールの重大度を設定するには、次の構文を使用します。

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

> [!IMPORTANT]
> ルールの "*カテゴリ*" または "*すべて*" のルールに対して、1 つのエントリで複数のルールの重大度レベルを構成する場合、その重大度は [既定で有効](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)であるルールに対してのみ適用されます。 既定で無効であるルールを有効にするには、次のいずれかを実行する必要があります。
>
> - ルールごとに明示的な `dotnet_diagnostic.<rule ID>.severity = <severity>` 構成エントリを追加する。
> - [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) を `AllEnabledByDefault` に設定して、"*すべて*" のルールを有効にする。

#### <a name="precedence"></a>優先順位

同一のルール ID に適用できる重大度構成エントリが複数ある場合は、次の順序で優先順位が選択されます。

- ID に基づく個々のルールに対するエントリは、カテゴリに対するエントリよりも優先されます。
- カテゴリに対するエントリは、すべてのアナライザー ルールに対するエントリよりも優先されます。

次の例を考えてみましょう。[CA1822](/visualstudio/code-quality/ca1822) はカテゴリが "パフォーマンス" に指定されています。

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

前の例では、3 つの重大度エントリすべてが CA1822 に適用できます。 ただし、指定した優先順位ルールを使用すると、最初のルール ID ベースのエントリが次のエントリに優先されます。 この例の場合、CA1822 の有効な重大度は `error` です。 "パフォーマンス" カテゴリに含まれる他のすべてのルールは重大度が `warning` です。

ファイル間で優先度が決まる方法の詳細については、[構成ファイルに関する記事の「優先順位」セクション](configuration-files.md#precedence)を参照してください。
