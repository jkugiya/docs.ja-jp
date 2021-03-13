---
title: .NET での書式付きデータの表示と保持に関するベスト プラクティス
description: .NET アプリケーションで数値と日付のデータを効果的に表示および保持する方法について説明します。
ms.date: 05/01/2019
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.openlocfilehash: dd2e85ed695072da24b6b25b187810a109b89b25
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693125"
---
# <a name="best-practices-for-displaying-and-persisting-formatted-data"></a>書式付きデータの表示と保持に関するベスト プラクティス

この記事では、数値データや日時データなどの書式付きデータを、表示および格納のために処理する方法について説明します。

.NET で開発するとき、数値、日付など、文字列以外のデータをユーザー インターフェイスに表示するには、カルチャに依存する書式設定を使用します。 文字列以外のデータを文字列形式で保持するには、[インバリアント カルチャ](xref:System.Globalization.CultureInfo.InvariantCulture)を使用する書式設定を使用します。 数値データや日時データを文字列形式で保持する場合は、カルチャに依存する書式設定を使用しないでください。

## <a name="displaying-formatted-data"></a>書式付きデータの表示

数値、日時など、文字列以外のデータをユーザーに表示するには、ユーザーのカルチャ設定を使用して書式設定します。 既定では、以下のすべてで、書式設定操作での現在のスレッド カルチャが使用されます。

- [C#](../../csharp/language-reference/tokens/interpolated.md) と [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) のコンパイラでサポートされている挿入文字列。
- [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) または [Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) の連結演算子を使用または <xref:System.String.Concat%2A?displayProperty=nameWithType> メソッドを直接呼び出す文字列連結操作。
- <xref:System.String.Format%2A?displayProperty=nameWithType> メソッド。
- 数値型と日時型の `ToString` メソッド。

指定されたカルチャまたは[インバリアント カルチャ](xref:System.Globalization.CultureInfo.InvariantCulture)の規則を使用することで文字列を書式設定することを明示的に指定するには、次を行うことができます。

- <xref:System.String.Format%2A?displayProperty=nameWithType> メソッドと `ToString` メソッドを使用している場合、`provider` パラメーター (<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> または <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> など) を持つオーバー ロードを呼び出し、それに <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> プロパティ、目的のカルチャを表す <xref:System.Globalization.CultureInfo> インスタンス、または <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType> プロパティを渡します。

- 文字列連結の場合、コンパイラに暗黙の変換の実行を許可しないでください。 代わりに、`provider` パラメーターを持つ `ToString` オーバーロードを呼び出すことで、明示的な変換を実行します。 たとえば、次のコードでは、<xref:System.Double> 値を文字列に変換するときに、コンパイラでは現在のカルチャが暗黙的に使用されます。

  [!code-csharp[Implicit String Conversion](./snippets/best-practices-strings/csharp/tostring/Program.cs#1)]
  [!code-vb[Implicit String Conversion](./snippets/best-practices-strings/vb/tostring/Program.vb#1)]

  代わりに、次のコードのように、<xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType> メソッドを呼び出して、変換に使用する書式指定規則を持つカルチャを明示的に指定することができます。

  [!code-csharp[Explicit String Conversion](./snippets/best-practices-strings/csharp/tostring/Program.cs#2)]
  [!code-vb[Implicit String Conversion](./snippets/best-practices-strings/vb/tostring/Program.vb#2)]

- 文字列補間の場合、挿入文字列を <xref:System.String> インスタンスに割り当てるのではなく、<xref:System.FormattableString> に割り当てます。 その後、その <xref:System.FormattableString.ToString?displayProperty=nameWithType> メソッドを呼び出して、現在のカルチャの規則を反映する結果の文字列を生成することも、<xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> メソッドを呼び出して、指定したカルチャの規則を反映する結果の文字列を生成することもできます。 また、書式設定可能な文字列を静的 <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> メソッドに渡して、インバリアント カルチャの規則を反映する結果の文字列を生成することもできます。 このアプローチの例を次に示します。 (この例の出力には en-US の現在のカルチャが反映されます)。

  [!code-csharp[String interpolation](./snippets/best-practices-strings/csharp/formattable/Program.cs)]
  [!code-vb[String interpolation](./snippets/best-practices-strings/vb/formattable/Program.vb)]

## <a name="persisting-formatted-data"></a>書式付きデータの保持

文字列以外のデータは、バイナリ データまたは書式付きデータとして保持できます。 書式付きデータとして保存するには、`provider` パラメーターを含む書式指定メソッドのオーバーロードを呼び出し、そのパラメーターを <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> プロパティに渡す必要があります。 インバリアント カルチャは、カルチャとコンピューターに依存しない書式付きデータに一貫した書式を提供します。 これに対し、インバリアント カルチャ以外のカルチャを使用して書式設定するデータの保持には、さまざまな制限があります。

- カルチャが異なるシステムでデータを取得したり、現在のシステムのユーザーが現在のカルチャを変更してデータを取得しようとしたりすると、そのデータは使用できない可能性があります。
- 特定のコンピューターのカルチャのプロパティは、その標準の値とは異なる場合があります。 常に、ユーザーはカルチャに依存した表示設定をカスタマイズする可能性があります。 このため、ユーザーがカルチャの設定をカスタマイズすると、システムに保存されている書式付きデータを読み取ることができなくなる場合があります。 コンピューター間の書式付きデータの移植性がさらに制限される可能性があります。
- 数値や日時の書式設定を制御する国際的、地域的、または国内の標準は時間と共に変化するため、これらの変化は Windows オペレーティング システムの更新プログラムに組み込まれています。 書式設定の規則が変わると、以前の規則に従って書式設定されたデータを読み取ることができなくなる場合があります。

次に、カルチャに依存する書式設定を使用してデータを保持すると移植性が制限される例を示します。 この例では、日時の値の配列をファイルに保存します。 これらは、英語 (米国) のカルチャの規則を使用して書式設定されています。 現在のスレッド カルチャがフランス語 (スイス) に変更されると、アプリケーションは現在のカルチャの書式設定規則を使用して保存された値を読み取ることを試みます。 2 つのデータ項目の読み取りを試みると、<xref:System.FormatException> 例外がスローされます。日付の配列には、<xref:System.DateTime.MinValue> に等しい 2 つの間違った要素が含まれることになります。

[!code-csharp[Conceptual.Strings.BestPractices#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
[!code-vb[Conceptual.Strings.BestPractices#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]

しかし、<xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> および <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> の呼び出しで、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> プロパティを <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> に置き換えると、保持されている日時データは正常に復元されます。次にその出力を示します。

```console
06.05.1758 21:26
05.05.1818 07:19
22.04.1870 23:54
08.09.1890 06:47
18.02.1905 15:12
```
