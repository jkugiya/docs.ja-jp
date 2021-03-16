---
title: 破壊的変更:CA2200:スタック詳細を保持するために再度スローします
description: .NET 5 での破壊的変更について学習します。これは、コード分析ルール CA2200 の有効化によって発生します。
ms.date: 09/03/2020
ms.openlocfilehash: 776a1bcf16c19364017e4652837720080fb7ba72
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257727"
---
# <a name="warning-ca2200-rethrow-to-preserve-stack-details"></a>警告 CA2200:スタック詳細を保持するために再度スローします

.NET 5.0 以降では、.NET コード アナライザー ルール [CA2200](/visualstudio/code-quality/ca2200) が既定で有効になっています。 これでは、`throw` ステートメントに例外が明示的に指定された、例外が再スローされるすべての `catch` ブロックに対し、ビルド警告を生成します。

## <a name="change-description"></a>変更内容

.NET 5 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。 これらのルールのいくつかは、[CA2200](/visualstudio/code-quality/ca2200) を含め、既定で有効になっています。 このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。

ルール CA2200 では、例外変数が `throw` ステートメントに指定されている、例外が再スローされるコードにフラグを立ます。 例外がスローされると、その情報の一部はスタック トレースになります。 スタック トレースとは、例外をスローするメソッドで始まり、例外をキャッチするメソッドで終了する、メソッド呼び出しを階層化した一覧です。 `throw` ステートメントに例外を指定して例外が再スローされると、スタック トレースが現在のメソッドで再開され、例外をスローした元のメソッドと現在のメソッド間のメソッド呼び出しの一覧が失われます。 元のスタック トレースの情報を例外で保持するには、例外を指定せずに `throw` ステートメントを使用します。

次のコード スニペットでは、ルール CA2200 で警告が生成されません。 ただし、コメント化された行では、違反がトリガー "*されます*"。

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

- 例外を明示的に指定せずに、例外を再スローします。 詳細については、[CA2200](/visualstudio/code-quality/ca2200) に関するページを参照してください。

- コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。 詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。

## <a name="affected-apis"></a>影響を受ける API

API 分析では検出できません。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
